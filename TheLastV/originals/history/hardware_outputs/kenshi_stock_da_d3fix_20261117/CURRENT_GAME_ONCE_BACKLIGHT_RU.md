## Актуально: 18 ноября 2026, запись 16:34:44–16:35:05 +05:00

Игровой Тетрис с ОДНОЙ настройкой подсветки записан один раз в [B000,F000).
Проект: `work/lcd_fps_20261117/game_once_backlight_20261118_162900/project`.
Сессия: `work/stock_da_trial_20261117/sessions/attempt_20261118_163444_240009`.
Fresh base: `7b312161b8fccf69eade0a24db8a5e9eb95724cd9f53c3ca5d82d752ada2f736`.
Patch: `9d99ca8a2db5e837c717b5f54e3e6e1b98a6c520af712b6dccf063c7073fbe14`.
Полный NOR/readback: `2d9f37c4a3507beb1dfde876f6cf88dff538f6ab7e91a444abb4e9b905bca2f3`.

Геометрия+свежие4MiB в той же DA session совпали. После одной D5/4 blocks
full4MiB readback побайтно, SHA и independent disk audit PASS. Изменены только
сектора 11–14; загрузчики/все внешние байты равны fresh before, системный хвост
не ремонтировали. Без ошибок USB/F0/CDC/FINISH/reset/retries/clear-halt/
reconnect/rollback. Ручной холодный старт новой сборки ещё НЕ проверен.

### Что изменено относительно устойчивой hold-сборки
Только src/main.c: удалён first_frame_hold и вызов. Анимация/tetris_tick,
обработка матрицы и повторные игровые DMA возвращены. board_backlight_init
по-прежнему вызывается только рано в boot_main. Все другие src/include/linker
побайтно прежние; PLL/питание/SD/звук/вибрация/mapping не менялись.
Счётчика A001 теперь НЕ ожидаем: это была намеренно остановленная hold-версия.
Строки KEYS/FPS/MS снова обновляются игровым кадром; CPU? — классификация
регистров, не ошибка и не измеренная частота.

### Управление для проверки
Кандидаты крестовины/OK ещё физически не подтверждены. Кодовые цифровые дубли
без изменения: 4/6 — влево/вправо, 5 — поворот, 8 — мягкое падение,
2 — сброс, 0 — пауза. Если mapping не подходит, код предусматривает «*»
при старте, затем отпускание и назначение LEFT/RIGHT/TURN/DOWN/DROP/PAUSE.
Обучение только RAM, NOR не меняет. Работа каждой физической кнопки пока
не подтверждена. Холодный старт: USB отключить, батарею снять/вернуть, включить.
Зафиксировать движение фигур, отклик кнопок и наличие/отсутствие погасания.

C99/11 packaging/heap+negative/game304597/PSRAM/BL2-GFH/RTC/4 profiles+8 failures
PASS. Native repeat45 frames + background: один backlight, игровые actions,
горизонтальное движение/гравитация и 7 разных framebuffer проверены.
Зависание второго gameDMA fail-closed C5, completion race/immediate PASS.
Writer104 tests+17 native cases и DryRun PASS. Всё это synthetic MMIO,
не реальное PMIC/WDT reset/electrical/FPS измерение.

Причина старого погасания НЕ доказана до нового аппаратного наблюдения.
Разрешение на текущую пробу использовано, база7b312...a2f736 SPENT.
Не повторять runner и не auto-repin/reset/rollback; старые разделы ниже — архив.

