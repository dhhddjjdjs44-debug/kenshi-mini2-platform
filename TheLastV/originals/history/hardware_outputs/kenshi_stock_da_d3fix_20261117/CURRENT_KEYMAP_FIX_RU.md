# Последняя попытка keypad fix: НЕ ЗАПИСАНО

18 ноября 2026 18:44:28 +05:00: один запуск остановился до открытия USB.
libusb found0 MediaTek0E8D:0003; DA initialization=false, transaction not_started,
NOR write=false, reads={}. Без повторов/FINISH/reset/reconnect/rollback.
Сессия: `C:\Users\USER\Documents\Codex\2026-11-16\senior-embedded-c99-developer-reverse-engineer\work\stock_da_trial_20261117\sessions\attempt_20261118_184428_696059`.
Кандидат: `C:\Users\USER\Documents\Codex\2026-11-16\senior-embedded-c99-developer-reverse-engineer\work\lcd_fps_20261117\keymap_photo_fix_20261118_183218`.
Новый patch 21fe2c57216da8a7b923e0f48e779287beed13c1011d4cb8ceb4ca8c0ae60b92 НЕ записан.
Expected NOR 070715772e33c457fde486b0a3399786cee21816b96b098cebce91dfdf202a46 НЕ достигнут.
Последний известный NOR 2d9f37c4a3507beb1dfde876f6cf88dff538f6ab7e91a444abb4e9b905bca2f3 — исторический readback.
Writer pins подготовлены для этого кандидата, но попытка остановлена;
НЕ ПОВТОРЯТЬ автоматически. Нужен новый человечески подтверждённый заход.
Границы [B000,F000), full fresh/geometry/readback/outer ranges обязательны.
Офлайн writer106+native17/DryRun PASS; защиты/протокол неизменны.
Актуальная установленная сборка остаётся прежней once-backlight game.

## Подготовленный пакет (не установлен)

# Исправленная раскладка — кандидат для одной разрешённой пробы

Пользователь: «Попробуй лучше запиши прошивку, будем на практике проверять».
Кандидат: `C:\Users\USER\Documents\Codex\2026-11-16\senior-embedded-c99-developer-reverse-engineer\work\lcd_fps_20261117\keymap_photo_fix_20261118_183218`. На этой стадии ещё НЕ записан.
LEFT21,RIGHT30,TURN42,DOWN15,DROP0,PAUSE33; aliases TURN9,DOWN6,PAUSE24.
STAR at boot = bit3. RIGHT/UP на фото совпали; UP пока тоже будет RIGHT,
отдельной привязки UP и красной трубки нет. Это не полная hardware verification.
Другие production изменения отсутствуют: PLL/EMI/PMIC/LCD/backlight прежние.

Base SHA256: 2d9f37c4a3507beb1dfde876f6cf88dff538f6ab7e91a444abb4e9b905bca2f3
Image 14016 bytes SHA256: 5172b9e8650e8b4f4432039f6a68dd572d69ff3cdfcb37c05d3a54bc145d7bc8
Patch SHA256: 21fe2c57216da8a7b923e0f48e779287beed13c1011d4cb8ceb4ca8c0ae60b92
Expected full NOR SHA256: 070715772e33c457fde486b0a3399786cee21816b96b098cebce91dfdf202a46
Диапазон только [0x00B000,0x00F000). Прежние runner pins израсходованы;
новые закреплены намеренно ДО новой пробы, не как реакция на отказ.
До D3/D5 обязательны live geometry + fresh full4MiB, точно равные base.
После обязательны full4MiB readback + побайтно + hash + outer ranges.
Одна попытка, без FINISH/reset/retry/reconnect/clear-halt/rollback.
При любой ошибке STOP. Ручной холодный старт только после verified_without_reset.

Офлайн: C99/packaging/heap+/negative/game304597/PSRAM/GFH/RTC/panels PASS;
keymap79 + combinations64 + learned79 + native STAR boot3 cases PASS;
repeat45/one-backlight PASS; writer106 + native17 PASS. Физическая проба ещё не начата.
