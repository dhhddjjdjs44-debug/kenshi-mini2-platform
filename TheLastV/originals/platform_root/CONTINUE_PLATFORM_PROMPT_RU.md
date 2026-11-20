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

## HW0.3: актуальная точка продолжения — 2026-11-20T16:41:40.830759+05:00

**Устройство: STOCK**, не платформа0.1 и не HW0.3. Authority: `work/current_installed_firmware.json`,
последний verifiedNOR834bf…1fd85 НЕfreshlivebaseline послеstockboot. Пользователь:
динамикплеера слышен безнаушников, Snakevibесть, SnakeaudioНЕслышен; батареяустановлена
сейчас («В телефоне аккум»), подключение/coldBootROMнеподтверждены. Вэтомofflinecheckpoint
0USB/NOR/SDoperations; старыеwritersSPENT, новыйwriterне создан.

**Разработка:** `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\platform_hw_20261120_115700`
UNSEALED, можно продолжатьздесь. Последнийотчёт: `REPORT_HW03_RU.md`;
`work/current_hw_diagnostics_candidate.json` и `work/current_platform_development.json`
обновлены по фактическим ELF/loaderhashes. SealedV11/V12/0.1/frozenHW02неправить.

**Реализовано в кандидате:** общаяфото-карта20контактовSDK/shell/Doom/tester (UP39,
RIGHT30,leftsoft33/rightsoft72,ENDunknown); новаяTCMESTMHZоценкаA/B,N/2N,3серии.
72MODEL/PCгруппыPASS,обаpairedloader/FAT/app; ЭТОНЕhardware-retеst. exactCPUHz0,
260MHzне доказаны. ФизическийaudioHAL/motor_setвсёещёunsupported; прежнийPMUprobe
НЕощущался. Ключеваянаходка:stockmotoroverride идётвaudio/DSP,неgenericPMUfallback.

**Не повторять закрытое исследование:** mainkernel1535504B и19DCMG223176B уже
native-decoded/BCJпроверены; bootstrapDSPpatch,wakeup,PCMring,mappingвоспроизведены
офлайн. ПолнаяstockOS/DSPнеbooted,realACK/analogrouteнет. StockDSPокнапересекают
DoomBSS6728B/cache-регион:непереноситьадреса/старыеF0*/TCMвызовыlive.
Следующийшаг:`research/hw/RESEARCH_NEXT_RU.md`. МузыкасSDещёнеinventoried;плеертолько
preparedmono16WAVизKDATA.PAK,произвольныеSDtracks/MP3неподдержаны. PrivateDSPstock
blobsНЕвSDK/публичныйпакет. Ниже—историяипостоянныеограничения; этотcheckpointновее.

## Актуальное продолжение20ноября2026: hardware-first

На телефоне уже установлена платформа0.1 DOOM; пользователь подтвердил работу,
иногда>50FPS. Последняя NOR authority c536e743…e7acd8; свежей аппаратной базы нет.
Новый диагностический кандидат0.2 НЕ установлен, рабочая копия UNSEALED:
C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\platform_hw_20261120_115700
Указатель: work/current_hw_diagnostics_candidate.json; отчёт REPORT_HW_PRIORITY_RU.md.
Моторный probe/CPU lower-bound/key capture/profile реализованы и моделируются,
PCM НЕ реализован. Новое по звуку: ALICE распакован, stockAFE slice найден;
продолжать по research/hw/RESEARCH_NEXT_RU.md. Старые sealed-copy/writer не трогать.

Ниже — предыдущие checkpoint/история; installed authority читать из current_installed.

# Продолжение после ночной реализации20ноября2026

Актуальный checkpoint ниже ПЕРЕОПРЕДЕЛЯЕТ старую команду «сначала выдели SDK»:
SDK/самостоятельный пример/оболочка уже написаны. Не начинай заново и не запускай
унаследованные V12 build/writer scripts из новой копии.

## Реализованная offline-платформа — 2026-11-20T02:07:33.332358+05:00

