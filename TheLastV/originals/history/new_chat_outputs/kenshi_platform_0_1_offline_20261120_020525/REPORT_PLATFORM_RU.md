# Ночная итерация Kenshi Mini 2: платформа 0.1

**20 ноября 2026, Asia/Yekaterinburg. OFFLINE, НЕ УСТАНОВЛЕНА.**
Пользователь ушёл спать. За эту итерацию0 физических операций,0 USB/NOR/card actions,
новый writer не создавался/не запускался. Установленная версия по актуальному указателю
по-прежнему **DOOM PERFORMANCE V11**. Полная целевая платформа ещё не готова.

## Сделано кодом, а не только планом

1. **C99 SDK + самостоятельная игра.** Video lease/RGB565/text/clipping, логические
   фронты/held/raw-key input, monotonic wrap-safe time, read-only assets, caller-owned
   memory arena, общая bounded PCM queue, haptic API. Типы Doom не участвуют в API.
2. **Новая оболочка.** Меню пяти приложений, независимая игра, возврат; optional Doom
   отдельно линкуется и поддерживает suspend/resume без догоняющих тиков после меню.
3. **Телефонный demo UI.** Набор/удаление/`*#06#`/любой непустой номер+OK→экран ID,
   coherent read-only RTC или явно UPTIME. Никаких вызовов модема/NV-записи.
   Исходный IMEI не получен; можно отдельно добавить приватный проверенный PHONE.ID,
   экран честно помечает config. В демонстрационный pack ID не включён.
4. **Read-only медиа.** WAV PCM16mono streaming, музыка pause/EOF/volume/track selection,
   KVID RGB565 покадровое чтение с ограниченным scratch, pause/restart/EOF/return;
   без физического sink — SILENT/NO AUDIO DRIVER. Программная AV-sync следует cursor
   реально сыгранных samples HAL, не числу отправленных данных.
5. **PC инструменты.** MP4/MP3/другой поддерживаемый PC FFmpeg-вход→KPA1/WAV/KVID,
   bounded duration, aspect preserving scale/pad; общий manifest packer ресурсов,
   проверка CRC и приватного config ID. Это не codecs на самом телефоне.
6. **Новый loader-контракт.** PLAT.ELF, optional KDATA.PAK/DOOM1.WAD, boot ABI32B,
   FAT/state/callbacks ниже64KiB, app от0x10000. Exact entry/length/PT_LOAD layout pins.
   Старый V11/V12 loader несовместим, нужна новая проверенная пара. Pins не подпись.
7. **Передаваемый независимый SDK.** Исходный ZIP содержит76 файлов, не содержит
   каталог Doom/WAD/stock dumps/внешние exe. Его отдельно распаковали, собрали без
   каталога Doom, получили bitexact sdk ELF+loader и прошли ARM/asset model tests.

## Сборки

| Flavor | PLAT.ELF | Loader | Свободно NOR | RAM после BSS |
|---|---:|---:|---:|---:|
|sdk без Doom |22 420B |13 964B |2420B |4 052 888B |
|shell + Doom |400 660B |13 964B |2420B |100 216B |

- sdk ELF SHA256 `c96b2431e57a8c88f66697fc0e215302aa44e9b6b1f46ee283a9ddc258847d73`
- sdk loader SHA256 `326ae7356bee17c4e1fc599409ddb61bdab7ab5053f03c1124d8d255d55d7cbe`
- doom ELF SHA256 `9dbfc426aaf21023dfc48ca8ace87defae3271f1b80ee5bad657a6e164af9f10`
- doom loader SHA256 `723ac80e2e99eb221ba468376131f9add620d0cfd9682ca80f29e743e29cbb78`

Остаток RAM не включает TCM stack в качестве «свободной памяти игры».
Максимальный single-function frame1328B у Doom не равен доказанному полному callstack;
модель отслеживает фактические stack stores. Min observed stack sdk0x70009A60,
doom0x70009668 при границе0x70009000. Непосещённые пути всё ещё требуют контроля.

