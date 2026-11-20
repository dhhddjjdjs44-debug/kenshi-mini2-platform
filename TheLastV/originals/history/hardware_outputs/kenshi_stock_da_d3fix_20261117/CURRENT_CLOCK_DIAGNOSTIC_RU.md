# CLK DIAG V3 записана и полностью проверена

Дата: 2026-11-18T21:55:25.743039+05:00 (Asia/Yekaterinburg).
Разрешение пользователя: «Записывай», в ответ на предложение именно V3.

Ровно одна физическая WriteFourSectors завершилась `verified_without_reset`.
Независимый дисковый аудит подтвердил все4194304 байта NOR, точный overlay и ELF.

- Same-session fresh-before SHA-256: `c1597dd261cdecff1f419b776eaeb37f8ba559856859c7b56031868895acf075`.
- Фактический полный hardware readback SHA-256: `bc942e7a3e8baa0564fd7fb0017d6665007cc5c3280904a406ac129a9f8f84e5`.
- Patch SHA-256: `a8a8830bd57e9e23ecd1fee1ff06ee10163ac678a116add269590c4c62252c5e`.
- Только секторы11,12,13 отличаются;14 ужеFF. Все внешние байты сохранены.
- Одна D5, четыре подтверждённых пакета, geometry+full-before до записи.
- Нет ошибок USB, control transfers, FINISH/reset/retry/reconnect/rollback.

## Теперь проверить на телефоне

1. Отключить USB, установить батарею, включить обычной кнопкой **без STAR**.
2. Дождаться **CLK DIAG V3**; прислать фото экрана с DRAW/DMA/FPS/TCM100K/TCM1M.
3. Нажать **5**; сообщить, чувствуется ли короткий виброимпульс, и код VIB.

Запуск нового V3, реальные TCM-тайминги, новый FPS и физическое вибро пока
НЕ наблюдались. VIB1 — успешная операция с регистром, не доказательство движения.

## Версия и ограничения

Это V3: оптимизированная отрисовка, ограниченная TCM-петля, тест VIBR по5.
Номинальный 50-мс VIBR control pulse сохраняет VOSEL и восстанавливает исходное
слово. PLL/EMI/SFI/cache/voltage init не менялись. CPU MHz и реальный прирост FPS
не объявляются до наблюдения. Аудиовывод/SD ещё не реализованы. **Doom не записан.**

Границы `[0xB000,0xF000)`, четыре сектора. Протокол/USB/original DA unchanged,
перенастроены только точные SHA-pins, длина image, файлы и офлайн-fixtures.
Writer112 unit+17native PASS; DryRun PASS. Firmware11packaging+26diagnostic+
10clock+11TCM/VIBR, renderer/heap/BL2/GFH PASS (все это офлайн-проверки).

Разрешение на эту единственную попытку израсходовано. Writer остаётся на старой
базе c1597dd2...cf075; **не rerun и не auto-repin**. Ни один полный NOR/DA в отчёт
не включён. Сессия с полными личными acquisitions сохранена локально:
`C:\Users\USER\Documents\Codex\2026-11-16\senior-embedded-c99-developer-reverse-engineer\work\stock_da_trial_20261117\sessions\attempt_20261118_215349_558077`.

Previous writer pins remain spent; no physical rerun is authorized.
