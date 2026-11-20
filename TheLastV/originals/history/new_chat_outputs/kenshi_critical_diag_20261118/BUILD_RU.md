# Сборка офлайн-диагностики

Архив содержит project/ и rtc_model.py. Не содержит dump, DA, writer или команд
подключения к телефону. Это НЕ разрешение на запись. Следуйте REPORT_RU.md.

Для воспроизведения в текущей Windows-среде после распаковки выполните PowerShell
из папки с project/ (пути toolchain и исходного проверенного dump явные):

```powershell
$py = 'C:\MTK_Drivers\python_env\Scripts\python.exe'
$root = 'C:\Users\USER\Documents\Codex\2026-11-16\senior-embedded-c99-developer-reverse-engineer'
$env:PYTHONPATH = "$root\work\pydeps"
$env:PYTHONIOENCODING = 'utf-8'
$prefix = "$root\work\toolchain\bin\arm-none-eabi-"
$dump = "$root\outputs\kenshi_phone_check_20261116\kenshi_before_flash_20261116.bin"
& $py .\project\tools\build.py --prefix $prefix --dump $dump
& $py .\project\tools\check_heap_assert.py --prefix $prefix
& $py .\project\tests\verify_diag_native.py
```

В build остаётся историческое имя kenshi_tetris_maui.bin — инструменты не
переименованы и не ослаблены. Содержимое в этом архиве — CORE DIAG, не игра.
Ожидаемые SHA конкретного образа и патча — в scope-audit.json. ELF содержит
debug paths, поэтому при сборке из другой абсолютной папки его SHA может
отличаться даже при том же исполняемом payload. Сверяйте также MAUI/patch hash.
Неточность SOURCE_SHA для dump должна останавливать extractor, не отключайте её.