Это актуальный checkpoint; пункты ниже, написанные19ноября, — исходный план/история.
- Новый самостоятельный SDK/launcher/phone UI/WAV+KVID software и конвертер реализованы.
- Ночная рабочая копия: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\platform_mvp_20261120_005032`. Дальнейшие изменения после seal — только новая копия.
- Передаваемый проверенный пакет: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_platform_0_1_offline_20261120_020525`. **НЕ установлен**, на устройстве остаётсяV11.
- Указатели: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\current_platform_candidate.json` и `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\current_platform_development.json`.
- Быстрый результат: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\NIGHT_PLATFORM_RESULT_RU.md`; подробный отчёт: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_platform_0_1_offline_20261120_020525\REPORT_PLATFORM_RU.md`.
-30ARM SDK groups,2paired loader/FAT/app models,15виртуальных минут lifecycle,
  independent source ZIP безDoom/WAD отдельно собран bitexact. Это НЕ hardware tests.
- **Не закрыты:** физический PCM/speaker, мотор, доказанная CPU frequency,
  исходныйIMEI, новая прошивка/видео на настоящем телефоне, неоднозначныйphysicalUP.
  См. CAPABILITIES.json / docs/HARDWARE_BLOCKERS_RU.md.
-0USB/card/NOR операций, writer не создан/не запущен. Новые имена PLAT.ELF/KDATA.PAK
  требуют парный новый loader и отдельный freshly-reviewed card allowlist/one-use attempt.


## Следующая сессия

1. Прочитай NIGHT_PLATFORM_RESULT_RU.md, пакетный REPORT_PLATFORM_RU.md,
   README_PLATFORM_RU.md, CAPABILITIES.json и docs/MORNING_TEST_RU.md.
2. Установленную V11 и sealedV11/V12/новый snapshot не редактировать/не пересобирать.
   Если нужен code fix — новая рабочая копия с recorded parent seal.
3. Если пользователя ещё нет у телефона: только offline работа, никаких device operations.
4. Когда пользователь вернулся: сначала актуальные researchAGENTS/PHONE_OPERATION,
   его свежая аппаратная готовность, конкретный flavour и отдельная безопасная установка.
   НовыйPLAT.ELF несовместим со старымloader. Физический writer в пакете отсутствует.
5. Приёмка сначалаmenus→own game→phoneUI→video→back, raw-key calibration,
   затемDoom/resume и15мин реальной устойчивости. Модель не заменяет этот тест.
6. АппаратныйPCM — главный незакрытый driver: не принимать предположительныеFIFO
   из внешнегоpcm_player.c за доказательство. Мотор/CPU частота тоже не подтверждены.
   Не ставитьsupported/260MHz в capabilities ради срока20ноября.
7. Собственная игра пользователя начинается вapps/demo_game.c безDoom.
   При замене ресурсов соблюдать новыйreviewed allowlist, сохранитьWAD/прочее,
   не предполагать буквукарты и не трогатьhostdisks/NV.

---
# Исходный промпт19ноября (история и сохраняющиеся ограничения)

# Готовый промпт для продолжения

Продолжай разработку Kenshi Mini 2 по плану:
`C:\Users\USER\Documents\Codex\2026-11-18\new-chat\PLATFORM_PLAN_RU.md`.

Главная цель пользователя — **платформа и общий игровой runtime для своей игры**, не отдельный Doom-порт. Doom — нагрузочный и регрессионный тест, одно из приложений. Целевой день рабочего MVP — **20 ноября 2026 года, Asia/Yekaterinburg**; если эта дата уже прошла, явно сообщи актуальное состояние, не изображай, что срок ещё впереди. Это целевой срок, не основание подделывать готовность.

Прочитай также новый целевой состав: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\FIRMWARE_MVP_SCOPE_RU.md`.
Пользователь добавил launcher игр с возвратом, телефонный демонстрационный режим (любой набранный номер + вызов → исходный IMEI без звонка), музыкальный и видеоплеер. Это теперь целевые пункты MVP. IMEI/NV не менять и идентификатор не выдумывать. Для музыки/видео нужен общий аппаратный PCM sink. Для первого видео допустим подготовленный на ПК простой формат; затем синхронный звук. Не обещать любые MP4/MP3 или FPS без проверки. Оценивать реальные приложения и переходы, не пустые меню. Сотовая связь/универсальная загрузка чужих ELF не требуются.

Начни с актуальных локальных указателей:
- `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\current_installed_firmware.json`;
- `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\current_v12_candidate.json`;
- `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\current_v12_development.json`;
- `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\current_stock_clock_research.json`.

Прочитай инструкции:
`C:\Users\USER\Documents\Codex\2026-11-16\senior-embedded-c99-developer-reverse-engineer\AGENTS.md`
и `C:\Users\USER\Documents\Codex\2026-11-16\senior-embedded-c99-developer-reverse-engineer\PHONE_OPERATION_RU.md`.

Контрольная точка при составлении промпта (2026-11-19T20:44:41+05:00): V11 установлена, V12 SEALED OFFLINE NOT FLASHED. Указатели могут обновиться — приоритет у проверенного актуального состояния. V12 находится в `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_v12_20261119_200415`; не редактируй/не пересобирай запечатанный оригинал. Пользуйся новой рабочей копией с записанным происхождением; не трогай чужие изменения.

