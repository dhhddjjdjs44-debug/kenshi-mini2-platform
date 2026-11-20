## Read-only SD/MP3 checkpoint — 2026-11-20T16:56:27.942241+05:00

Карта телефона свежо определена CIM: MINI_2USB/LUN0 → D:FAT32,16GB.
В My Music157MP3; начальные фреймы всех157: MPEG1LayerIII,44.1kHz,stereo,
320kbps в выборке (НЕ полная проверка/CBR). У custom WAV/KDATA player MP3 нет.
Ноль devicewrites/NOR/writer/форматирования; только перечисление+bounded headers.
USB-storage подтверждено, cold BootROM/готовность к прошивке — НЕТ.
Stock остаётся; audio/motor не готовы, MHz неизвестны. Отчёт:
`C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\phone_music_inventory_20261120_165133\REPORT_RU.md`.
Новый research audit24nativecases — не firmware regression/аппаратный успех.
Ниже старые offline checkpoints; формулировка «SDещёнеinventoried» устарела.

# Продолжение аппаратного порта — 20 ноября 2026, HW0.3

## Сначала восстановить состояние

- Работать только в этой UNSEALED копии; родители V11/V12/platform0.1 и
  frozen_doom_pair не менять и не пересобирать.
- Сейчас на телефоне **STOCK**, источник истины: родительский
  `work/current_installed_firmware.json`. Архивный verified NOR834bf…1fd85
  не является свежей live-базой после запуска стока. Все writers SPENT.
- Пользователь подтвердил динамик stock-плеера без наушников и вибро Snake.
  Позднее поправил: Snake audio не слышен, причина неизвестна.
- Последнее сообщение: «В телефоне аккум». Батарея есть СЕЙЧАС; это не означает
  USB/cold BootROM/readiness и не доказывает батарею при прежнем HW0.2 motor test.
- Текущее продолжение: 0 USB/NOR/SD операций, новый writer не создавался.
- Новый код уже исправляет общую карту кнопок и добавляет TCM EST MHZ.
  Обе пары loader/ELF собраны; полный свежий прогон 72 MODEL/PC групп PASS.
  Ни DSP, ни реальные CPU MHz, ни новые кнопки этим не подтверждены на телефоне.

## Уже закрыто — не повторять sweeps

1. ALICE_2 @0x1930C0: 1328768B, native range decoder/boundaries сверены.
   Исследовательская +2 branch-restoration копия использует base10250800;
   работает в конкретных проверенных путях, но whole-span/block-edge cases
   не следует объявлять решёнными. Main native BCJ использует другую схему+4.
2. Main kernel:1535504B, native LZMA с ALICE preset dictionary, затем native
   BCJ. Проверка `verify_native_kernel_decode.py` / `native-kernel-decode-audit.json`.
   runtimebase F0240750, SHA ae5ba4b7628b9afd59e724897209ee67af8a08822191ecbbb6a717ccf0384609.
3. Все19DCMG:223176B, native decoder и независимый LZMA дают byte-equal output;
   `verify_native_dcmg.py` / `native-dcmg-audit.json`. Overlay destinations
   пересекаются: в модель одновременно добавлять ровно нужный overlay, не все19.
   DCMG10:dest F015C580,26920B. Между декодированиями сбрасывать mutable context.
4. Standard LZMA без preset и повторный 75-property sweep не нужны.
5. Удобный inspector: `inspect_stock.py ADDRESS --overlay 10 --bytes 0x100`,
   ARM veneers показывать с `--arm`. Static references ещё не runtime proof.

Все decoded .bin и извлечённый DSP patch — private stock, НЕ SDK/release assets.
Старые F0*/TCM функции **не вызывать live** из нашего baremetal окружения.

## Вибро: найден реальный override, не останавливаться на PMU

`audit_stock_vibration_override.py` / `stock-vibration-override-audit.json`:
- DCMG10 F0161DCC загружает10260159; F015F9A0 ARM veneer →100344F1,
  registrar сохраняет callback вF00967BC.
- Native100344CC для output6 вызывает этот override при ненулевом указателе.
  Только null ведёт в generic fallback10033844.
- Handler10260158 ставит async message4559: callback1026CAD1,on/off,0.
  Нативный allocator подменён ОДНИМ явно обозначенным callback на сообщение;
  модель останавливается на входе OS send1031B93C, scheduling не подделывается.
- Extracted receiver1026CAD0 →102D46B0 →1030F790(on)/1030F8D8(off).
  Native submit slice пишет82207E60,5C,5E,5A. Stop снимает request15,
  затем ждёт DSP bit14; начало/полная init/ACK не доказаны.

`audit_stock_vibration_path.py` проверяет **ТОЛЬКО generic PMU fallback**:
полный native PMU init F015E555, device17→index8, контроль2, только EN0.
Actual stock TCM IRQ save/restore выполняются, но unresolved query0xBFD
заменён явным callback с обоими результатами0/1. 16cases PASS не board proof.
**1003B57C — PMU open, не I2C.** Wrapper1003B570 читает F008DC30, куда PMU init
регистрирует100106E9. Возврат1 верхнего wrapper не переносит nested PMU status.
Не менять voltage/discharge/SS наугад. Custom50ms probe пользователем НЕ ощущался.

