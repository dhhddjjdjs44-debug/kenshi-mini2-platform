# Kenshi Platform0.1 установлена; холодный запуск ещё не проверен

2026-11-20T11:49:08.058946+05:00

Установлен интегрированный doom-вариант: launcher, самостоятельная игра,
телефонный demo UI, музыкальный/видеоплеер и optional Doom. PLAT.ELF/KDATA.PAK
скопированы на свежепроверенную microSD с Flush/reopen/full SHA256; WAD/старый DOOM.ELF сохранены.

Новый парный loader записан только в[B000,F000), четыре сектора.
До записи в этой же сессии проверены геометрия и полный4MiB fresh baseline.
После прочитаны все4MiB: точный overlay, outer/NV/bootloader неизменны,
независимый ELF PT_LOAD audit пройден. Readback SHA256: c536e743206fa8923a75c565afd758f43bd7a69ecb24949820e6c236c3e7acd8.
87 offline writer tests и dryrun PASS; штатная BootROM->DA initialization выполнена в этой же writer-сессии.
Нет reset/FINISH/retry/reconnect/clear-halt/rollback. Writer SPENT, повторять нельзя.

Это подтверждает запись NOR, НЕ работу меню/игры/видео на железе.
Ручной coldboot: отключить USB, установить батарею, включить. Ожидается KENSHI PLATFORM.
Первым проверить YOUR GAME и возврат, затем PHONE/VIDEO; Doom запускается отдельно.
MUSIC: NO AUDIO DRIVER ожидаемо; VIDEO: SILENT. Звук/мотор/CPU MHz не доказаны.