## Что проверено

- **30 групп** real-ARM SDK с fake HAL: input/lifecycle/DMA lease, memory arena,
  asset/format/overflow/I/O faults, streaming, PCM partial/backpressure/errors,
  played-vs-submitted pause/EOF, game PCM bridge, haptic deadline/cancel/wrap,
  CPU UNKNOWN, optional RTC callback, UI rate limits.
- 80 воспроизводимых metadata mutations, malformed WAV/KVID/pack, CRC-content damage.
- **15 виртуальных минут,51 цикла demo↔menu**, плюс20 коротких циклов.
  Это НЕ15 минут физической устойчивости.
- Две real-loader → SD register model → fragmented FAT → real-ARM app интеграции.
  SDK71frames; shell+Doom126frames, в том числе20 после запуска Doom;
  pause/resume без роста gametic в меню. Отброшено4 несовместимых/битых ELF на flavor
  до изменения RAM-приложения. Optional pack/WAD проверены.0 SD write/erase commands.
- 6 групп PC-конвертера: синтетический MP4+AAC → pack → ARM video/EOF/return,
  fake PCM, silent/missing audio, no-overwrite/invalid geometry/duration/path.
- 3 группы manifest packer: bitexact pack, ошибки до создания output, приватный ID
  не раскрывается в выводе; реальных идентификаторов в тестах нет.
- Rebuild: deployable ELF/payload/loader bitexact. Отдельная сборка распакованного
  независимого source ZIP тоже bitexact, без Doom/WAD.
- Packaging audit: stripped/debug PT_LOAD идентичны, pins/entry/границы RAM/NOR,
  SRAM loader state<64KiB, GFH/payload, in-memory архивный overlay толькоsectors11..14.
  Архивный baseline НЕ текущий phone authority и не разрешение на запись.
- V11 **338 файлов** и V12 **224 файла** перепроверены по seals без изменений.
  current_installed_firmware.json тоже не изменён.

Evidence: `build/platform/test-results/*.json`, изображения **MODEL_ONLY**, source diff.
Старые скопированные V12 reports/build dirs в этой рабочей копии — исторические,
не evidence новой платформы. Нативный board model не моделирует реальные clock rates,
cache coherency, electrical routing или настоящий cold boot устройства.

## Что НЕ сделано (критично)

| Возможность | Реальный статус |
|---|---|
|Новая платформа на телефоне |not tested / not installed |
|Звук из динамика |not-implemented: аппаратный PCM sink отсутствует |
|Музыка на телефоне со звуком |blocked by actual PCM sink; software только |
|Вибрация |not-implemented в новом HAL, физически не подтверждена |
|260MHz/другая точная CPU frequency |не доказана; raw профиль B621/1401/div0, hz=0 |
|Исходный IMEI |не извлечён; config не равно доказанному stock identity |
|Video performance/AV-sync на железе |не проверено; нет аппаратного audio clock |
|Physical UP/right |raw mapping ambiguity осталась; numeric fallback есть |
|15min настоящего gameplay/SD/cache |не проверено; старый lateED08 не объявлен исправленным |

Полная machine-readable матрица — CAPABILITIES.json.
Нельзя выдавать fake HAL/ненулевой PCM/PMIC readback за динамик/мотор.
Внешний placeholder FIFO-пример не портировали как «готовый драйвер».

## Утро

Открыть README_PLATFORM_RU.md и docs/MORNING_TEST_RU.md. Сначала свежая готовность
пользователя/питание, новый reviewed card allowlist, затем отдельная безопасная установка
выбранной loader+app пары. Никакого запуска SPENT writer/format/fullrestore/auto retry.
Сначала menus/own game/video/keys, затем отдельные физические audio/motor/clock milestones.
Свою игровую логику уже можно писать/собирать независимо от Doom, но это ещё не означает,
что полный аппаратный SDK закончен. Новые аппаратные результаты нужны утром.