Первая задача после проверки состояния — не ещё один большой план, а конкретная реализация:
1. Выделить переиспользуемые драйверы и минимальный C99 API: video, input, monotonic time, read-only assets, memory, audio PCM, haptics, capabilities/diagnostics.
2. Собрать самостоятельный небольшой пример, не линкующий Doom: движение по кнопкам, update/render, свой ресурс. Одна воспроизводимая команда сборки, понятная точка для пользовательской логики. API не зависит от WAD и kenshi_doom_*.
3. Не выдавать нынешний Doom/WAD loader за универсальный. Изолировать его ABI совместимым адаптером и отдельно проверить путь к собственным ресурсам и engine pins. В NOR всего 188 свободных байт у V12 — новые драйверы/diagnostics преимущественно в RAM. Не обещать загрузку произвольного ELF без изменения текущего контракта.
4. Подготовить один RAM-диагностический пакет, проверять подсистемы последовательно: сырые кнопки; CPU/PLL/mux/div; ограниченный мотор; тихий тон; затем непрерывный PCM. Не менять несколько неизвестных аппаратных факторов за раз.
5. Добиться физических подтверждений звука и мотора, проверить длительную работу и передать SDK с примером. Doom затем использует те же общие сервисы, без переписывания его ядра.

Не забывай реальные неизвестные:
- GPT 26 MHz — не частота ARM. B621/PLL1401/DIV0 подтверждены stock-путём, но сами по себе не доказывают 260 MHz. Расшифруй полную ARM clock chain, укажи уровень доказательности/погрешность, при неопределённости выводи UNKNOWN. TCM ticks не равны MHz.
- Полную stock init PLL/SFI живьём не вызывать. Никаких слепых PLL/voltage retune. 100 ms — задержка, не +100 MHz.
- Doom PCM можно получить программно; регулярного аппаратного sink нет. Сначала короткий тихий тон и безопасный stop, потом PCM-поток без блокировки игры, потом звук примера и Doom SFX. Ненулевые samples не доказывают звук динамика.
- Reference AFE: `C:\Users\USER\Documents\Codex\2026-11-16\senior-embedded-c99-developer-reverse-engineer\work\reference\afe.c` и соседний `afe.h`. Это ориентир, не проверенный полный драйвер нашей платы. Не угадывай PCM FIFO/питание усилителя.
- VIB1/readback PMIC 0xA07001B0 не доказывает физический мотор. Во время stock-этапа пользователь проверяет звук/вибро с аккумулятором. Не повышай напряжение вслепую; импульс ограниченный с восстановлением и auto-off/cancel.
- UP/right неоднозначны; сырая матрица и подписи пользователя надёжнее догадок. Диагностические комбинации не должны срабатывать в игре.
- ED08 — поздний WAD I/O, причина не установлена. Частичный LCD V12 ещё физически не проверен. Сохранить безопасный полный fallback и корректное DMA ownership/cache.

Аппаратные ограничения обязательны:
NOR только [0xB000,0xF000), сектора 11–14; никакого full restore. Новый одноразовый writer на попытку; не rerun SPENT. В той же сессии геометрия/свежий полный read и независимый baseline gate перед записью, полный read/outer/PT_LOAD audit после. Stock меняет NV — нужен новый проверенный read-only baseline, не silent repin. Без автоматических retry/reset/FINISH/reconnect/clear-halt/rollback. Карту идентифицировать заново; диски ноутбука не трогать, форматирование не нужно. Замена только согласованного ELF с Flush/close/reopen/fullhash, WAD сохранять. Исторический overlay не физический baseline.

Пользователь разрешил эксперименты и устал от повторных общих разрешений. Не переспрашивай их, но фактическая готовность телефона сейчас неизвестна: перед аппаратной операцией нужна текущая готовность/короткое указание нужного физического действия. Пока её нет, выполняй офлайн-реализацию и проверки. Ничего не устанавливай вслепую. Не обещай фоновую работу, если она не запущена. Никаких новых чатов, задач по расписанию, worktree или делегирования без отдельного запроса.

Готовность показывай фактами: independent demo + public API + build command + hardware results + целевой непрерывный 15-минутный прогон. Модельный PASS ≠ hardware PASS. Если периферия не закрыта к сроку, передай пригодный для начала игры SDK и назови оставшиеся драйверы открытыми; «всё готово» не говори. Не трать срок на редактор, универсальный launcher чужих бинарников или 60 FPS Doom любой ценой. Простой launcher наших игр, телефонный UI, музыка и видео входят в новый целевой объём; проверить запуск/возврат и честно указать статус каждого.

Общайся коротко, по-русски, открыто и по делу. Начни с нескольких строк о фактическом состоянии и сразу переходи к исполнению. По итогам сообщай только реальный прогресс, доказательства и следующее необходимое действие пользователя.
