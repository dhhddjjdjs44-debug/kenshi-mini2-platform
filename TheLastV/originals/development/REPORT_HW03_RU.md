## SDK для своей игры выдан отдельно — 2026-11-20T17:15:19.011950+05:00

Проверенный PC-start комплект: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_game_sdk_start_20261120_170604`.
Указатель: work/current_game_sdk_starter.json. Независимый отDoom SDK распакован,
собран и проверен:70групп, documented Preview-Game.ps1 -Headless PASS.
В UNSEALED development78MODEL/PCгрупп PASS; добавлены6preview tests.
Preview исполняет реальный ARM-код игры с FAKEHAL, не весь телефон и не аппаратный FPS.
Своя игра: apps/demo_game.c/.h; guide docs/START_GAME_RU.md. В экспортированном SDK
AGENTS.md самостоятельный: править sdk/комплекта, не provenanceworking_copy.
Телефон остаётся STOCK;0deviceoperations в этой итерации, binaries unchanged;
customaudio/vib нет, MHz неизвестны, MP3 direct player нет. Полный аппаратный релиз
НЕ готов, SDK-start не подмена этим требованиям. USB-storage observation неcoldBootROM.
Для каждой новой сборки игры пока парныеloader/ELFpins: не обещать SD-onlyupdate.

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

# HW0.3: кнопки / оценка CPU / родной DSP и вибро

Checkpoint: 2026-11-20T16:39:36.102919+05:00. **Это ещё не релиз с рабочим звуком и мотором.**

## Устройство

На телефоне STOCK_CODE_RESTORED_CURRENT_NV_PRESERVED. Последний проверенный полный NOR: `834bf1dc728d27d4b77242ea1b943fd0d0ba73fafe4376ab24a5194d4dd1fd85` — архивный readback, не свежая live-база после работы стока. Пользователь подтвердил плеер через динамик без наушников, вибро змейки; звук змейки впоследствии НЕ слышен. Сейчас пользователь сообщил: «В телефоне аккум». Батарея при прежнем неудачном custom50ms тесте неизвестна.

В текущем offline-продолжении **0 USB/NOR/SD операций, writer не создан**. Все прошлые writers SPENT. Батарея сейчас не означает холодный BootROM или готовность к новой записи.

## Готовые изменения кода

- Единая карта `sdk/include/k_keys.h` / `sdk/src/k_keys.c` для SDK, launcher, raw-мастера и Doom. По фото UP=39, RIGHT=30, left soft=33, right soft=72; END остаётся unknown255. В SDK левая софт выбирает, правая возвращает; в Doom левая софт — ESC, правая — shell. Цифровой fallback и игровые chords сохранены. Новая карта на телефоне ещё не проверена.
- `ports/cpu_tcm.c` / `ports/cpu_work.S`: дифференциальная оценка частоты N/2N, A=SUBS/BNE, B=ADD/SUBS/BNE, N=65536,3 серии. Используется прежний16B TCM scratch с восстановлением на выходах. Базовые допущения — GPT26MHz и zero-wait ARM7 цикл4/5; проверка согласования2% не является метрологической погрешностью. IRQ/FIQ должны уже быть masked; MSR/MCR/CPS/SVC не исполняются. UI показывает **EST MHZ**, exactHz=0. На телефоне НЕ измерено, 260MHz не утверждаются.

## Прорыв по стоковому мотору

Реальная DCMG10 registration call: `F0161DCC` загружает `10260159`, veneer `F015F9A0` идёт в registrar `100344F1`, запись `F00967BC`. Native wrapper `100344CC` для output6 выбирает зарегистрированную функцию; только при null идёт в generic PMU fallback `10033844`. Handler ставит сообщение `4559`/callback `1026CAD1`; получатель вызывает `102D46B0`, далее engine on/off `1030F790`/`1030F8D8`. Native submit slice пишет DPRAM `82207E60/5C/5E/5A`; stop снимает request15 и ждёт DSP. Это **не доказанный физический мотор**.

`stock-vibration-override-audit.json`: два on/off случая,1явная allocator-подстановка на сообщение, остановка на входе OS send без подделки scheduling/success; extracted receiver и mailbox-срезы отдельно. Generic PMU audit16cases выполняет native PMU init/TCM IRQ, но содержит1обозначенный query callback и проверяет **только fallback**, не активный board override.

Исправление прошлых терминов: `1003B57C` — **PMU open**, не I2C; `1003B570` читает dispatch pointer `F008DC30`, установленный native PMU init в `100106E9`. Нельзя делать вывод «PMU EN работает в модели → мотор исправлен». Напряжение/discharge не менять наугад.

## Аудио: что доказано офлайн

- Main kernel1535504B и19DCMG/223176B декодированы оригинальными decoder/BCJ и сверены с независимым декодированием. Это не загрузка всего stockOS. ALICE runtimebase10250800 используется в проверенных путях, но whole-span/block-edge translation остаётся отдельным ограничением.
- Native PCM ring: data82250000, CTRL82207E0C, producerW82207E0E, consumerR82207E10;2040nativecases/4941advances. Изолированный C-transport прошёл2500syntheticARMsteps/5groups, **не включён в прошивку**, boot/route отсутствуют.
- Native patch initializer `F0162D56` с исходным getter/LZMA/staticallocator воспроизводит1094MMIOwrites,16patch entries/1023IDMAwords. DSP не исполнялся. Private patch/decoded stock не включать в SDK/публичный пакет.
- Native wakeup `F027A884`:20expectedwrites,0callstubs/patches, синтетическое время. Следующий native ready `F027A6F0` БЕЗ поддельного ACK остановлен bounded-моделью в ожидании `82207400=5555`; оригинальное ожидание бесконечное. ARM selftest5555/6666 на82207E92/94 **не DSP ACK**.
- Native PSRAM getter/builder: буферы3EB000/3F1000,size2000/4000, а отображаемые окна3E8000..3F0000 и3F0000..3F8000. **Doom BSS перекрывает первое окно на6728B.** Сейчас резервов нет, оба окна не портированы. До live DSP нужны явный linker-reserve, пересчёт всех PT_LOAD и cache/DSP coherency: существующий Doom cache-регион до400000 тоже перекрывает окна.
- Физический sink всё ещё K_UNSUPPORTED; плеер читает только подготовленный mono16WAV изKDATA.PAK. Наличие музыки на16GB SD не означает поддержку её имён/форматов. Требуются свежая идентификация карты, read-only inventory и direct-files API/декодер либо согласованная конвертация.

## Проверки текущих файлов

Полный чистый MODEL/PC прогон:72группы — SDK30,hardware11,TCM5,diagnostics10,keymap5,packer3,converter6,paired2. Лог `build/platform/hw03-full-regression-clean.log`; свежесть ELF/report hashes проверена в `work/hw03_checkpoint_20261120/verification.json`.
Свежий packaging-аудит: обе пары PT_LOAD/pins/budget PASS, loader13964B/NORfree2420B; RAM slack sdk4044248B,doom91576B — **до резервов DSP**. Sealed parents338V11/224V12/670platform0.1 и12frozen-HW02files проверены read-only. Low-level исходники родителя сохранены; Doom adapter менялся только для общего ввода.

Новые native-аудиты находятся в `research/hw/stock-*-audit.json`. Не складывать native/modelcases и группы тестов в «аппаратные проверки». Релиз/архив пока не создан; packager исправлен под новый24u32 hw-report/CPU+keys tests и отдельные loaderELF/BIN hashes.

## Следующее действие

1. Проследить power/clock/reset и два ready-перехода DSP до запуска DLL/PCM; не исполнять старые F0*/TCM veneers в baremetal.
2. Выделить отдельные uncached DSP buffers/windows, проверить отсутствие BSS/cache collision, then bounded init/mute/stop/ACK faults. Не переносить stock virtual RAM addresses.
3. Довести speaker routing + PCM consumer; затем объединить плеер и DSP-vib с автономным safety-off/ограниченным stop. Нельзя обещать мотор из mailbox slice.
4. Узнать реальные файлы на freshly identified SD; keys/CPU готовы к аппаратной проверке, но ими не подменять цель «рабочая музыка+вибро».
5. Для установки — свежая фактическая готовность и отдельная one-use процедура по PHONE_OPERATION, не повтор старого writer.
