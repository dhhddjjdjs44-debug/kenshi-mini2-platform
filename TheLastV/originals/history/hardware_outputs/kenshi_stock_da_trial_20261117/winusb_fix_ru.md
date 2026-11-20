# Исправление WinUSB / stock_cdc_setup — 17 ноября 2026

## Что произошло в физической попытке

Проверен исходный журнал `C:\Users\USER\Documents\Codex\2026-11-16\senior-embedded-c99-developer-reverse-engineer\work\stock_da_trial_20261117\sessions\attempt_20261117_141813_730826`.

```json
{"direction":"control_out","libusb_rc":-9,"actual_bytes":0,"requested_bytes":7}
```

Точный код — **`LIBUSB_ERROR_PIPE = -9`**, а не `LIBUSB_ERROR_NOT_SUPPORTED = -12`. Эти значения сверены с локальным первичным кодом PyUSB (`C:\MTK_Drivers\python_env\Lib\site-packages\usb\backend\libusb1.py`). На этапе control transfer это соответствует отказу/STALL запроса; сам журнал не доказывает, какая именно часть устройства или Windows-маршрутизации его вызвала.

Из порядка запросов старого кода установлено, что отказал первый `SET_LINE_CODING`: `bmRequestType=0x21`, `bRequest=0x20`, `wValue=0`, **`wIndex=0`**, длина 7, 921600/8N1. Следовательно, исправлять «забытый wIndex» было нечего: он уже нулевой. `SET_CONTROL_LINE_STATE` ещё не отправлялся. В этой попытке bulk TX/RX равны нулю; DA не был загружен, транзакция не начата, D3/D5 и FINISH не отправлялись. Свежего NOR-дампа эта попытка не дала — проверка его актуального хеша по такому журналу невозможна.

[Машинный разбор исходного журнала](C:/Users/USER/Documents/Codex/2026-11-16/senior-embedded-c99-developer-reverse-engineer/outputs/kenshi_stock_da_trial_20261117/evidence/cdc_failure_analysis.json). Исходная сессия не изменена.

## Проверка локального mtkclient

В `C:\MTK_Drivers\dump_tool\mtkclient\Library\Port.py` штатная функция `run_handshake` вызывает настройку line coding/RTS перед обменом A0/0A/50/05. Но обе соответствующие функции в `C:\MTK_Drivers\dump_tool\mtkclient\Library\Connection\usblib.py` ловят исключения control transfer и не делают их условием отказа самого handshake. Для не-FTDI там тоже применяется интерфейс 0.

Мы **не переносили** такое широкое подавление исключений: оно не подходит под ограничения нашего строгого транспорта. Вместо этого выбран заранее фиксированный путь direct USB bulk, без CDC. Он предназначен только для поддерживаемого этим запускателем MT6261/0E8D:0003 через libusb/WinUSB, не для UART/COM или произвольных CDC-устройств. Источники и их хеши: [реестр](C:/Users/USER/Documents/Codex/2026-11-16/senior-embedded-c99-developer-reverse-engineer/outputs/kenshi_stock_da_trial_20261117/evidence/cdc_primary_sources.json).

## Узкая правка

Изменён [модуль DA](C:/Users/USER/Documents/Codex/2026-11-16/senior-embedded-c99-developer-reverse-engineer/outputs/kenshi_stock_da_trial_20261117/source/stock_da.py): фаза `stock_cdc_setup` проверяет свежесть и исправность транспорта, записывает событие `stock_cdc_setup_skipped` с политикой `direct_usb_bulk_no_cdc`, затем сразу начинает живой BootROM handshake. Ни `SET_LINE_CODING`, ни `SET_CONTROL_LINE_STATE` в физическом пути больше не отправляются. Первым bulk OUT должен стать `A0`, ожидаемый ответ — `5F`; далее 0A/F5, 50/AF, 05/FA.

Изменён [единый запускатель](C:/Users/USER/Documents/Codex/2026-11-16/senior-embedded-c99-developer-reverse-engineer/outputs/kenshi_stock_da_trial_20261117/source/physical_trial.py): он вызывает инициализатор без control callback и сохраняет признак `stock_cdc_setup: skipped_direct_usb_bulk` в результате попытки.

