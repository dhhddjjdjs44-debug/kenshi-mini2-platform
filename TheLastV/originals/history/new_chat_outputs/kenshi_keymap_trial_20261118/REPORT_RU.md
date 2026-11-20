# Kenshi Mini 2 — исправленная раскладка: запись НЕ состоялась

18 ноября 2026, попытка 18:44:28 +05:00. Новый пакет собран и проверен,
но **на телефон не записан**. Автоматического повтора не было.

## Фактический результат

Пользователь разрешил: «Попробуй лучше запиши прошивку, будем на практике проверять».
Выполнен один запуск существующего writer в режиме WriteFourSectors без
FinishAfterVerify/UseExistingDA. Он остановился на `open_once`:

`Need exactly one MediaTek 0E8D:0003, found 0`

- transaction_status = not_started;
- stock_da_initialized = false;
- nor_write_command_attempted = false;
- reads = {}: свежего NOR before/readback нет;
- FINISH/reset/retry/reconnect/clear-halt/rollback не выполнялись.

Стирание/запись не начинались. Не было ни загрузки DA, ни DA/NOR-команд.
Сессия с исходным result.json: `C:\Users\USER\Documents\Codex\2026-11-16\senior-embedded-c99-developer-reverse-engineer\work\stock_da_trial_20261117\sessions\attempt_20261118_184428_696059`.
Не путать эту остановку обнаружения с ошибкой прошивки/питания телефона.

Пассивный Windows PnP до/после показывает запись устройства 0E8D:0003,
службу WinUSB, oem51.inf. Это **не** доказательство доступности через libusb
или готовности BootROM/DA: именно libusb discovery writer вернул 0 устройств.
Причина расхождения не установлена; драйверы/конфигурация USB не менялись,
никакого обходного открытия или повторной попытки подключения не делалось.

## Подготовленная, но НЕ установленная раскладка

| Физическая кнопка | Действие | Бит |
| --- | --- | --- |
| ← | Влево | 21 |
| → | Вправо | 30 |
| OK | Поворот | 42 |
| ↓ | Мягкое падение | 15 |
| 2 | Мгновенный сброс | 0 |
| Левая софт-клавиша | Пауза | 33 |
| 8 | Поворот, дополнительная | 9 |
| 7 | Мягкое падение, дополнительная | 6 |
| Зелёная трубка | Пауза, дополнительная | 24 |

STAR boot learning исправлен с bit2 на фото-подтверждённый bit3.
На фото → и ↑ оба дали bit30: если так и при повторном нажатии,
↑ в этом кандидате тоже будет означать вправо. Отдельной привязки UP нет,
красная трубка не назначена. Это не полностью подтверждённая уникальная карта.
Изменены только production src/input.c и src/main.c в НОВОЙ копии проекта.
PLL/EMI/PMIC/LCD/backlight и старая установленная сборка не редактировались.

## Офлайн-проверки

- C99, 11 packaging tests, heap positive + negative ASSERT PASS.
- 304597 game checks, PSRAM, original BL2/GFH/entry, 4 LCD profiles,
  8 fail-closed paths, RTC и повторные 45 game DMA/одна backlight init PASS.
- Native input: idle+78 bits79, combinations64, learned-map79 PASS.
- Точный Reset_Handler -> matrix_init: idle не включает learning,
  STAR3 включает, прежний bit2 не включает; 3/3 synthetic cases PASS.
- Writer106 unit tests +17 native cases PASS, DryRun PASS без открытия устройства.
- Протокол writer/strict_usb/stock DA/границы не изменялись. Точные hashes,
  размер образа и ожидаемые fixtures намеренно закреплены ДО одной новой пробы
  по новому запросу пользователя, не в обход отказа/не как auto-rebaseline.
- Это модели, не аппаратные проверки кнопок, PMIC/WDT, RAM или FPS.

## Pins НЕ записанного кандидата

```json
{
  "base_path": "C:\\Users\\USER\\Documents\\Codex\\2026-11-16\\senior-embedded-c99-developer-reverse-engineer\\work\\stock_da_trial_20261117\\sessions\\attempt_20261118_163444_240009\\full_after.bin",
  "base_sha256": "2d9f37c4a3507beb1dfde876f6cf88dff538f6ab7e91a444abb4e9b905bca2f3",
  "image_bytes": 14016,
  "image_sha256": "5172b9e8650e8b4f4432039f6a68dd572d69ff3cdfcb37c05d3a54bc145d7bc8",
  "patch_bytes": 16384,
  "patch_sha256": "21fe2c57216da8a7b923e0f48e779287beed13c1011d4cb8ceb4ca8c0ae60b92",
  "expected_after_sha256": "070715772e33c457fde486b0a3399786cee21816b96b098cebce91dfdf202a46",
  "allowed_range": [
    45056,
    61440
  ],
  "fresh_full_before_required": true,
  "full_readback_and_bytewise_required": true,
  "hardware_verified": false
}
```

ELF SHA256: `218943ed8552eac1d597a0149f0823c75e256a47d88d73519053c18f7dd1faf3`.
Последний известный установленный NOR остаётся историческим readback
`2d9f37c4a3507beb1dfde876f6cf88dff538f6ab7e91a444abb4e9b905bca2f3`.
**Это не новое чтение телефона. Expected-after 070715... не достигнут/не проверен.**
Кандидат: `C:\Users\USER\Documents\Codex\2026-11-16\senior-embedded-c99-developer-reverse-engineer\work\lcd_fps_20261117\keymap_photo_fix_20261118_183218`.

## Следующее действие

Для нового осознанного захода пользователь физически отключает USB,
снимает аккумулятор и подключает телефон к ПК без аккумулятора и без
зажатия кнопок, затем подтверждает готовность в чате. Автоматически
повторять текущую попытку запрещено, даже несмотря на отсутствие стирания.
В следующем разрешённом заходе по-прежнему нужны геометрия и свежие4MiB,
совпадающие с base, до любых D3/D5; диапазон только [0x00B000,0x00F000),
полный побайтный readback и проверка внешних диапазонов после, без reset.

В этом пакете нет NOR/DA binaries. Старые прошивки/сессии/отчёты сохранены.
