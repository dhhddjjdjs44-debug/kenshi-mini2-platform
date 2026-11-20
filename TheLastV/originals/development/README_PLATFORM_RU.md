# Быстрый старт своей игры — 20 ноября 2026

Сначала `docs/START_GAME_RU.md`. Правь `apps/demo_game.c`, запускай
`.\Preview-Game.ps1`: реальный ARM-код игры в локальном окне с тестовым HAL,
без Doom и без прошивки. Физические audio/vib и CPU measurement не готовы.
Полная прошивка по-прежнему не установлена; ниже состояние аппаратного порта.

# Kenshi Mini 2 — HW0.3 development

**20 ноября 2026. Новая сборка НЕ установлена, не sealed release.** На телефоне сейчас
**STOCK_CODE_RESTORED_CURRENT_NV_PRESERVED**; последняя verified NOR834bf…1fd85
не свежая live-база после работы стока. Пользователь сообщил, что батарея установлена.
В текущем offline checkpoint0USB/NOR/SDопераций; writer не создан.

Готовы: единая фото-карта20контактов (END unknown) для SDK/menu/Doom/key wizard;
дифференциальная оценка CPU в TCM, **EST MHZ**, не exact measurement. Собраны обе
пары loader+ELF;72MODEL/PCгруппы PASS. На телефоне эти изменения не проверялись.
**Физический PCM отсутствует, custom50ms PMU probe не ощущался, частота не измерена.**

Родной kernel+19DCMG декодированы. Stock motor override идёт в audio/DSP queue,
а не только PMU fallback. Native DSP patch/wakeup/PSRAM mapping воспроизведены
офлайн; real DSP ACK/аналоговый путь не доказаны. Стоковое DSPокно пересекает DoomBSS
на6728B и текущий cache-region: напрямую переносить адреса нельзя. Private stock
blobs/DSP patch исключены из SDK и публичных пакетов. Полный актуальный результат:
`REPORT_HW03_RU.md`; следующие шаги: `research/hw/RESEARCH_NEXT_RU.md`.

## Что уже можно делать

- Писать свою игру в `apps/demo_game.c`: `demo_init`, `demo_update`, `demo_render`.
- Использовать C99 SDK: RGB565 128×160, текст/прямоугольники, клавиши, время,
  собственные read-only ресурсы, статическую arena-память, очередь PCM и haptic API.
- Пользоваться оболочкой: GAMES / PHONE / MUSIC / VIDEO / DIAGNOSTICS,
  запускать игру и возвращаться; в сборке `doom` — приостанавливать/возобновлять Doom.
- Готовить на ПК WAV/KVID и пакеты ресурсов. Реальный поток видео реализован,
  не загрузочная картинка. Скорость на железе пока не измерена.

**Не готово:** реальный PCM-драйвер динамика, подтверждённый мотор, доказанная частота CPU,
автоматическое чтение исходного IMEI. Статусы `K_UNSUPPORTED`, `CPU MHZ UNKNOWN`,
`NO AUDIO DRIVER` — намеренные, а не обещание спрятанной работающей функции.
Телефонный режим — демонстрационный UI, без модема/связи/SMS. Выдавать его за
действующий телефон нельзя. IMEI/NV не записываются.

## Одна команда сборки

Из папки проекта в PowerShell:

```powershell
.\Build-Platform.ps1 -Flavor sdk
# Опционально: оболочка + реальный Doom
.\Build-Platform.ps1 -Flavor doom
```

На этом ПК Python/toolchain уже найдены. На другом: Python 3.10+ и `pyelftools`,
ARM GCC `arm-none-eabi`, переменная `ARM_NONE_EABI_PREFIX` с полным префиксом,
например `C:/toolchain/bin/arm-none-eabi-`; параметр `-Python` задаёт интерпретатор.
Прямая команда: `python tools/build_platform.py --flavor sdk`.
Новая C-часть собирается с `-Wall -Wextra -Werror`. Вендорный PureDOOM — без `-Werror`.
Для сборки `sdk` каталог Doom и WAD не требуются.

Результат:

- `build/platform/sdk/PLAT.ELF` — приложение для карты;
- `build/platform/sdk/UNFLASHED_platform_loader.bin` — **только кандидат** загрузчика;
- `build/platform/sdk/build-info.json`, `platform_pins.h`, map, stack-usage — бюджеты/контракт;
- аналогично `build/platform/doom` для интегрированной сборки;
- `stage/KDATA.PAK` — локальные демонстрационные ресурсы.

**Не копировать PLAT.ELF поверх DOOM.ELF в старой системе.** V11/V12 ожидают другой
ABI/имя/разметку. У каждой сборки свой новый загрузчик с pin размера, entry и PT_LOAD.
Pin — проверка компоновки, **не криптографическая подпись**. SHA256 проверяется в пакете
и при будущем ручном развёртывании; сам loader не аутентифицирует произвольный контент.
Изменение игры требует пересборки/повторного аудита пары, не только одного ELF.
Универсальная загрузка сторонних игр отдельными ELF в эту версию не входит.

