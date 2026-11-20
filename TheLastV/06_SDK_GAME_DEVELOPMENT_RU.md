# 6. Разработка своей игры и команды ПК

## Где писать

Проверенная рабочая копия для игры:
`C:/Users/USER/Documents/Codex/2026-11-18/new-chat/outputs/kenshi_game_sdk_start_20261120_170604/sdk`.
Архив рядом: `Kenshi_SDK_independent_sources.zip`, без Doom/WAD/stock dump/writer.
TheLastV содержит документацию, не дублирует SDK и внешние исполняемые tools.

В PowerShell перейти в SDK:

```powershell
Set-Location -LiteralPath 'C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_game_sdk_start_20261120_170604\sdk'
.\Preview-Game.ps1
```

Править `apps/demo_game.c` и `.h` в этой SDK-папке. Не редактировать старую
папку, указанную в provenance как working_copy: это происхождение, не команда.
Независимый SDK не содержит Doom; игра стартует из демо-слота общего PLAT.ELF.

## Быстрый цикл

1. Изменить механику/состояние/отрисовку.
2. Закрыть preview и снова выполнить `Preview-Game.ps1`: ARM-код пересобирается.
3. По умолчанию открывается YOUR GAME. `-Menu` начинает с launcher.
4. Для автоматического smoke-test: `Preview-Game.ps1 -Headless`.
5. Скриншот: `build/platform/preview/MODEL_ONLY_game.png` внутри SDK.

Нет hot reload. Окно — real ARM C + fake HAL, виртуальный шаг 33ms, не телефонная
скорость. Звук и мотор намеренно unsupported. KDATA.PAK preview максимум 2MiB:
это буфер fixture, а не предел потокового SD телефона.

## API

- `demo_init` — начальное состояние; `demo_update` — ввод/механика;
  `demo_render` — рисование при полученном framebuffer lease.
- `r->now`: монотонные uint32 milliseconds с wrap. `dt` считать разностью,
  большие задержки ограничивать осмысленно; не ускорять игру из-за FPS.
- `r->input.held/pressed/released`: битовые маски. `digits`: фронты 0..9, *#.
  Не обрабатывать одно действие повторно через оба поля без необходимости.
- `K_WIDTH=128`, `K_HEIGHT=160`, RGB565. Рисовать только с действительной lease,
  после present не писать до нового acquire. `K_BUSY` — вернуться к poll,
  а не крутить бесконечное ожидание или писать в занятый DMA framebuffer.
- `k_rect/k_text/k_number/k_hex` — ограниченная экраном отрисовка.
- `k_asset_find/read/verify` — read-only ресурсы. CRC проверка явная,
  не путать CRC с подписью/аутентификацией.
- `k_arena_init/alloc/reset`: caller-owned arena, без индивидуального free.
  После reset прежние указатели недействительны. Проверять NULL/ошибки.
- `k_audio_*` и `k_haptic_pulse/cancel`: вызывать через SDK, обрабатывать
  K_UNSUPPORTED, не обращаться к PMIC/PLL из игровой логики.

Детальный неизменённый контракт: `originals/development/docs/SDK_API_RU.md`.

## Полная сборка кандидата

```powershell
.\Build-Platform.ps1 -Flavor sdk
.\Test-Platform.ps1 -Flavor sdk
```

В полной research-development копии с Doom доступно `-Flavor doom` или `all`;
в независимом архиве Doom исходников нет, поэтому `doom/all` там не использовать.
Опциональный конвертер тестируется через `-WithMediaConverter` при наличии FFmpeg.
В main development новый полный all+converter прогон дал 78 групп;
в отдельном SDK sdk-прогон —70. Модельные PASS не hardware verified.

Выход: `build/platform/sdk/PLAT.ELF`, `UNFLASHED_platform_loader.bin`,
`platform.elf`, `platform_pins.h`, `build-info.json`, linker map и stack usage.
Сам бинарник загрузчика не является командой записи.

**Важно:** loader pins привязаны к entry/размеру/PT_LOAD этого ELF.
После правки игры пересобираются и проверяются оба; нынешний loader не позволяет
просто заменить произвольный ELF только на SD. Не отключать pins ради удобства.
Удобное обновление игр без NOR — отдельная незакрытая задача.

## Инструменты

ARM GCC `arm-none-eabi-*`, Python3.10+, pyelftools; preview/tests ещё Unicorn,
Pillow и Tkinter/TclTk для окна. Бинарники инструментов в архив не включены.
На этом ПК уже найдены; на другом устанавливаются отдельно, сами скрипты из
сети ничего не скачивают. `-Python` задаёт интерпретатор;
`ARM_NONE_EABI_PREFIX` — полный путь с префиксом; `KENSHI_PYDEPS` — каталог модулей.

Полезные найденные пути этого ПК:
- сборки/research Python: `C:/MTK_Drivers/python_env/Scripts/python.exe`;
- tests/preview Python: `C:/Users/USER/.cache/codex-runtimes/codex-primary-runtime/dependencies/python/python.exe`;
- toolchain: `C:/Users/USER/Documents/Codex/2026-11-16/senior-embedded-c99-developer-reverse-engineer/work/toolchain/bin/arm-none-eabi-`.

Не обещаны запись save-файлов, произвольные MP3, русские шрифты, динамический plugin
ABI и гарантированные 60FPS. Нужная игра должна корректно работать без звука/вибро,
пока физические драйверы не прошли отдельную приёмку.
