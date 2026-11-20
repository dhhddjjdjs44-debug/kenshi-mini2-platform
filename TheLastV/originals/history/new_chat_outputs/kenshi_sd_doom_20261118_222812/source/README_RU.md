# Исходники SD/FAT/ELF и Doom — только офлайн

Лицензия GPL-2.0, полный текст в LICENSE. PureDOOM сохранён без изменений;
upstream commit 355cfbd16fac119718879239336ee2ea408886bd.
WAD, полный NOR, DA и прошивальщик намеренно отсутствуют.

## Сборка и проверки

Требуются Python 3, GNU Arm Embedded GCC (проверено 14.2.1), pyelftools и unicorn.
Запускать из этой папки. CROSS_COMPILE — префикс arm-none-eabi-, при необходимости полный путь.

```powershell
$env:CROSS_COMPILE='C:/path/to/bin/arm-none-eabi-'
python build.py
python tests/native_storage.py --unit-only
python tests/native_msdc.py
$env:KENSHI_TEST_WAD='C:/path/to/your/doom1.wad'
python tests/native_storage.py
```

Последняя проверка ожидает IWAD Doom shareware с SHA-256
1d7d43be501e67d927e415e0b8f3e29c3bf33075e859721816f652a526cac771.
Проверки создают разреженный диск в памяти, не обращаются к физическим накопителям.
Изображение MODEL_ONLY — framebuffer ARM-модели, не фотография телефона.

## Границы реализации

* FAT16/FAT32: 512-байтовые секторы; MBR либо superfloppy; только корень,
  короткие имена 8.3, DOOM.ELF и DOOM1.WAD. GPT/exFAT/FAT12 и подкаталоги не поддержаны.
* Цепь файла проверяется целиком при открытии, лишние кластеры после размера
  файла отвергаются. Циклы/плохие кластеры/ошибки чтения не чинятся.
* 64 якоря на файл и отдельный 8-КиБ кэш FAT; динамического выделения нет.
* ELF32/ARM/EABI5/soft-float: PT_LOAD только 0x10000..0x400000, без перекрытий
  и W+X; TCM NOLOAD mailbox сохраняется, инициализированные данные туда запрещены.
  Это проверка структуры и границ, не криптографическая подпись.
* storage.elf — вызываемый модуль, НЕ образ начальной загрузки. Низкая RAM для
  состояния/стека должна быть отдельно освобождена платой; старый LCD DMA должен
  быть остановлен ДО загрузки. platform_prepare_engine по умолчанию возвращает 0.
* platform_sector_read по умолчанию возвращает ошибку. msdc_ro.c — отдельный
  CMD17 PIO-примитив для УЖЕ настроенной карты/контроллера, без card enumeration,
  PMIC/pinmux/clock bring-up. Модельные проверки не доказывают работу слота.
* После загрузки caller обязан настроить engine clock/LCD/DMA state, передать
  storage_wad в kenshi_doom_init и организовать цикл шагов. Это ещё НЕ реализовано
  как аппаратный handoff. Не прыгать в entry как в reset vector.
* Программный микшер проверен; аппаратный DAC/динамик не подключён.

НИКАКИЕ файлы этой папки не предназначены для WriteFourSectors.
Не увеличивать разрешённый диапазон NOR. Не форматировать карту пользователя.