Это **пропуск необязательной операции до любого I/O**, а не восстановление после уже случившейся USB-ошибки. Старый отравленный транспорт не реанимируется. Если control-запрос был фактически выполнен и отказал, его ошибка по-прежнему терминальна. Также терминальны все ошибки bulk, включая `-9`, `-12`, `-7`, `-4`, короткую запись и ошибки с ненулевым числом переданных байтов. Повтор, clear-halt, reset и reconnect не добавлены.

Побайтно неизменны строгий USB-транспорт, ограничитель D3/D5, шлюз FINISH, обе PowerShell-обёртки, секторный образ и бинарник игры. Проверки живой защиты/геометрии, исходного полного NOR, только четырёх секторов `[0x00B000,0x00F000)` и полного финального readback остаются прежними. [Хеши неизменённых файлов](C:/Users/USER/Documents/Codex/2026-11-16/senior-embedded-c99-developer-reverse-engineer/outputs/kenshi_stock_da_trial_20261117/evidence/unchanged_safety_files.json), [diff](C:/Users/USER/Documents/Codex/2026-11-16/senior-embedded-c99-developer-reverse-engineer/outputs/kenshi_stock_da_trial_20261117/evidence/cdc_fix.patch).

## Проверки

Запущен именно `C:\Users\USER\Documents\Codex\2026-11-16\senior-embedded-c99-developer-reverse-engineer\outputs\kenshi_stock_da_trial_20261117\verify_offline.ps1`. Результат: **68 unit-тестов и 9 native-сценариев — PASS**. USB-ошибка инжектировалась на каждом из **2142** bulk-вызовов инициализации; `init_control_transfers = 0`.

Добавлены проверки:

- WinUSB-модель возвращает `-9` на CDC, но эти запросы вообще не вызываются, и начинается A0/0A/50/05.
- Уже отказавший, закрытый, буферизованный или использованный транспорт не допускается к обмену.
- Bulk `-9` и другие ошибки не становятся «необязательными» и не вызывают повтор.
- Событие пропуска CDC записывается до первой bulk-передачи; сбой записи события тоже останавливает процесс.
- Во всех пяти сквозных native-сценариях подтверждены ноль CDC-запросов и прежние границы записи.

Дополнительно обычная PowerShell-команда без `-Mode` завершилась `offline_preflight_passed`, `device_opened=false`; все Python-исходники синтаксически проверены. [Фактический отчёт тестов](C:/Users/USER/Documents/Codex/2026-11-16/senior-embedded-c99-developer-reverse-engineer/outputs/kenshi_stock_da_trial_20261117/evidence/offline_summary.json).

В рамках этой правки физический USB не открывался. Инициализация BootROM/DA всё ещё проверена на протокольной модели, а не на кремнии. Исправление устраняет известный обязательный CDC-барьер; фактическое прохождение следующей стадии подтвердит только новая физическая попытка.

## Команда повторного физического запуска

Запускатель обновлён на месте. Никакой установки драйвера или изменения DA для этой правки не требуется. Нужен один аппарат, доступный для штатного BootROM handshake; не запускать одновременно другой прошивальщик.

```powershell
$root = 'C:\Users\USER\Documents\Codex\2026-11-16\senior-embedded-c99-developer-reverse-engineer'
& "$root\outputs\kenshi_stock_da_trial_20261117\run_trial.ps1" `
    -WorkspaceRoot $root `
    -Mode WriteFourSectors `
    -FinishAfterVerify
```

Эта команда **не выполнялась** при подготовке правки. При следующей ошибке не повторять её автоматически и не ослаблять проверки — сохранить новую сессию.

Для повторной проверки без телефона:

```powershell
& "$root\outputs\kenshi_stock_da_trial_20261117\verify_offline.ps1" -WorkspaceRoot $root
```

Прежнее ограничение не изменилось: `-FinishAfterVerify` отправляет штатный D9 только после полного проверенного readback, но **не гарантирует аппаратную перезагрузку и запуск Тетриса**. Для проверки старта может потребоваться ручное включение после успешного результата.