## Быстрый старт своей игры

1. Открой `apps/demo_game.c`. Вся игровая логика находится в трёх функциях; в ней нет
   `kenshi_doom_*`, WAD или MMIO. Пример движет собственный спрайт, считает действия.
2. Состояние держи в `apps/demo_game.h`. Для MVP допустимы свои статические массивы.
   `k_arena_init/alloc/reset` дают ограниченную arena без Doom heap/общего malloc.
3. `update` получает время и логический ввод через `struct k_runtime`.
   Рисуй только в `render`, когда оболочка уже получила framebuffer lease.
4. Новый собственный ресурс добавь в KDATA.PAK через `tools/pack_assets.py`.
5. Собери **sdk**, запусти модельные тесты, затем договорись о новом физическом тесте.
   Скрипты сборки/тестов не работают с устройством.

Минимальная логика в update:

```c
if (r->input.pressed & K_ACTION) {
    ++g->score;
    /* Может вернуть K_UNSUPPORTED: физический мотор ещё не подключён. */
    (void)k_haptic_pulse(r, 50u);
}
```

## Кнопки оболочки

Общий источник: `sdk/include/k_keys.h`. По фото UP39,DOWN15,LEFT21,RIGHT30,OK42;
левая софт33,правая72,CALL24. Контакт END не установлен и не угадывается.
- Крестовина и2/8/4/6 — направления. UP больше не BACK.
- OK / левая софт — подтвердить;5 — игровое действие/выбор по контексту.
- Правая софт — назад/возврат из игры; в Doom левая софт открывает ESC-меню.
- Музыка/видео: OK/5 pause/resume;4/6 предыдущий/следующий;2/8 громкость0..8.
  Сейчас физического sinkнет; произвольные треки на SD не поддержаны автоматически.
- Диагностика:6страниц,4/6 перелистывают; OK запускает явный тест.
  CPU: EST MHZ/TCM DELTA, keys:21шага EXPECT/DETECTED/raw, END можно пропустить.
- В Doom4/6 strafe,5 use,0 map; диагностические chords сохранены.
Новая карта протестирована ARM-моделью, но её физическая повторная проверка ещё нужна.

## Телефонный ID

Исходный IMEI в этом пакете **не получен**, на экране UNAVAILABLE / STOCK CHECK DUE.
Не выдумывай цифры и не считай валидный checksum доказательством происхождения.
После сверки пользователем с заводской системой можно локально добавить `PHONE.ID`:
ровно15 ASCII-цифр, Luhn, без перевода строки, type4. Экран честно подпишет **ID FROM CONFIG**.
Скрипт не выводит значение в лог. Публично этот персональный pack распространять не нужно.
Это конфигурация отображения, не запись/подмена NV и не самостоятельная идентификация телефона.

## Медиа на ПК

См. `docs/MEDIA_FORMATS_RU.md`. Быстрая демонстрация (новое имя файла):

```powershell
python tools/media_pack.py --sample --out stage/NEW_DEMO.PAK
python tools/convert_media.py --video "C:/clips/input.mp4" --seconds 10 --out stage/CLIP.PAK
python tools/convert_media.py --audio "C:/music/input.mp3" --seconds 30 --out stage/MUSIC.PAK
```

`--ffmpeg C:/path/to/ffmpeg.exe` выбирает установленный на ПК FFmpeg.
Локальная исследовательская копия в `tools/vendor` может использоваться здесь, но в
передаваемый source SDK/утренний пакет внешний87MB FFmpeg **не включён**.
Конвертация на ПК ≠ MP4/MP3-кодек на телефоне. Без sink видео играет SILENT, музыка
пишет NO AUDIO DRIVER. PCM/AV sync проверены с fake HAL, **не динамиком телефона**.

## Проверки

```powershell
.\Test-Platform.ps1 -Flavor sdk
# С имеющимся doom1.wad и FFmpeg:
.\Test-Platform.ps1 -Flavor all -DoomWad "C:/path/DOOM1.WAD" -WithMediaConverter
```

Нужны Python `unicorn`2.1.x, `pyelftools`, Pillow; на этом ПК уже доступны.
Нативный ARM-код исполняется в Unicorn. SDK fixture подставляет fake HAL; парный тест
исполняет настоящий loader → SD register model → FAT → приложение. Это не аппаратный
cold boot, не реальное время, не проверка cache-coherency и не измерение FPS/частоты.
15 виртуальных минут lifecycle не заменяют15 минут игры на телефоне.

Утренний порядок и безопасное развёртывание: `docs/MORNING_TEST_RU.md`.
Лицензии/происхождение: `docs/THIRD_PARTY_NOTICES_RU.md`.