## Аудио: bootstrap и место реального ожидания

- PCM ring (`audit_stock_pcm_ring.py`): data82250000, CTRL82207E0C, ARM W82207E0E,
  DSP R82207E10; state F00ACC08, length+10/start+12/end+14/relative+1C.
  2040native cases/4941advances,0stubs/patches.
- `pcm-protocol-model/`: отдельный clean C transport,2500synthetic ARM steps/5groups.
  Ready gate до любого DPRAM, ownership/backpressure/finite copy≤512word;
  не пишет consumerR/CTRL, не выдумывает played cursor. НЕ linked в firmware.
- `audit_stock_dsp_patch_bootstrap.py`: F0162D56(1), native ALICE getter/LZMA/
  static allocator,16patch entries/64configwrites,1023IDMAwords/1094MMIOwrites.
  Ноль instruction patches/call stubs. DSP не исполнялся; это не готовый DAC.
- `audit_stock_dsp_wakeup.py`: F027A884,20native writes,0stubs/patches.
  Synthetic +10/read clocks НЕ реальная задержка. Wakeup activation writes к
  82CC имеют ширину16bit; patch bootstrap выше использует32bit. Не смешивать.
- Native ready entry F027A6F0 ждёт82207400==5555, сбрасывает его, строитmapping
  F028F034, вызываетF02EE910(0), пишет82207402=6666, снова ждёт5555, затем
  таблицыF03743AC(110entries)/F0374734(79entries), остальную init.
  Модель БЕЗ ACK правильно останавливается в первом wait, не возвращает ready.
  Оригинальные ожидания unbounded: в наш порт их переносить нельзя.
- 5555/6666 на82207E92/94 — ARM memory selftest, НЕ DSP ACK.

Конкретные следующие static/native точки:
- Kernel initF024EF20 вызываетF0263788 (83010800 clock fields), затем
  F02D5498→1001A56C, wakeupF024EF3E→F027A884; F02D54C0→1001A638,
  F024EF7A→F027A6F0. Runtime wrapperF02637D0 вызывает wakeup+ready подряд.
- F02D1A98:82C00058&~20,83000400 low16|4,82C00214|200.
- DCMG10 F015DFB8 TOPSM init имеет unbounded wait83010040&F==1.
- Native F027A828→F024944C и F027A832→F02F70D4 — поздняя конфигурация/копии;
  F02F70D4 читает tableF0050134, её initialized data надо восстановить,
  нули модели нельзя считать реальным stock конфигом.
- Проверить domain power/clock/reset и полноценную загрузку DSP module,
  далее analog DAC/speaker route, mute/stop и аппаратный consumer.
  Чтение незапитанного domain само может повесить шину, обычный timeout после
  read это не исправляет. Не ungate modem вслепую.

## Память — найден потенциальный конфликт

`audit_stock_dsp_psram_mapping.py` выполняет native getter1002008C/builderF028F034
без stubs/MMIOwrites. Getter:3EB000/3F1000, mode0, size2000/4000. Табличные
слова C00383E8/C003C3F0 дают по алгоритму стока окна3E8000..3F0000 и3F0000..3F8000.
Это offline-интерпретация mapping, не аппаратная проверка всей aperture.
DoomBSS3E9A48 пересекает первое окно на6728B; текущий cache до400000 тоже их
накрывает. Нельзя переносить stock constants. Сначала отдельные aligned/uncached
DSP buffers, явные linker reservations/ASSERT и rebudget обоих flavours,
потом пересборка/PT_LOAD pins/paired tests и cache-coherency review. Резервов пока нет.

## CPU / ввод / музыка

- Новый EST MHZ probe готов, но не измерен: GPT26M +zero-waitTCM4/5cycle assumptions,
  три N/2N серии, reject при>2% inconsistencies.2% не абсолютная точность; exactHz0.
- Shared keymap готов:UP39,RIGHT30,leftsoft33/rightsoft72,ENDunknown. Сверять
  `sdk/include/k_keys.h`, photo authority `work/hw02_runtime_observation_20261120_132811/
  captured_key_contacts.json`. Никакой новой слепой карты.
- Music пока prepared mono16WAV вKDATA.PAK; arbitrary SDtracks/MyMusic/MP3 decoder
  не реализованы, файлы карты не inventoried. Fresh read-only card identity прежде
  любых файловых операций, старую букву диска не использовать. Форматировать не надо.

## Не подменять цель

Кнопки и CPU-only прошивка не означают «рабочий плеер+вибро». Нужны реальный PCM/
speaker, проверяемый безопасный motor path и физический CPU result. Пока они
незакрыты, не объявлять платформу готовой. Подробности `../../REPORT_HW03_RU.md`.
