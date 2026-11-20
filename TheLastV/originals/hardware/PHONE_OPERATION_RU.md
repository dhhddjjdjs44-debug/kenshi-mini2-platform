## Стоковый плеер: ДИНАМИК телефона без наушников слышен — 2026-11-20T13:52:01.927837+05:00

На прямой вопрос «Трек в плеере слышен именно из динамика телефона, без наушников?»
пользователь ответил «Да, в плеере всё впорядке». USER_REPORTED,не инструментальный замер.
Положительный ориентир аудио: stock player -> phone speaker без наушников.
Snake audio остаётся NOT_AUDIBLE/причина неизвестна; наличие настроек не success.
Snake vib ранее USER_REPORTED_PRESENT; customHW0.2 vibFAIL,customPCM отсутствует.
Evidence:C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\stock_player_speaker_observation_20261120_135201\observation.json
Не считать stockspeaker success найденным PCM/routing/init драйвером.
0USB/NOR/SD операций; установлен STOCK. Старые writers SPENT,готовность не обновлена.

## ПОСЛЕДНЕЕ уточнение: змейка НЕ слышна; звук ориентир ПЛЕЕР — 2026-11-20T13:50:55.419514+05:00

Пользователь:«Очень странно, но звук в змейке не работает, хотя он должен был быть».
Предыдущее утверждение snakeaudio success отозвано; наличие меню Sound/Volume
НЕ доказательство слышимого звука. Причина неизвестна,не угадывать.
Player audio ранее слышен; Snake vib ранее ощущается — в этом сообщении не retest.
Evidence:C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\stock_snake_audio_correction_20261120_135055\observation.json
В качестве положительного аудиопримера использовать плеер,не змейку.
Speaker/headphones route пока не уточнён. CustomPCM отсутствует,customvibFAIL.
0USB/NOR/SDдействий; currentNORauthority по последнему чтению не менялась.

## Уточнение стока: змейка ЗВУК+ВИБРО; настройки on/off и громкость — 2026-11-20T13:45:00.062665+05:00

Последнее прямое сообщение пользователя: в играх найдены настройки; у змейки
есть звук И вибро, их можно выключать; там же регулируется громкость.
Это актуальная USER_REPORTED проверка, заменяет промежуточное «звука нет»
и «вибро неизвестно». Аудиоплеер также ранее слышен по отчёту пользователя.
Evidence:C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\stock_game_settings_observation_20261120_134500\observation.json
Мотор и аудиовывод работают в стоке по сообщению пользователя; speaker/headphones
route не указан. Наш HW0.2 мотор всё ещё FAIL_NO_FELT_VIBRATION, PCM не реализован.
Не считать стоковую работоспособность найденной init/route/PCM последовательностью;
не называть конкретный регистр неверным без дальнейшего доказательства.
0device operations сейчас, SD/NOR не менялись. Установлен STOCK; lastverified834bf…1fd85
не свежий baseline после работы стока. Старые writersSPENT,не запускать.

## Родной код ВОССТАНОВЛЕН — 2026-11-20T13:38:47.800897+05:00

Одна авторизованная bounded-stock проба успешно завершена verified_without_reset.
Fresh-before `117cac003a9327d9fb72eeda6a40fcf48204c95376d54c30d12b0896e693b9aa`. Hardware full readback `834bf1dc728d27d4b77242ea1b943fd0d0ba73fafe4376ab24a5194d4dd1fd85`.
Независимый аудит всех4194304 байт PASS; stock code [0,0x389000) совпал
с original9109aa. Только секторы11..14 изменены; весь outer/NV сохранён.
НЕ full restore. Ноль reset/FINISH/retry/reconnect/control transfers.
Текущий статус телефона: STOCK_CODE_RESTORED, ещё НЕ наблюдался холодный старт.
Разрешён ручной обычный старт с батареей, затем штатная змейка и проверка вибро/звука при проигрыше.
Диски ноутбука НЕ изменять. Карта на ПК ещё не идентифицирована, копирования нет.
Doom НЕ записан. Все старые writers и новый bounded-stock SPENT; не rerun.
После запуска stock ОС может изменить NV — послезаписная база не гарантируется дальше;
для следующей записи нужен новый согласованный fresh read/pin, не auto-repin.
Не обновлять SD в этой проверке.
Report: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_stock_for_vibration_20261120_133847\REPORT_RU.md`. Исторические записи ниже — не текущий статус.

## Временный возврат родной прошивки — ОДНА проба 2026-11-20T13:37:44.986391+05:00

Пользователь: «Да, в родной в змейке при проигрыше вроде бы, можем вернуть дамп и я проверю» после запроса
на проверку родного вибро в змейке. SD не обновляется.
Trial: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\stock_restore_for_vibration_20261120_133255`. Original writer release не изменён и остаётся SPENT.
Отдельная копия ограничена [0xB000,0xF000), только pins+image length.
85 unit PASS + dryrun PASS. Base `117cac003a9327d9fb72eeda6a40fcf48204c95376d54c30d12b0896e693b9aa`;
stock patch `32551e3af80f3b2fe2c7b9f280211c5e9694f29d4802f4b65604ca01326a47a2`; expected `834bf1dc728d27d4b77242ea1b943fd0d0ba73fafe4376ab24a5194d4dd1fd85`.
Stock code [0,0x389000) восстановится побайтово из original9109aa;
весь outer NOR и текущее NV сохраняются. FULL NOR restore ЗАПРЕЩЁН.
Перед записью live geometry+fresh4MiB в этой же сессии, после full4MiB+audit.
Никаких retry/reset/FINISH/reconnect/clear-halt/автоотката.
Разрешение израсходовано на этот один запуск, результат ещё НЕ получен.
Doom этим запуском НЕ записывается. Диски ноутбука/карта не изменяются.

## Stock Snake vibration cross-check prepared NOT launched — 2026-11-20T13:35:26.572305+05:00

Пользователь вспоминает:в стоковой змейке при проигрыше «вроде бы» вибрировало;
предлагает вернуть сток и проверить. Это НЕ новое подтверждение мотора.
NEW unconsumed trial: C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\stock_restore_for_vibration_20261120_133255. 85unit+dryrun PASS,0USB/NOR/card actions.
Base117cac…3b9aa -> expectedstock834bf…1fd85 (НЕ readback). Только[B000,F000).
Current pointer:work/current_stock_vibration_check.json; helpers:C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\stock_vibration_check_20261120_133255.
NEXT свежий ручной USB-off/battery-out/USB-in безкнопок и ответ пользователя.
USB0E8D:0003present сегодня сам по себе НЕ доказательство cold readiness.
Только после ответа записать authorization.fresh_hardware_readiness_report,
запустить НОВЫЙ launch_stock_vibration_once.py --user-authorized-platform-install
один раз; затем audit_stock_vibration.py. Standard coldBootROM->originalDA,
same-session geometry/full-before equality доD3/D5/full-after+outeraudit.
Никаких retry/reset/FINISH/fallback/auto-repin. Все старые writersSPENT.
SD/PLAT/KDATA/WAD не трогать; на стоке проверить змейку при проигрыше,
при наличии включить game sound/vibration; отдельно спросить фактические звук/вибро.
NOR HW0.2 пока остаётся установленной117cac…3b9aa,звук/вибро не объявлятьготовыми.

## HW0.2 runtime фото: NO VIB; CPU lowerbound7;20key contacts — 2026-11-20T13:28:11.226969+05:00

Observation: C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\hw02_runtime_observation_20261120_132811\observation.json
Key evidence: C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\hw02_runtime_observation_20261120_132811\captured_key_contacts.json
Пользователь «Вибро нет». MOTOR0C22/8C23/0C22 EN CLEARED — физический FAIL,
не успехhaptic. Наличие/стоковая работоспособность мотора неизвестны.
CPU MIN MHZ7 НЕ точная частота;B621/1401/0288,26MHZ NOT RULED.
Loop обычнаяRAM.text0x15480,неTCM. PLL/cache/вольтаж не менялись.
20unique rawcontacts;UP39,RIGHT30,softL33,softR72,CALL24;END-- не угадана.
Старая карта не исправлена,photo10overlap проигнорирована; ясные дубли есть.
PCM NO SINK/SPK0030: рабочий звук отсутствует. Profilegamezeros не0FPS.
Runtime diagnosticsUI observed; не весь launcher/Doom/медиа retest.
NOR authority117cac…3b9aa неизменна;0USB/SD/NOR operationsв этом отзыве.
Старые writersSPENT; свежего подтверждения готовности устройства нет.

## HW0.2 DOOM записана; полный NOR/PT_LOAD audit PASS — 2026-11-20T13:20:46.187289+05:00

Installed authority current_installed_firmware.json. Readback117cac003a9327d9fb72eeda6a40fcf48204c95376d54c30d12b0896e693b9aa.
Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\platform_hw02_cold_trial_20261120_131504 SPENT,НЕ rerun. Только[B000,F000),outer/NV сохранены.
No reset/FINISH/retry/reconnect. Ручной USB-off/battery-in/normal-coldboot разрешён.
Runtime ещё НЕ наблюдался; DIAGNOSTICS MOTOR50ms/CPU lowerbound/KEYS ожидаются.
Рабочего PCM нет,exactCPUHzunknown. Frozen pair и sealed parents не изменены.
Report: C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_hw02_written_20261120_132046\REPORT_RU.md. Исторические статусы ниже не текущая authority.

## ПлатформаHW0.2 doom: НОВАЯ холодная попытка — 2026-11-20T13:19:47.303384+05:00

User fresh manual USB cycle: «готов после read-only». Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\platform_hw02_cold_trial_20261120_131504.
Прошлые writers SPENT; не повторяются. Новая source-copy и87offline tests PASS.
ТОЛЬКО стандартная BootROM->DA initialization, БЕЗ --use-existing-da или fallback.
Reviewed baseline 834bf1dc728d27d4b77242ea1b943fd0d0ba73fafe4376ab24a5194d4dd1fd85; fresh same-session geometry/full4MiB
равенство ДО D3/D5. Только[B000,F000), после full4MiB + outer/NV/PT_LOAD audit.
Нет retry/reset/FINISH/reconnect/clear-halt/rollback/auto-repin.
Разрешение потреблено; результат pending. Платформа ещё НЕ объявлена установленной.

## HW0.2 fresh baseline reviewed; writer prepared NOT launched — 2026-11-20T13:15:58.364891+05:00

READ-ONLY capture hw02_post_card_readonly_20261120_131322 PASS:4MiB SHA
834bf1dc728d27d4b77242ea1b943fd0d0ba73fafe4376ab24a5194d4dd1fd85.
Независимо проверено:7028 изменённых байт только NV blocks943,947,948;
код[0,389000) совпадает сток/архив. Нет D3/D5/reset/FINISH/retry.
Installed pointer обновлён на reviewed STOCK baseline, НЕ HW0.2.
NEW one-use trial: C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\platform_hw02_cold_trial_20261120_131504. 87tests+dryrun+launcher offline gates PASS.
Pins: image4e8e3570…453c9; patche67bb990…c862b; expected117cac00…3b9aa (НЕ readback!).
Физический writer НЕ запускался; authorization не потреблена.
NEXT нужен ручной USB-off/USB-in БЕЗ батареи/кнопок ПОСЛЕ этого read-only capture.
Fresh_manual_USB_cycle_report сейчас WAITING_MANUAL_USB_CYCLE_AFTER_READONLY;
заменить только после нового пользовательского подтверждения готовности.
Launcher: C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\hw02_install_20261120_125942\launch_hw02_cold_once.py --execute-user-directed-once
Только cold BootROM->original DA, без --use-existing-da/fallback. Same-session
geometry/full-before equality передD3/D5; full-after+independent audit обязательно.
После запуска нужен НОВЫЙ independent hardware audit для frozen flat pair;
старый audit_platform_cold_written_v2.py содержит pins0.1/package layout49 и НЕ подходит.
Не менять frozen pair/подготовленный source/evidence; baseline-review указывает physical_capture,
а путь raw = physical_capture/full_capture.bin (не полеfull_verified_acquisition).
Состояние/карта/пути: current_hw02_trial.json, current_hw02_post_card_capture.json,
current_hw02_install.json, current_hw02_card_copy.json. Старые trials SPENT.

## HW0.2: SD обновлена, сток остаётся — 2026-11-20T13:11:25.173778+05:00

Свежая identity MINI_2 USB disk1/15635841024B FAT32 D: проверена перед/после.
Изменён ТОЛЬКО PLAT.ELF406496 SHA7b109db125e409c294301cc73a4af58155124846e0e06dc2ada5403d34df2695;
WriteThrough/Flush(true)/close/reopen full SHA PASS. Прежний PLAT сохранён на ПК.
DOOM.ELF/WAD/KDATA неизменны по полным SHA. Форматирования/host block операций нет.
Frozen deployment pair (не публичный release): C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\hw02_install_20261120_125942\frozen_doom_pair.
Согласованный новый loader13964 SHA4e8e3570214212e6bde55ea58af856711ccf263243b63c795ff5d661889453c9.
В NOR пока СТОК, last verified61b471…f0c96; stock boot мог изменить NV.
NEXT ручной USB-off/телефон-off/battery-out/USB-in без кнопок; новый read-only capture
через стандартный cold BootROM->DA и независимый review NV. Старую базу не auto-repin.
Затем НОВЫЙ cold one-use writer только[B000,F000), same-session geometry/full4MiB
before equality и full4MiB after/independent PT_LOAD+outer/NV audit. Старые trials SPENT.
Аудио пока отсутствует; CPU exact unknown, motor/key diagnostics physical unverified.
Card report: C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\hw02_install_20261120_125942\card-copy-result.json

## Родной код ВОССТАНОВЛЕН — 2026-11-20T13:01:17.296045+05:00

Одна авторизованная bounded-stock проба успешно завершена verified_without_reset.
Fresh-before `c536e743206fa8923a75c565afd758f43bd7a69ecb24949820e6c236c3e7acd8`. Hardware full readback `61b471300eaf712a12c63de4530516c0fbd097ea5afdfbc8bd0a70d5d19f0c96`.
Независимый аудит всех4194304 байт PASS; stock code [0,0x389000) совпал
с original9109aa. Только секторы11..14 изменены; весь outer/NV сохранён.
НЕ full restore. Ноль reset/FINISH/retry/reconnect/control transfers.
Текущий статус телефона: STOCK_CODE_RESTORED, ещё НЕ наблюдался холодный старт.
Разрешён ручной обычный старт с батареей, затем stock USB mass storage microSD.
Диски ноутбука НЕ изменять. Карта на ПК ещё не идентифицирована, копирования нет.
Doom НЕ записан. Все старые writers и новый bounded-stock SPENT; не rerun.
После запуска stock ОС может изменить NV — послезаписная база не гарантируется дальше;
для следующей записи нужен новый согласованный fresh read/pin, не auto-repin.
Report: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_stock_for_platform_20261120_130117\REPORT_RU.md`. Исторические записи ниже — не текущий статус.

## Временный возврат родной прошивки — ОДНА проба 2026-11-20T13:00:37.987649+05:00

Пользователь: «Заливай стоковый дамп тогда, закидываем на сд карту и накатываем новый; готов» после запроса
на установку новой платформы через временный stock и USB mass storage microSD.
Trial: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\stock_restore_for_platform_20261120_125942`. Original writer release не изменён и остаётся SPENT.
Отдельная копия ограничена [0xB000,0xF000), только pins+image length.
85 unit PASS + dryrun PASS. Base `c536e743206fa8923a75c565afd758f43bd7a69ecb24949820e6c236c3e7acd8`;
stock patch `32551e3af80f3b2fe2c7b9f280211c5e9694f29d4802f4b65604ca01326a47a2`; expected `61b471300eaf712a12c63de4530516c0fbd097ea5afdfbc8bd0a70d5d19f0c96`.
Stock code [0,0x389000) восстановится побайтово из original9109aa;
весь outer NOR и текущее NV сохраняются. FULL NOR restore ЗАПРЕЩЁН.
Перед записью live geometry+fresh4MiB в этой же сессии, после full4MiB+audit.
Никаких retry/reset/FINISH/reconnect/clear-halt/автоотката.
Разрешение израсходовано на этот один запуск, результат ещё НЕ получен.
Doom этим запуском НЕ записывается. Диски ноутбука/карта не изменяются.

## ПЛАТФОРМА0.1 DOOM ЗАПИСАНА; full NOR/PT_LOAD проверены — 2026-11-20T11:49:08.058946+05:00

Текущая installed authority: C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\current_installed_firmware.json.
NOR SHA256 c536e743206fa8923a75c565afd758f43bd7a69ecb24949820e6c236c3e7acd8. New trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\platform_doom_cold_trial_20261120_114510 SPENT; НЕ rerun/auto-repin.
Только[B000,F000), fresh same-session geometry+full4MiB before; full4MiB after
побайтовый overlay/outer/NV/bootloader/ELF PT_LOAD audit PASS.
Стандартная BootROM->DA initialization выполнена в этой же успешной writer-сессии;
87offline tests PASS; --use-existing-da НЕ использовался; нет reset/FINISH/retry/reconnect/clear-halt.
Карта PLAT.ELF400660 SHA9dbfc426aaf21023dfc48ca8ace87defae3271f1b80ee5bad657a6e164af9f10
и KDATA.PAK833596 SHA38cf2146af721cc2fc1554e7cc24a7b90de4a1df252a34f0f76130c471b33caa
full Flush/reopen hash PASS; старый DOOM.ELF/WAD сохранены.
COLD BOOT ЕЩЁ НЕ НАБЛЮДАЛСЯ. Разрешён ручной USB-off/battery-in/power-on.
Ожидается KENSHI PLATFORM; первым YOUR GAME, возврат, PHONE, VIDEO; Doom отдельно.
MUSIC NO AUDIO DRIVER/VIDEO SILENT ожидаемо; физические звук/мотор/CPU MHz/исходныйIMEI не закрыты.
Sealed SDK/V11/V12/package не изменены. Report C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_platform_written_20261120_114908\REPORT_RU.md.

## Платформа0.1 doom: НОВАЯ холодная попытка — 2026-11-20T11:47:21.905957+05:00

User fresh manual USB cycle: «Странно. Ну я сделал». Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\platform_doom_cold_trial_20261120_114510.
Предыдущий geometry STOP SPENT; не повторяется. Новая source-copy и87offline tests PASS.
ТОЛЬКО стандартная BootROM->DA initialization, БЕЗ --use-existing-da или fallback.
Reviewed baseline 61b471300eaf712a12c63de4530516c0fbd097ea5afdfbc8bd0a70d5d19f0c96; fresh same-session geometry/full4MiB
равенство ДО D3/D5. Только[B000,F000), после full4MiB + outer/NV/PT_LOAD audit.
Нет retry/reset/FINISH/reconnect/clear-halt/rollback/auto-repin.
Разрешение потреблено; результат pending. Платформа ещё НЕ объявлена установленной.

## Platform writer STOPPED до стирания; требуется новый ручной USB заход — 2026-11-20T11:42:40.767282+05:00

New platform trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\platform_doom_trial_20261120_113806 SPENT. Первая B0 geometry дала
unexpected reply b101010101 вместо000000005a. Отправлено5байт, принято5;
D3/D5 НЕ отправлялись, full NOR в этой неудачной попытке НЕ читался.
Не было reset/FINISH/retry/reconnect/clear-halt/rollback; причина ответа НЕ доказана.
Новая платформа НЕ записана. Последний verified stock NOR61b471300eaf712a12c63de4530516c0fbd097ea5afdfbc8bd0a70d5d19f0c96.
Карта PLAT.ELF/KDATA.PAK ранее fullhash verified, старый WAD/DOOM.ELF сохранены.
NEXT: пользователь вручную отключает/подключает USB без аккумулятора.
Только НОВАЯ one-use trial со штатной BootROM->DA initialization, не --use-existing-da;
перед D3/D5 live geometry+full4MiB equality с reviewed baseline. Не авто-fallback.
Audit C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\platform_doom_trial_20261120_113806\independent-stopped-audit.json.

## Платформа0.1 doom: ОДНА попытка записи начинается — 2026-11-20T11:41:41.877021+05:00

New trial: C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\platform_doom_trial_20261120_113806. Карта PLAT.ELF/KDATA.PAK full reopen/hash verified.
Post-stock baseline независимо проверен: 61b471300eaf712a12c63de4530516c0fbd097ea5afdfbc8bd0a70d5d19f0c96; изменилось только NV.
Используется штатный --use-existing-da: DA ТОЛЬКО ЧТО успешно инициализирована
и выполнила full read-only capture без reset/FINISH; это не угадывание по VID.
ПЕРЕД D3/D5 в новом writer снова live B0 geometry + full4MiB equality gate.
Только[B000,F000),87offline tests incl live-DA success/mismatched-base refusal PASS.
После полный4MiB readback + независимый PT_LOAD/outer/NV audit.
Никакого init fallback/retry/reset/FINISH/reconnect/clear-halt/rollback/auto-repin.
Разрешение потреблено; результат pending. Платформа ЕЩЁ НЕ объявлена установленной.

## Карта новой платформы проверена; stock остаётся — 2026-11-20T11:33:37.9868410+05:00

User: «Всё, делай». Fresh OS inventory: USB MINI_2 disk1, 15635841024B,
FAT32 partition offset4194304/size15631646720, nonboot/nonsystem; observed D: (НЕ предполагать в будущем).
Только PLAT.ELF400660 SHA9dbfc426aaf21023dfc48ca8ace87defae3271f1b80ee5bad657a6e164af9f10
и KDATA.PAK833596 SHA38cf2146af721cc2fc1554e7cc24a7b90de4a1df252a34f0f76130c471b33caa
созданы через CreateNew/WriteThrough/Flush(true), закрыты и fullhash reopened PASS.
Сохранены DOOM.ELF/WAD, их SHA прежние. Без форматирования/host-block операций.
Отчёт: C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\platform_install_20261120_112607\card-copy-result.json. Copy claim SPENT; НЕ rerun.
Сейчас stock bbb880...67d7 по последней NOR-проверке; stockboot мог изменить NV.
Новая платформа ЕЩЁ НЕ записана. Ждём ручной USB-off, poweroff, battery-out, USB-on.
Новый read-only capture helper подготовлен, НЕ запущен; затем независимый review
нового baseline и НОВЫЙ one-use paired doom-platform loader writer, только[B000,F000).

## Родной код ВОССТАНОВЛЕН — 2026-11-20T11:29:16.296073+05:00

Одна авторизованная bounded-stock проба успешно завершена verified_without_reset.
Fresh-before `8b618813d04f86b86cf5daa4ab06703d5344737dd383787d555e5e2dda983c09`. Hardware full readback `bbb880755be74317e74f45c2234b062906a0bca68bc02e6d61c7ff35586e67d7`.
Независимый аудит всех4194304 байт PASS; stock code [0,0x389000) совпал
с original9109aa. Только секторы11..14 изменены; весь outer/NV сохранён.
НЕ full restore. Ноль reset/FINISH/retry/reconnect/control transfers.
Текущий статус телефона: STOCK_CODE_RESTORED, ещё НЕ наблюдался холодный старт.
Разрешён ручной обычный старт с батареей, затем stock USB mass storage microSD.
Диски ноутбука НЕ изменять. Карта на ПК ещё не идентифицирована, копирования нет.
Doom НЕ записан. Все старые writers и новый bounded-stock SPENT; не rerun.
После запуска stock ОС может изменить NV — послезаписная база не гарантируется дальше;
для следующей записи нужен новый согласованный fresh read/pin, не auto-repin.
Report: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_stock_for_platform_20261120_112916\REPORT_RU.md`. Исторические записи ниже — не текущий статус.

## Временный возврат родной прошивки — ОДНА проба 2026-11-20T11:28:50.115631+05:00

Пользователь: «Накатывай чумба» после запроса
на установку новой платформы через временный stock и USB mass storage microSD.
Trial: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\stock_restore_for_platform_20261120_112608`. Original writer release не изменён и остаётся SPENT.
Отдельная копия ограничена [0xB000,0xF000), только pins+image length.
85 unit PASS + dryrun PASS. Base `8b618813d04f86b86cf5daa4ab06703d5344737dd383787d555e5e2dda983c09`;
stock patch `32551e3af80f3b2fe2c7b9f280211c5e9694f29d4802f4b65604ca01326a47a2`; expected `bbb880755be74317e74f45c2234b062906a0bca68bc02e6d61c7ff35586e67d7`.
Stock code [0,0x389000) восстановится побайтово из original9109aa;
весь outer NOR и текущее NV сохраняются. FULL NOR restore ЗАПРЕЩЁН.
Перед записью live geometry+fresh4MiB в этой же сессии, после full4MiB+audit.
Никаких retry/reset/FINISH/reconnect/clear-halt/автоотката.
Разрешение израсходовано на этот один запуск, результат ещё НЕ получен.
Doom этим запуском НЕ записывается. Диски ноутбука/карта не изменяются.

## V12 SEALED OFFLINE; ORIGINAL CPU + LATE CACHE + 100MS; PARTIAL LCD — 2026-11-19T20:29:06.037816+05:00

NEW immutable candidate C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_v12_20261119_200415; manifest224 files SHA cf9c8c6f4643c199193cc922d8da90305ed05b94a7d2458febfdb889e50f5eb2.
Engine385648 SHA 5d8d3dce8ecdc4ae4a79d0a91e73ec077535fdc5647418180cbb774a831be889; loader16196 SHA 4590e1f86cea832559197f3b4f4b2e666d26659345157aa8b64831dfa9ac850a.
V12 NOT flashed/card-copied; no USB/card/NOR operations, no new physical writer.
Installed authority still V11 8b618813d04f86b86cf5daa4ab06703d5344737dd383787d555e5e2dda983c09.
V11/V10 seals verified unchanged. DO NOT rebuild/test in sealedV12: use a NEW clone.
Default originalB621, cache only AFTER init + first completed idle LCD frame + ONCE100ms guard.
Hold5 atENGINE skips auto cache; 5+9 manualcache; 5+3 fullLCD fallback B/F; avoid5+# initially.
Packed scaler bitexact10240pixels,5120stores; normal DMA rows40..119/20480B, HUD full5Hz.
Target60 presentation, sim35Hz, NO interpolation/FPS promise. IMPORTANT correction:
V11 PureDOOM actually had singletics=true (one tic/render), so TryRunTics was NOT its live limiter.
V12 setsfalse and nonblocking zero-due-tic path; actualARM35/60 calls give identical35tics/movement.
Diagnostic5/0 commit onrelease, 80ms pulse; chords consumed, physicalUP mapping still unresolved.
19 ARM processes +11 packaging PASS;21 reports; normal/safe64frames,125textures; rebuildbitexact.
Independent PT_LOAD/pins/audit PASS; loaderLCD allocsections identicalV11; NOR free188B;
BSS engine0x3e3048/slack118712; loaderEBA0; modeled minstack70009648, reserve70009000.
SoftwarePCM only; A--, no speaker sink. Vibration physical unconfirmed. LateED08 cause unknown.
NEXT user poweroff/removebattery/USB readiness, temporary bounded stock, fresh identified microSD
DOOM.ELF copy/reopen/fullhash, then NEW reviewed poststock baseline + NEW one-useV12 writer.
ONLY[B000,F000), same-session geometry/fullbefore gate and fullafter/outer/PT_LOAD audit.
No full restore, SPENT rerun, automatic repin/retry/reset/FINISH/reconnect/clearhalt; no host disk edits.
Reference overlay NOT a physical write authority. No card format required; preserve WAD.
Report C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_doom_v12_offline_20261119_202906\REPORT_RU.md; candidate pointer C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\current_v12_candidate.json.

## V11 FIRST LEVEL COMPLETED; STOCK CLOCK EXTRACTION CONFIRMS B621 — 2026-11-19T19:53:36.004357+05:00

User completed firstlevel; occasional drops. Photo C:\Users\USER\AppData\Local\Temp\codex-clipboard-ba74fa8b-0f1f-406d-95bc-eb3e42657ff4.png:~34.4FPS intermission,
CC1/cache028F,CPU5/MCUB621,PLL1401,VIB0,A--. Gameplay works with originalCPU+cache.
US0x8D8=2.264ms,CP0x3AE=0.942ms,LCD0x5474=21.620ms (INTERMISSION, not game mean).
Prior ED08 historical cause still unresolved; do not claim all-level stability.
Exact archival stock Thumb0x10001D71 replayed6cases: profiles2/5 intentionallyB621/1401/div0.
Full routine resets/sharedPLL and changesSFI; NO live reuse/retune implemented.
NEW private read-only100ms ARM guard16casesPASS incl stoppedtimer/wrap/changedregs;
not integrated/flashed, zeroMMIO writes.100ms interpreted as delay, NOT+100MHz.
No new game build/USB/card/NOR operation. V11/V10 seals verified unchanged.
Performance next:29ms gate AND minimum-tic wait; preserve35Hz sim. FullLCD~21.62ms
precludes60full transfers/s without partial updates/other validated display changes.
Report C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_stock_clock_research_20261119_195336\REPORT_RU.md; private evidence C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\stock_clock_extract_20261119_194852.

## V11 PHOTO: ED08 LATE WAD IO; CACHE OFF, CPU B620; CONTROLS QUESTIONED — 2026-11-19T19:37:13.837766+05:00

Photo C:\Users\USER\AppData\Local\Temp\codex-clipboard-e28e9db7-fa9b-4b06-b6be-afc10ace9fdf.png. ED08 is emitted by engine_trace_io_error AFTER frames>0.
HUD CC0/cache0288,CPU1/MCUB620,VIB1,PLL1401. CPU chord DID selectB620; no measuredMHz.
US0x143A0=82.848ms,CP0x3EB6=16.054ms,LCD0x55CD=21.965ms; FPS~10.7 latched, not proof of continuing frames.
Earlier31FPS cache report is NOT stable-play proof. Cause of late IO unknown; no blind SD retries.
Some controls intentionally use aliases; UP/right historical ambiguity remains. Current diagnostic
chords also leak5=SPACE/0=TAB into Doom. Need consume chords, not guess physical remap.
User now prioritizes performance toward60FPS but normal boot+IO stability also need repair.
No new firmware built, no card/USB/NOR writes; V11 sealed parent immutable, writer SPENT.
Detailed observation and next-iteration PLAN ONLY: C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\v11_late_io_key_report_20261119_193713.

## V11 USER REPORT: 31FPS AFTER RUNTIME CACHE CHORD — 2026-11-19T19:28:49.483215+05:00

User: «нажал5+9 фпс вырос до31». TEXT REPORT, no new photo/video timing.
Source5+9 toggles cache only; earlier safe photo CC5/CPU5/B621/cache0288.
Current CPU state unknown: user has NOT confirmed whether5+# was pressed earlier.
Do not attribute all gain exclusively to cache or claim260MHz without HUD/evidence.
Strong evidence runtime cache helps; startup failure cause/order/coherency NOT established.
NEXT keep current state, photograph full HUD CC/CPU/MCU/cache/US/CP/LCD and check
movement/turn/fire briefly. No need for new flash. Avoid simultaneous changes.
No USB/card/NOR operations; immutable V11 candidate and SPENT writer unchanged.
Observation C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\v11_runtime_cache_report_20261119_192849\runtime-observation.json.

## V11 SAFE ENGINE BOOT WORKS: USER5FPS DROPS3 — 2026-11-19T19:24:25.693088+05:00

Photo C:\Users\USER\AppData\Local\Temp\codex-clipboard-6d7eaf59-db4e-431f-b915-b3d9be5a3a4d.png; visible gameplay, HUD approx5.3FPS (separator blurred).
CC5/CPU5/MCUB621/cache0288 confirm numeric5 safe path: both experiments skipped.
T0=0x9C8C,T1=0x9C89 essentially equal GPT ticks, not MHz.
US0x22F38=143.160ms;CP0x3EB6=16.054ms;LCD0x55C9=21.961ms.
Fields not exact same-frame sum. Engine work still largest displayed interval.
Normal pre-init CPU+cache path failed before firstframe; exact culprit NOT isolated.
NEXT same-scene runtime CPU-only test5+# ONCE, release: expectCPU1/MCUB620,cache remains0288.
Do not enable cache5+9 simultaneously; T0/T1 not refreshed by runtime chords.
No new firmware/card/USB writes. Sealed V11 immutable, writer SPENT.
Audio sink absent;VIB0 means no probe yet. Physical controls this boot not reconfirmed.
Observation C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\v11_safe_gameplay_20261119_192425\runtime-observation.json.

## V11 PHOTO: ENGINE RETURN, ZERO FRAMES; GAME NOT RUNNING — 2026-11-19T19:18:49.498134+05:00

Photo C:\Users\USER\AppData\Local\Temp\codex-clipboard-2864818e-fe6f-4103-b11b-d12af0fb9c4a.png. FRM00000000,FATL00000000,CODE00000000,LCD00003700,FLAG1,LBA004044C0,STA8018.
RAM engine returned; no gameplay frame shown. Successful flash audit is NOT runtime success.
Early source/first-WAD-header/directory checks can return0 without error code; exact cause unknown.
CPU/cache changes precede those gates. NEXT manual cold boot holding numeric5 through ENGINE
entry skips BOTH experiments; safe vs normal outcome required before assigning cause.
No new build/card/USB/NOR writes. V11 sealed338file candidate untouched; writer SPENT.
Installed NOR hash8b618813d04f86b86cf5daa4ab06703d5344737dd383787d555e5e2dda983c09 unchanged.
Observation C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\v11_engine_return_20261119_191849\runtime-observation.json. Historical runtime-not-observed statements superseded.

## V11 PHYSICALLY WRITTEN; NEW CARD ENGINE VERIFIED — 2026-11-19T19:12:30.689424+05:00

User-directed sequence stock -> new DOOM.ELF -> V11 completed in this chat.
New card383928 SHA 5a2df8ed013985d44ad0edf54dc23b4f79d323a7bb56b07175f0aa5f425a87c6, Flush/reopen/full hash PASS;
WAD unchanged, freshly identified MINI_2 card, no formatting or laptop block changes.
Stock code restored then post-boot NV independently acquired/reviewed before NEW writer.
V11 full fresh same-session before bbb880755be74317e74f45c2234b062906a0bca68bc02e6d61c7ff35586e67d7; actual after 8b618813d04f86b86cf5daa4ab06703d5344737dd383787d555e5e2dda983c09.
All4194304 bytes exact overlay; independent ELF PT_LOAD PASS. Only[B000,F000),
blocks11..14; all outer/NV preserved. Original standard DA/protocol unchanged.
OneD5/fourACK, USBerrors0/control0, no retry/reset/FINISH/reconnect/clearhalt/rollback/staging.
Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_performance_v11_trial_20261119_191036 SPENT; physical-attempt.claimed.json and authorization-consumption.json authoritative.
Do NOT rerun or repin. Candidate338file seal unchanged;V11 offline verification +86 writer tests.
Manual USB disconnect + battery/card + normal cold boot WITHOUT STAR now allowed.
V11 hardware boot/control/FPS/startup improvement NOT YET OBSERVED; audio NOT implemented.
Return page ENGINE RETURN V11 shows CODE/FATL/FRM/LCD/FLAG; photograph if it appears.
Report C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_doom_performance_v11_written_20261119_191230\REPORT_RU.md. Historical statuses below do not override this result.

## V11 ONE ATTEMPT STARTING — 2026-11-19T19:12:02.426364+05:00

User authorized stock -> card -> V11 sequence. New card engine full reopen/hash PASS.
Fresh post-card stock capture independently reviewed: only NV changed after stock boot.
NEW writer C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_performance_v11_trial_20261119_191036; base bbb880755be74317e74f45c2234b062906a0bca68bc02e6d61c7ff35586e67d7; expected 8b618813d04f86b86cf5daa4ab06703d5344737dd383787d555e5e2dda983c09.
Sealed candidate338 files/252 groups,86 writer tests PASS. Original standard protocol.
Only[B000,F000); live same-session full before equality gate BEFORE D3/D5; full after+ELF.
No staging pauses/retry/reset/FINISH/reconnect/clearhalt/rollback/auto-repin.
Old writers remain SPENT; this single authorization is now consumed. Result PENDING.
V11 NOT declared installed. Card files and laptop block devices not touched by writer.

## V11 CARD VERIFIED; FRESH BASE REVIEWED; WRITER PREPARED, NOT LAUNCHED — 2026-11-19 19:11 +05:00

Card engine383928 SHA5a2df8ed013985d44ad0edf54dc23b4f79d323a7bb56b07175f0aa5f425a87c6 verified Flush/reopen; WAD unchanged.
Fresh post-stock full capture bbb880755be74317e74f45c2234b062906a0bca68bc02e6d61c7ff35586e67d7 reviewed independently:6512 changed bytes only NV blocks939,941,943; original code exact.
NEW trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_performance_v11_trial_20261119_191036,86 writer tests and offline dryrun PASS. V11 NOT written.
Read-only session ended without reset/FINISH. NEED manual USB disconnect/reconnect without battery to re-enter BootROM before launch.
Launch once: work/launch_doom_v11_once.py --user-authorized. Then work/audit_doom_v11_written.py.
Only[B000,F000), same-session full before gate and full after; no retry/reset/reconnect/auto-repin. Old writers SPENT.

## Родной код ВОССТАНОВЛЕН — 2026-11-19T19:05:36.200689+05:00

Одна авторизованная bounded-stock проба успешно завершена verified_without_reset.
Fresh-before `118033f1995690c992cee2eab0cb9964053bf261c9b445263fe000033adc12b8`. Hardware full readback `c1857309b34e0881916f7a43e4bc7bf1da264953c550c1abb9f60cd3117b2098`.
Независимый аудит всех4194304 байт PASS; stock code [0,0x389000) совпал
с original9109aa. Только секторы11..14 изменены; весь outer/NV сохранён.
НЕ full restore. Ноль reset/FINISH/retry/reconnect/control transfers.
Текущий статус телефона: STOCK_CODE_RESTORED, ещё НЕ наблюдался холодный старт.
Разрешён ручной обычный старт с батареей, затем stock USB mass storage microSD.
Диски ноутбука НЕ изменять. Карта на ПК ещё не идентифицирована, копирования нет.
Doom НЕ записан. Все старые writers и новый bounded-stock SPENT; не rerun.
После запуска stock ОС может изменить NV — послезаписная база не гарантируется дальше;
для следующей записи нужен новый согласованный fresh read/pin, не auto-repin.
Report: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_stock_restored_20261119_190536\REPORT_RU.md`. Исторические записи ниже — не текущий статус.

## Временный возврат родной прошивки — ОДНА проба 2026-11-19T19:05:09.283223+05:00

Пользователь: «накатывай сток» после запроса
на один временный возврат stock ради USB mass storage microSD.
Trial: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\stock_restore_for_v11_20261119_190236`. Original writer release не изменён и остаётся SPENT.
Отдельная копия ограничена [0xB000,0xF000), только pins+image length.
85 unit PASS + dryrun PASS. Base `118033f1995690c992cee2eab0cb9964053bf261c9b445263fe000033adc12b8`;
stock patch `32551e3af80f3b2fe2c7b9f280211c5e9694f29d4802f4b65604ca01326a47a2`; expected `c1857309b34e0881916f7a43e4bc7bf1da264953c550c1abb9f60cd3117b2098`.
Stock code [0,0x389000) восстановится побайтово из original9109aa;
весь outer NOR и текущее NV сохраняются. FULL NOR restore ЗАПРЕЩЁН.
Перед записью live geometry+fresh4MiB в этой же сессии, после full4MiB+audit.
Никаких retry/reset/FINISH/reconnect/clear-halt/автоотката.
Разрешение израсходовано на этот один запуск, результат ещё НЕ получен.
Doom этим запуском НЕ записывается. Диски ноутбука/карта не изменяются.

## V11 SEALED OFFLINE PERFORMANCE CANDIDATE; V10 STILL INSTALLED — 2026-11-19T18:01:18.190838+05:00

Current V11 candidate C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_v11_20261119_170318; manifest 338 files SHA 3f1e3cdeb6e3cd27e54482e4e92ada751a809d3661f0aec45b833d06a10a1be0.
No V11 USB/card/NOR operations. Working installed V10 118033f1995690c992cee2eab0cb9964053bf261c9b445263fe000033adc12b8 unchanged;
all279 sealed V10 files independently verified. Old physical writers remain SPENT.
V11 engine 383928 SHA 5a2df8ed013985d44ad0edf54dc23b4f79d323a7bb56b07175f0aa5f425a87c6; paired loader 16196 SHA 284c219aa5aa51011f3a8c9eb31b23d47a54eb78b265662ef023a37021819322.
NEW card engine copy/reopen/hash REQUIRED before paired loader. KEEP WAD; no format.
V11: -O2 engine,160x84 scene/320x200 UI, direct indexed framebuffer, fast RAM copies,
5Hz HUD.17 ARM processes+11 packaging PASS; normal/safe64frames each;125 texture reference.
Actual steady-game ARM instruction reduction 59.2%, same tics/trajectory;
transition wipe excluded. NOT phone FPS/cache timing. Hardware V11 untested.
CPU B621->B620 only with inheritedMPLL1401/DIV0; NO PLL reset/retune/EMI/SFI/core voltage.
260MHz NOT measured. T0/T1 are100000-iteration TCM GPT ticks, NOT MHz.
Cache only engine RAM, excludes loader/DMA/framebuffer/aliases/MMIO/TCM; exact restore.
Safe ENGINE boot hold5;5+9 cache toggle;5+# CPU original/nominal fast;5+0 bounded50ms VIB.
Hardware coherency and motor effect NOT verified. Software PCM PASS; SPEAKER SINK ABSENT(A--).
Future physical chain: bounded stock sectors -> new card file -> fresh reviewed stock base
-> NEW one-use V11 writer. Only[B000,F000); same-session full before gate BEFORE D3/D5,
full after+independent every-byte/protected outer+ELF. No retry/reset/FINISH/reconnect/
clearhalt/rollback/auto-repin/staging or laptop disk/phone internal-volume operations.
Private overlay is OFFLINE reference over historical V10, NOT post-stock authorization.
Sealed V11 is IMMUTABLE: verify only; use NEW clone for builds/tests/edits.
Report C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_doom_v11_offline_20261119_180118\REPORT_RU.md. Historical headers below do not override this state.

## V10 HUD PHOTO: CPU PATH DOMINATES, ~2.4 FPS — 2026-11-19T16:45:23.950808+05:00

Photo C:\Users\USER\AppData\Local\Temp\codex-clipboard-c892c3fc-80ba-432e-88cd-55c3e63c0dac.png. US0x455BF=284.095ms,CP0x17284=94.852ms,LCD0x620A=25.098ms.
UP/FR0x11E; MCU B621,PLL1401,cache0288. CPU MHz not proven; B621 differs B620 classifier.
US includes simulation/render; CP includes redundant64000-byte doom_get_framebuffer(1) copy + palette/scaler.
Runtime memcpy volatile byte loop. HUD time outside US/CP; LCD poll previous transfer, timings not exact same-frame sum.
Prioritize eliminating unnecessary framebuffer copy/byte-loop cost, speed build tests, then native low-res render; cache requires coherent DMA/alias policy.
No new firmware edits/physical operations, sealed V10 untouched. Observation C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\v10_hud_photo\hud-observation.json.

## V10 GAMEPLAY WORKS PER USER; 2 FPS REPORTED — 2026-11-19T16:42:53.875837+05:00

User: game and controls work, 2 FPS. No new photo/video or independent timing yet.
V10 installed NOR118033f1995690c992cee2eab0cb9964053bf261c9b445263fe000033adc12b8 unchanged.
Source confirms cache disabled, engine -Os,320x200 internal render scaled128x80. These are candidates, not established bottleneck causes.
Requested HUD US/CP/LCD + raw MCU/PLL/cache to distinguish engine/conversion/display. Values except FPS HEX.
No new build/flash/clock/cache/voltage changes. Sealed V10 and spent writers untouched.
Observation C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_v10_runtime_observation_20261119_164253\runtime-observation.json.

## V10 PHYSICALLY WRITTEN; NEW CARD ENGINE VERIFIED — 2026-11-19T16:38:44.640152+05:00

User-directed sequence stock -> new DOOM.ELF -> V10 completed in this chat.
New card321952 SHA d76a9a8d8af53f0ef98912ffb88772850192237e6ccb040a03758d057dc8f0df, Flush/reopen/full hash PASS;
WAD unchanged, freshly identified MINI_2 card, no formatting or laptop block changes.
Stock code restored then post-boot NV independently acquired/reviewed before NEW writer.
V10 full fresh same-session before c1857309b34e0881916f7a43e4bc7bf1da264953c550c1abb9f60cd3117b2098; actual after 118033f1995690c992cee2eab0cb9964053bf261c9b445263fe000033adc12b8.
All4194304 bytes exact overlay; independent ELF PT_LOAD PASS. Only[B000,F000),
blocks11..14; all outer/NV preserved. Original standard DA/protocol unchanged.
OneD5/fourACK, USBerrors0/control0, no retry/reset/FINISH/reconnect/clearhalt/rollback/staging.
Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_loop_v10_trial_20261119_163801 SPENT; physical-attempt.claimed.json and authorization-consumption.json authoritative.
Do NOT rerun or repin. Candidate279file seal unchanged;252 model groups +86 writer tests.
Manual USB disconnect + battery/card + normal cold boot WITHOUT STAR now allowed.
V10 hardware boot/control/FPS/startup improvement NOT YET OBSERVED; audio NOT implemented.
Return page ENGINE RETURN V10 shows CODE/FATL/FRM/LCD/FLAG; photograph if it appears.
Report C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_doom_loop_v10_written_20261119_163844\REPORT_RU.md. Historical statuses below do not override this result.

## V10 ONE ATTEMPT STARTING — 2026-11-19T16:38:23.568222+05:00

User authorized stock -> card -> V10 sequence. New card engine full reopen/hash PASS.
Fresh post-card stock capture independently reviewed: only NV changed after stock boot.
NEW writer C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_loop_v10_trial_20261119_163801; base c1857309b34e0881916f7a43e4bc7bf1da264953c550c1abb9f60cd3117b2098; expected 118033f1995690c992cee2eab0cb9964053bf261c9b445263fe000033adc12b8.
Sealed candidate279 files/252 groups,86 writer tests PASS. Original standard protocol.
Only[B000,F000); live same-session full before equality gate BEFORE D3/D5; full after+ELF.
No staging pauses/retry/reset/FINISH/reconnect/clearhalt/rollback/auto-repin.
Old writers remain SPENT; this single authorization is now consumed. Result PENDING.
V10 NOT declared installed. Card files and laptop block devices not touched by writer.

## V10 WRITE ATTEMPT STOPPED BEFORE OPEN; STOCK REMAINS — 2026-11-19T16:36:28.834182+05:00

Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_loop_v10_trial_20261119_163449 SPENT, physical result C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_loop_v10_trial_20261119_163449\sessions\attempt_20261119_163558_137322\result.json.
No device found at open, no DA init/NOR commands; V10 NOT written. No automatic retry/reset/reconnect.
Card V10 engine still verified. Reviewed post-card stock base c1857309b34e0881916f7a43e4bc7bf1da264953c550c1abb9f60cd3117b2098 remains last acquisition.
Need new user-directed attempt in NEW trial, never rerun/repin spent source.
Next request disconnect first, prepare detection before manual connection to reduce transient-enumeration timing issue.

## V10 ONE ATTEMPT STARTING — 2026-11-19T16:35:57.995316+05:00

User authorized stock -> card -> V10 sequence. New card engine full reopen/hash PASS.
Fresh post-card stock capture independently reviewed: only NV changed after stock boot.
NEW writer C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_loop_v10_trial_20261119_163449; base c1857309b34e0881916f7a43e4bc7bf1da264953c550c1abb9f60cd3117b2098; expected 118033f1995690c992cee2eab0cb9964053bf261c9b445263fe000033adc12b8.
Sealed candidate279 files/252 groups,86 writer tests PASS. Original standard protocol.
Only[B000,F000); live same-session full before equality gate BEFORE D3/D5; full after+ELF.
No staging pauses/retry/reset/FINISH/reconnect/clearhalt/rollback/auto-repin.
Old writers remain SPENT; this single authorization is now consumed. Result PENDING.
V10 NOT declared installed. Card files and laptop block devices not touched by writer.

## POST-CARD V10 CAPTURE STOPPED; USB DISCOVERY UNSTABLE — 2026-11-19T16:32:41.806898+05:00

User manually reconnected. Read-only discovery returned0,then1 MTK, but separate capture open found0.
Capture C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\post_card_v10_readonly_20261119_163224 STOPPED before open; no acquisition/DA/NOR commands. No retry/reset or automatic reconnect.
V10 card verified; stock remains installed. Fresh stock NV baseline unknown. Next needs manual connection check; do not flash from old baseline.

## V10 POST-CARD READ-ONLY CAPTURE STOPPED DEVICE ABSENT — 2026-11-19T16:31:25.460494+05:00

Capture C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\post_card_v10_readonly_20261119_163113 found zero 0E8D:0003 before open; no NOR write, no capture obtained.
No retry/reset/reconnect performed. Card V10 engine remains verified; last physically written loader is STOCK.
Current post-stock-boot NOR baseline unknown; NEW read-only acquisition required after manual reconnect.
Do NOT reuse spent attempts, do NOT pin old pre-boot stock dump. V10 loader NOT flashed.

## V10 CARD ENGINE VERIFIED; STOCK STILL INSTALLED — 2026-11-19T16:30:18.520835+05:00

Card freshly identified USB MINI_2 15635841024 FAT32. One DOOM.ELF replaced,321952 bytes
SHA d76a9a8d8af53f0ef98912ffb88772850192237e6ccb040a03758d057dc8f0df; Flush/reopen hash PASS.
WAD unchanged. No format/internal volume/block writes. Evidence C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\card_v10_copy_20261119_162959\copy-result.json.
V10 loader NOT written. Stock code still installed; OS boot means previous full NOR baseline may have changed NV.
Next manual USB disconnect,power off,remove battery,reconnect; new read-only capture and independent NV review required before NEW writer.
No prior SPENT writer may be rerun.

## Родной код ВОССТАНОВЛЕН — 2026-11-19T16:28:43.438026+05:00

Одна авторизованная bounded-stock проба успешно завершена verified_without_reset.
Fresh-before `b8e32e2d98d645490dc9f657192efd3218c7711976dccb48b09430472ba1d4d3`. Hardware full readback `b20f25fdfe14cb8024c39df0c9444ecc41d3402e813d558e82120b0e65104db7`.
Независимый аудит всех4194304 байт PASS; stock code [0,0x389000) совпал
с original9109aa. Только секторы11..14 изменены; весь outer/NV сохранён.
НЕ full restore. Ноль reset/FINISH/retry/reconnect/control transfers.
Текущий статус телефона: STOCK_CODE_RESTORED, ещё НЕ наблюдался холодный старт.
Разрешён ручной обычный старт с батареей, затем stock USB mass storage microSD.
Диски ноутбука НЕ изменять. Карта на ПК ещё не идентифицирована, копирования нет.
Doom НЕ записан. Оба writer (старый V3 и новый bounded-stock) SPENT; не rerun.
После запуска stock ОС может изменить NV — база d6f0 не гарантируется дальше;
для следующей записи нужен новый согласованный fresh read/pin, не auto-repin.
Report: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_stock_restored_20261119_162843\REPORT_RU.md`. Исторические записи ниже — не текущий статус.

## Временный возврат родной прошивки — ОДНА проба 2026-11-19T16:28:22.868556+05:00

Пользователь: «ебашь прошивку старую, быстро всё делаем как в тот раз, БЕГОМ БЛЯТЬ» после запроса
на один временный возврат stock ради USB mass storage microSD.
Trial: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\stock_restore_for_v10_20261119_162803`. Original writer release не изменён и остаётся SPENT.
Отдельная копия ограничена [0xB000,0xF000), только pins+image length.
85 unit PASS + dryrun PASS. Base `b8e32e2d98d645490dc9f657192efd3218c7711976dccb48b09430472ba1d4d3`;
stock patch `32551e3af80f3b2fe2c7b9f280211c5e9694f29d4802f4b65604ca01326a47a2`; expected `b20f25fdfe14cb8024c39df0c9444ecc41d3402e813d558e82120b0e65104db7`.
Stock code [0,0x389000) восстановится побайтово из original9109aa;
весь outer NOR и текущее NV сохраняются. FULL NOR restore ЗАПРЕЩЁН.
Перед записью live geometry+fresh4MiB в этой же сессии, после full4MiB+audit.
Никаких retry/reset/FINISH/reconnect/clear-halt/автоотката.
Разрешение израсходовано на этот один запуск, результат ещё НЕ получен.
Doom этим запуском НЕ записывается. Диски ноутбука/карта не изменяются.

## V10 STOCK ATTEMPT STOPPED BEFORE DEVICE OPEN — 2026-11-19T16:27:00.605761+05:00

User authorized stock/card/V10. New stock trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\stock_restore_for_v10_20261119_162602 SPENT.
open_once found zero 0E8D:0003 in libusb; no DA init, no NOR read/write command.
Phone last verified installed V9 b8e32e2d98d645490dc9f657192efd3218c7711976dccb48b09430472ba1d4d3 unchanged by this attempt.
No retry/reset/reconnect/rollback performed. No card or host disk writes.
Request manual USB reconnect battery-out; any next physical trial must be NEW, never rerun this one.
V10 remains offline only; previous preparation 85 tests,279 candidate files PASS.

## Временный возврат родной прошивки — ОДНА проба 2026-11-19T16:26:43.408024+05:00

Пользователь: «ебашь прошивку старую, быстро всё делаем как в тот раз, БЕГОМ БЛЯТЬ» после запроса
на один временный возврат stock ради USB mass storage microSD.
Trial: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\stock_restore_for_v10_20261119_162602`. Original writer release не изменён и остаётся SPENT.
Отдельная копия ограничена [0xB000,0xF000), только pins+image length.
85 unit PASS + dryrun PASS. Base `b8e32e2d98d645490dc9f657192efd3218c7711976dccb48b09430472ba1d4d3`;
stock patch `32551e3af80f3b2fe2c7b9f280211c5e9694f29d4802f4b65604ca01326a47a2`; expected `b20f25fdfe14cb8024c39df0c9444ecc41d3402e813d558e82120b0e65104db7`.
Stock code [0,0x389000) восстановится побайтово из original9109aa;
весь outer NOR и текущее NV сохраняются. FULL NOR restore ЗАПРЕЩЁН.
Перед записью live geometry+fresh4MiB в этой же сессии, после full4MiB+audit.
Никаких retry/reset/FINISH/reconnect/clear-halt/автоотката.
Разрешение израсходовано на этот один запуск, результат ещё НЕ получен.
Doom этим запуском НЕ записывается. Диски ноутбука/карта не изменяются.

## V9 STATIC IMAGE USER REPORT; V10 OFFLINE READY, NOT FLASHED — 2026-11-19T16:20:12.135598+05:00

V9 installed unchanged b8e32e2d98d645490dc9f657192efd3218c7711976dccb48b09430472ba1d4d3. User reports loading artifacts then normal-looking
static game image, no visible error. No new video/FPS measurement; halt vs slow unproven.
New candidate C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_loop_v10_20261119_160714, 252groups PASS, two64-frame integrations, ordinary step inputs.
Actual old V9 synthetic-lag test proves hidden render batches1750->3500->7000.
V10 port uses one paced force_update per step; unbounded doom_update dead-stripped.
Same-lag test1/1/1; idle no redraw, key/LCD polling, wrap PASS. HUD border only.
No CPU/PLL/EMI/SFI/cache/voltage init changes. Cache remains disabled; MHz NOT measured.
Loading artifacts NOT established/fixed. Hardware V10 gameplay/FPS/audio NOT verified.
New card engine321952 SHA d76a9a8d8af53f0ef98912ffb88772850192237e6ccb040a03758d057dc8f0df REQUIRED before paired loader16196.
New card has NOT been copied; V10 has NOT been written; no new physical authorization.
No physical USB/card operations for this analysis. Previous V9 writer remains SPENT.
Future chain bounded stock -> one-file card copy/reopen hash -> NEW V10 trial,
with new reviewed stock base, same-session full before gate/full after+ELF,
only[B000,F000), no retry/reset/FINISH/reconnect/clearhalt/rollback/auto-repin/staging.
Report C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_doom_loop_v10_offline_20261119_162012\REPORT_RU.md. Older status headings do not override this observation.

## V9 PHYSICALLY WRITTEN; NEW CARD ENGINE VERIFIED — 2026-11-19T15:51:54.473218+05:00

User-directed sequence stock -> new DOOM.ELF -> V9 completed in this chat.
New card319984 SHA 2bd50fbe5b5d34b58e9885a7fa27cd59600540d05a87c58d7d0e16d5f57aa7af, Flush/reopen/full hash PASS;
WAD unchanged, freshly identified MINI_2 card, no formatting or laptop block changes.
Stock code restored then post-boot NV independently acquired/reviewed before NEW writer.
V9 full fresh same-session before b20f25fdfe14cb8024c39df0c9444ecc41d3402e813d558e82120b0e65104db7; actual after b8e32e2d98d645490dc9f657192efd3218c7711976dccb48b09430472ba1d4d3.
All4194304 bytes exact overlay; independent ELF PT_LOAD PASS. Only[B000,F000),
blocks11..14; all outer/NV preserved. Original standard DA/protocol unchanged.
OneD5/fourACK, USBerrors0/control0, no retry/reset/FINISH/reconnect/clearhalt/rollback/staging.
Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_runtime_v9_trial_20261119_154859 SPENT; physical-attempt.claimed.json and authorization-consumption.json authoritative.
Do NOT rerun or repin. Candidate250file seal unchanged;245 model groups +86 writer tests.
Manual USB disconnect + battery/card + normal cold boot WITHOUT STAR now allowed.
V9 hardware boot/control/FPS/startup improvement NOT YET OBSERVED; audio NOT implemented.
Return page ENGINE RETURN V9 shows CODE/FATL/FRM/LCD/FLAG; photograph if it appears.
Report C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_doom_runtime_v9_written_20261119_155154\REPORT_RU.md. Historical statuses below do not override this result.

## V9 ONE ATTEMPT STARTING — 2026-11-19T15:49:44.839492+05:00

User authorized stock -> card -> V9 sequence. New card engine full reopen/hash PASS.
Fresh post-card stock capture independently reviewed: only NV changed after stock boot.
NEW writer C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_runtime_v9_trial_20261119_154859; base b20f25fdfe14cb8024c39df0c9444ecc41d3402e813d558e82120b0e65104db7; expected b8e32e2d98d645490dc9f657192efd3218c7711976dccb48b09430472ba1d4d3.
Sealed candidate250 files/245 groups,86 writer tests PASS. Original standard protocol.
Only[B000,F000); live same-session full before equality gate BEFORE D3/D5; full after+ELF.
No staging pauses/retry/reset/FINISH/reconnect/clearhalt/rollback/auto-repin.
Old writers remain SPENT; this single authorization is now consumed. Result PENDING.
V9 NOT declared installed. Card files and laptop block devices not touched by writer.

## Родной код ВОССТАНОВЛЕН — 2026-11-19T15:40:51.051819+05:00

Одна авторизованная bounded-stock проба успешно завершена verified_without_reset.
Fresh-before `cf0e0cc4aeff8a8f74a3127a7e6bc87f414d2622e2d229c575a1affabba932f0`. Hardware full readback `6fce1362fd3dbbf2b6ab3b8ee0a5c2029a7e7753afe17d7659b9eaf284c47142`.
Независимый аудит всех4194304 байт PASS; stock code [0,0x389000) совпал
с original9109aa. Только секторы11..14 изменены; весь outer/NV сохранён.
НЕ full restore. Ноль reset/FINISH/retry/reconnect/control transfers.
Текущий статус телефона: STOCK_CODE_RESTORED, ещё НЕ наблюдался холодный старт.
Разрешён ручной обычный старт с батареей, затем stock USB mass storage microSD.
Диски ноутбука НЕ изменять. Карта на ПК ещё не идентифицирована, копирования нет.
Doom НЕ записан. Оба writer (старый V3 и новый bounded-stock) SPENT; не rerun.
После запуска stock ОС может изменить NV — база d6f0 не гарантируется дальше;
для следующей записи нужен новый согласованный fresh read/pin, не auto-repin.
Report: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_stock_restored_20261119_154051\REPORT_RU.md`. Исторические записи ниже — не текущий статус.

## Временный возврат родной прошивки — ОДНА проба 2026-11-19T15:40:05.661697+05:00

Пользователь: «Давай всё быстро и в темпе, старая прошивка, залив файлов, новая прошивка. Задание сбрасывать не надо, я у компа, сделаю всё быстро» после запроса
на один временный возврат stock ради USB mass storage microSD.
Trial: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\stock_restore_for_v9_20261119_153842`. Original writer release не изменён и остаётся SPENT.
Отдельная копия ограничена [0xB000,0xF000), только pins+image length.
85 unit PASS + dryrun PASS. Base `cf0e0cc4aeff8a8f74a3127a7e6bc87f414d2622e2d229c575a1affabba932f0`;
stock patch `32551e3af80f3b2fe2c7b9f280211c5e9694f29d4802f4b65604ca01326a47a2`; expected `6fce1362fd3dbbf2b6ab3b8ee0a5c2029a7e7753afe17d7659b9eaf284c47142`.
Stock code [0,0x389000) восстановится побайтово из original9109aa;
весь outer NOR и текущее NV сохраняются. FULL NOR restore ЗАПРЕЩЁН.
Перед записью live geometry+fresh4MiB в этой же сессии, после full4MiB+audit.
Никаких retry/reset/FINISH/reconnect/clear-halt/автоотката.
Разрешение израсходовано на этот один запуск, результат ещё НЕ получен.
Doom этим запуском НЕ записывается. Диски ноутбука/карта не изменяются.

## V9 OFFLINE VERIFIED; NEW CARD DOOM.ELF REQUIRED FIRST — 2026-11-19T15:32:50.737364+05:00

Installed V8 remains unchanged and SPENT. V8 photos ED02/static artifacts/no controls,
about7min user-reported. ED02=RAM engine returned, caller halts; reason NOT measured.
V9 C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_runtime_v9_20261119_151806: source fixes WAD maptexture int32 masked (ARM enum default1byte caused
wrong width/height), sprite names byte reads, full -warp episode/map argv6.
Indexed1-only removes unused RGBA256k; zone2.5MiB, arena use3036056/3145728 in model.
LCD latches REAL start BUSY/CPL before delayed poll, still fails missing/stuck events;
return page exposes mailbox error/FATL/FRM/LCD/FLAG. Hardware original ED02 root unknown.
SD identificationF0 -> selected card transfer30, readback gate; CPU/PLL/voltage/source
unchanged, actual hardware speed NOT measured. Hardware audio absent.
245 groups PASS, two64-frame integrations, all125 texture metadata/valid column
pixels exact independent MSVC reference. Synthetic turn/move/fire(50->49)/menu PASS.
V9 NOT WRITTEN. NEW card engine SHA 2bd50fbe5b5d34b58e9885a7fa27cd59600540d05a87c58d7d0e16d5f57aa7af, 319984bytes;
new loader image 16192 SHA 0875de9955289693c93cdb83fd899267e17d182e019c82d229a7b6cef0cca07f. Sealed 250files.
MUST copy new DOOM.ELF to freshly identified CARD ROOT before V9 loader; WAD unchanged.
No cardreader: bounded stock restore -> stock USB storage -> one-file copy+reopen/hash
-> NEW V9 physical trial. Historical D:/disk1 identity NOT reusable without rediscovery.
No formatting or laptop block changes. V8 reference overlay NOT post-restore flash pin;
future trial must bind verified installed stock acquisition after card-copy stage.
Only[B000,F000), full same-session before equality gate beforeD3/D5, after+ELF,
standard DA; no retry/reset/FINISH/reconnect/clear-halt/rollback/auto-repin. All old
spent writers stay spent; no physical operations were performed for this analysis.
Report C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_runtime_v9_offline_20261119_153250\REPORT_RU.md. Older statuses do not override this result.

## V8 PHYSICAL: visible image -> ED02 RETURN HALT; NOT PLAYABLE — 2026-11-19T15:02:23.053248+05:00

Photos show ED02 and corrupted-looking image. User reports no controls/static
image and about7min startup (NOT independently timed). ED02 is emitted by
NOR diagnostic_main ONLY after RAM engine entry returns, then board_halt.
Return reason unknown: mailbox.error/engine fatal NOT displayed. Do not guess
LCD/SD/allocator cause as established fact. Similar visual artifacts exist
in model image;64-frame model tests did NOT verify visual correctness.
Physical boot/engine entry/image now observed; playable game NOT verified.
Observation C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_v8_ed02_20261119_150223\runtime-observation.json; report C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_v8_ed02_20261119_150223\REPORT_RU.md.
Installed V8 NOR unchanged, writer SPENT; NEVER rerun/repin this trial.
No USB/card/host-block operations during this analysis. Phone may be powered off.
Next offline work: reproduce return gate, visual rendering, startup SD overhead.
New physical trial only NEW candidate-bound source, full same-session before
gate/after+ELF, four sectors[B000,F000), no retries/reset/FINISH/reconnect/rollback.
Historical statuses below do not override this observation.

## DOOM PLAY V8 ЗАПИСАНА; full NOR и ELF проверены — 2026-11-19T14:48:06.772758+05:00

Одна разрешённая физическая запись, новый V8 writer теперь SPENT. НЕ rerun/repin.
Fresh same-session full before V7 ca37304d6109bb70ed9b7a1fa482e087b069364171749929cd604b4665657d06;
actual full4MiB after V8 cf0e0cc4aeff8a8f74a3127a7e6bc87f414d2622e2d229c575a1affabba932f0. Image16008 SHA cb2aa23014ca5b0f08173dceb1480ac305d58515ba09175ed872cff4d76a24d3.
Все4194304байта совпали с overlay; ELF PT_LOAD independently exact.
Только секторы11–14 [B000,F000), outer/NV/stock bootloader сохранены.
USB errors0/control0; однаD5/четыреACK. Никаких retry/reset/FINISH/reconnect/
clear-halt/rollback/staging pauses. Карта/диски ноутбука НЕ изменялись.
Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_sprite_v8_trial_20261119_144706; physical-attempt.claimed.json/authorization-consumption.json авторитетны.

На телефоне V8; физический boot/игровой кадр ещё НЕ наблюдались.
ОтключитьUSB, аккумулятор+microSD, обычное включение БЕЗ STAR, снять результат.
V7 fatal invalid sprite frame28 PLAY/RD041E воспроизведён legacy sprite-name LDR
моделью; V8 actual C shim выравнивает138 sprite-name RAM DATA pointers после
полного original pointer/content gate. Engine opcodes и card DOOM.ELF/WAD/tree
неизменны. Buffer/BSS end0xEBA0 <0x10000. Bad data E801 без публикации pointers.
NOR sd_init Thumb для размера, source algorithm/CPU/PLL/voltage/SDdivider прежние.
234 groups, три64-frame модели PASS; это не аппаратное доказательство исправления/FPS.
Startup hooks на втором WAD callback; print/exit восстанавливаются после первого
кадра, aligned sprite-name DATA pointers остаются. Hardware audio отсутствует.
Report C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_doom_sprite_v8_written_20261119_144806\REPORT_RU.md.
Исторические статусы ниже не отменяют этот результат.

## DOOM PLAY V8: разрешение получено, ОДНА проба запускается — 2026-11-19T14:47:37.831118+05:00

Пользователь разрешил текущую V8: «Подключииил бро давай я верю в тебя».
Подключение battery-out USB сообщено пользователем; до discovery независимо не проверено. Одна попытка discovery/записи.
Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_sprite_v8_trial_20261119_144706; новый authorization V8 израсходован на ОДИН запуск.
Base ca37304d6109bb70ed9b7a1fa482e087b069364171749929cd604b4665657d06; expected cf0e0cc4aeff8a8f74a3127a7e6bc87f414d2622e2d229c575a1affabba932f0.
Протокол original standard physical_trial, full fresh same-session gate ДО D3/D5,
full readback после+независимый audit. Только[B000,F000). Результат пока НЕ получен.
Никаких staging pauses/retries/reset/FINISH/reconnect/clear-halt/rollback/auto-repin.
Пока НЕ объявлять V8 установленной. При ошибке STOP и сохранить сессию.
PREPARATION seal/authorization.json исторические, consumption marker physical-attempt.claimed.json авторитетен.

## DOOM PLAY V8: ОДНА запись подготовлена, USB пока не открыт — 2026-11-19T14:47:06.168925+05:00

Пользователь «Подключииил бро давай я верю в тебя» сообщил о подключении
после просьбы battery-out USB. Readiness user-reported, до discovery не проверена.
Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_sprite_v8_trial_20261119_144706; candidate C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_sprite_align_v8_20261119_143817. Новый writer/source, прежние V7 writers SPENT.
Image16008 SHA cb2aa23014ca5b0f08173dceb1480ac305d58515ba09175ed872cff4d76a24d3; patch e3f2fb9ded8b983b5faf10eee5cbd115a43c267ea88d020031fec73f858144b2.
Base V7 ca37304d6109bb70ed9b7a1fa482e087b069364171749929cd604b4665657d06; expected V8 cf0e0cc4aeff8a8f74a3127a7e6bc87f414d2622e2d229c575a1affabba932f0.
217-file candidate seal,234 model groups,86 writer tests и offline DryRun PASS.
Операций USB пока0. Только[B000,F000), full fresh same-session gate ДО D3/D5,
full after+independent ELF audit; original stock DA/protocol/guard неизменны.
Никаких retry/reset/FINISH/reconnect/clear-halt/rollback/auto-repin/staging pauses.
На телефоне пока verified V7. SD/card и диски ноутбука НЕ трогать.
V8 выравнивает138 sprite-name RAM DATA pointers; engine/card/WAD неизменны.
Аппаратное исправление и игровой кадр пока НЕ проверены.

## DOOM PLAY V8 ГОТОВА ОФЛАЙН, НЕ ЗАПИСАНА — 2026-11-19T14:42:13.232060+05:00

V7 physical fatal R_ProjectSprite invalid sprite frame28; user waited about5min.
Legacy sprite-name LDR model reproduces exact visible error AND RD1054=041E;
PLAY at0x3C283 is unaligned; sprites[28].numframes becomes0. Original Unicorn
permissive unaligned loads missed this. Not an SD write/format or clock problem
established by this test; do not overclaim physical root until patched boot.
V8 C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_sprite_align_v8_20261119_143817:138 immutable original sprite names copied into aligned persistent NOR-loader
BSS below0x10000; publishes ONLY engine RAM DATA sprnames pointers after complete
original pointer/content gate. No opcodes, card engine/tree/WAD changes.
Fingerprint FNV is accidental-integrity gate, NOT cryptographic authentication.
Bad table/range/content -> SPRITE DATA BAD / E801 before any pointer publication.
Alignment buffer and loader BSS end0xEBA0 remain below engine RAM0x10000; not TCM stack.
NOR-only sd_init newly Thumb for size; source/controller/SDdividerF0/CPU/PLL/voltage unchanged.
234 unit/model/packaging groups PASS; THREE64frame integrations, including actual
linked V8 C shim under legacy sprite-name LDR semantics, no host-side relocation.
Sprite28 PLAY has23frames, no unaligned sprite-name LDR/no fatal in that model.
Other instruction semantics not globally emulated; not hardware FPS or boot proof.
Image16008 SHA cb2aa23014ca5b0f08173dceb1480ac305d58515ba09175ed872cff4d76a24d3; patch e3f2fb9ded8b983b5faf10eee5cbd115a43c267ea88d020031fec73f858144b2.
Base current V7 ca37304d6109bb70ed9b7a1fa482e087b069364171749929cd604b4665657d06; expected V8 NOR cf0e0cc4aeff8a8f74a3127a7e6bc87f414d2622e2d229c575a1affabba932f0.
217-file seal validated. V8 has0physical operations; installed V7 unchanged and writer SPENT.
Next action: user battery-out USB connection readiness (not redundant permission),
then NEW candidate-bound one-use trial. Only[B000,F000), full fresh same-session
before equality gate beforeD3/D5, full after+independent ELF audit; standard DA,
no retry/reset/FINISH/reconnect/clear-halt/rollback/auto-repin/use-existing-DA.
Never rerun/repin any spent V7/V6 writer. Do not touch card/laptop disks.
Report C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_sprite_v8_ready_20261119_144137\REPORT_RU.md.
Historical statuses below do not override this result.

## V7 PHYSICAL FATAL локализован: sprite-name alignment; V8 OFFLINE — 2026-11-19T14:40:18.473436+05:00

Фото пользователя: DOOM FATAL V7 / invalid sprite frame28, RD041E, OFF0C, ERR0.
28=PLAY sprite index; log48chars truncates actual frame; raw CODEFFFFFFFF=exit(-1).
Legacy rotating LDR model at original engine instruction0x29B40 reproduces fatal
sprite28:13 AND RD1054=041E, zero frames. Default Unicorn did permissive unaligned
word reads, including with ARM926 selection; prior64frame tests missed this defect.
Host DATA alignment proof:138 aligned names ->64frames, PLAYnumframes23, no fatal.
V8 C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_sprite_align_v8_20261119_143817 offline implementation: guarded DATA pointer relocation only, no card/opcode
patches. Original immutable engine/card tree remains unchanged. NOR sd_init newly
Thumb for space; algorithm/clock/voltage/SDdivider unchanged. Full tests pending.
No USB/flash/card operations for this analysis. Installed verified V7 NOR unchanged;
writer SPENT, NEVER rerun/repin. V8 not physically tested or written; do not claim fix
on hardware until new trial and boot. Only[B000,F000), full fresh same-session gate
before D3/D5 and full after+independent ELF audit; no retry/reset/FINISH/reconnect.
Report C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_v7_fatal_alignment_20261119_144018\REPORT_RU.md. Historical statuses below do not override this result.

## DOOM START V7 ЗАПИСАНА, full NOR и ELF проверены — 2026-11-19T14:20:52.269299+05:00

Пользователь разрешил текущую V7 без повторного подтверждения; одна проба завершена.
Fresh full same-session before 64b6c22bf31804d35dcd24b5bd24a8d2c04212031ca96880bf8e2d7eb1926d6f;
actual full4MiB after ca37304d6109bb70ed9b7a1fa482e087b069364171749929cd604b4665657d06. Image16356 SHA 38974238418d5cd84043f221b39621a8d7c8369c1c031090130ebcf13acd3f21; patch 9fbe7b594b72248feaa779082c6bd2a3e733ad2f9d0f061f445c35304eb4f307.
Все4194304байта совпали с V7 overlay; ELF PT_LOAD независимо сверены.
Только секторы11–14 [B000,F000); outer/NV/stock bootloader сохранены.
USB errors0/control0; одна D5/четыреACK; no retry/reset/FINISH/reconnect/clear-halt/rollback.
Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_startup_v7_trial_20261119_141927; расходные physical-attempt.claimed.json/authorization-consumption.json
авторитетны; подготовительные authorization.json/preparation исторические. НЕ rerun/repin.

На телефоне теперь V7; физические boot/SD/игровой кадр V7 ещё НЕ наблюдались.
ОтключитьUSB, аккумулятор+microSD, обычное включение БЕЗ STAR; снять видео/последний экран.
Новые экраны DOOM INIT V7 / WAD IO ERROR V7 / DOOM FATAL V7 / TRACE NOT BOUND.
Hooks only at SECOND WAD callback; earlier stall/fatal remains uninstrumented.
Only RAM DATA callback pointers; no opcode patches; suppress PIO once frames>0,
restore pointers on next callback. V6 reached R_Init; actual stall cause unknown. V7 fixes diagnostic whitespace/newline filter only.
DOOM.ELF/WAD прежние, карту/диски НЕ форматировать. Hardware audio отсутствует.
Report C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_doom_startup_v7_written_20261119_142052\REPORT_RU.md.
Исторические статусы ниже не отменяют этот результат.

## DOOM START V7: разрешение получено, ОДНА проба запускается — 2026-11-19T14:20:23.600759+05:00

Пользователь разрешил текущую V7: «Давай на V7 Запустим уже его, заебал».
Физическая готовность этой V7 попытки не подтверждена; одна попытка discovery/записи.
Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_startup_v7_trial_20261119_141927; новый authorization V7 израсходован на ОДИН запуск.
Base 64b6c22bf31804d35dcd24b5bd24a8d2c04212031ca96880bf8e2d7eb1926d6f; expected ca37304d6109bb70ed9b7a1fa482e087b069364171749929cd604b4665657d06.
Протокол original standard physical_trial, full fresh same-session gate ДО D3/D5,
full readback после+независимый audit. Только[B000,F000). Результат пока НЕ получен.
Никаких staging pauses/retries/reset/FINISH/reconnect/clear-halt/rollback/auto-repin.
Пока НЕ объявлять V7 установленной. При ошибке STOP и сохранить сессию.
PREPARATION seal/authorization.json исторические, consumption marker physical-attempt.claimed.json авторитетен.

## DOOM START V7: новое разрешение на ОДНУ запись получено — 2026-11-19T14:19:27.994152+05:00

Пользователь «Давай на V7 Запустим уже его, заебал»
разрешил текущую V7. Физическая готовность V7 попытки отдельно не подтверждена;
это одна стандартная попытка обнаружения/записи, без повторов при ошибках.
Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_startup_v7_trial_20261119_141927; candidate C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_startup_v7_20261119_141525.
Image16356 SHA 38974238418d5cd84043f221b39621a8d7c8369c1c031090130ebcf13acd3f21; patch 9fbe7b594b72248feaa779082c6bd2a3e733ad2f9d0f061f445c35304eb4f307.
Base 64b6c22bf31804d35dcd24b5bd24a8d2c04212031ca96880bf8e2d7eb1926d6f; expected ca37304d6109bb70ed9b7a1fa482e087b069364171749929cd604b4665657d06.
86 fake-transport writer tests + offline DryRun PASS. Физических операций пока0;
на телефоне пока V6. Новая source-копия отличается только4 pins/image length;
DA/guard/standard protocol неизменны. Только[B000,F000), full fresh same-session
before equality gate ДО D3/D5, full after+independent audit. Никаких staged pauses,
retry/reset/FINISH/reconnect/clear-halt/rollback/auto-repin. При сбое STOP.
Карту и диски ноутбука НЕ трогать. Старые writers/authorization SPENT.

## DOOM TRACE V6 ЗАПИСАНА, full NOR и ELF проверены — 2026-11-19T14:03:17.481233+05:00

Пользователь разрешил текущую V6 без повторного подтверждения; одна проба завершена.
Fresh full same-session before 8a3eb01cf5cd9176e47099256181e2162cdef0a3c80694f6d0c2279c5a6d46a0;
actual full4MiB after 64b6c22bf31804d35dcd24b5bd24a8d2c04212031ca96880bf8e2d7eb1926d6f. Image16356 SHA b037019d53066ee5dd0be0b77bdc57fb5457ebb687eef1aac6119307be1e37ed; patch d31450a660b1bf8c7b0a3ee0967d467038f983ad1bd9d253e2f4a8c3dd4feae9.
Все4194304байта совпали с V6 overlay; ELF PT_LOAD независимо сверены.
Только секторы11–14 [B000,F000); outer/NV/stock bootloader сохранены.
USB errors0/control0; одна D5/четыреACK; no retry/reset/FINISH/reconnect/clear-halt/rollback.
Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_trace_v6_connected_trial_20261119_140200; расходные physical-attempt.claimed.json/authorization-consumption.json
авторитетны; подготовительные authorization.json/preparation исторические. НЕ rerun/repin.

На телефоне теперь V6; физические boot/SD/игровой кадр V6 ещё НЕ наблюдались.
ОтключитьUSB, аккумулятор+microSD, обычное включение БЕЗ STAR; снять видео/последний экран.
Новые экраны DOOM INIT V6 / WAD IO ERROR V6 / DOOM FATAL V6 / TRACE NOT BOUND.
Hooks only at SECOND WAD callback; earlier stall/fatal remains uninstrumented.
Only RAM DATA callback pointers; no opcode patches; suppress PIO once frames>0,
restore pointers on next callback. V5 D007 persisted; actual cause unknown.
DOOM.ELF/WAD прежние, карту/диски НЕ форматировать. Hardware audio отсутствует.
Report C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_doom_trace_v6_written_20261119_140317\REPORT_RU.md.
Исторические статусы ниже не отменяют этот результат.

## DOOM TRACE V6: разрешение получено, ОДНА проба запускается — 2026-11-19T14:02:34.294868+05:00

Пользователь разрешил текущую V6: «Давай делай».
Пользователь сообщил «подключил»; новая одноразовая попытка после ручного переподключения.
Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_trace_v6_connected_trial_20261119_140200; новый authorization V6 израсходован на ОДИН запуск.
Base 8a3eb01cf5cd9176e47099256181e2162cdef0a3c80694f6d0c2279c5a6d46a0; expected 64b6c22bf31804d35dcd24b5bd24a8d2c04212031ca96880bf8e2d7eb1926d6f.
Протокол original standard physical_trial, full fresh same-session gate ДО D3/D5,
full readback после+независимый audit. Только[B000,F000). Результат пока НЕ получен.
Никаких staging pauses/retries/reset/FINISH/reconnect/clear-halt/rollback/auto-repin.
Пока НЕ объявлять V6 установленной. При ошибке STOP и сохранить сессию.
PREPARATION seal/authorization.json исторические, consumption marker physical-attempt.claimed.json авторитетен.

## DOOM TRACE V6: новое разрешение на ОДНУ запись получено — 2026-11-19T14:02:00.641849+05:00

Пользователь «Давай делай»
разрешил текущую V6; теперь сообщил «подключил» после запроса battery-out USB;
это одна стандартная попытка обнаружения/записи, без повторов при ошибках.
Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_trace_v6_connected_trial_20261119_140200; candidate C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_engine_trace_20261119_133922.
Image16356 SHA b037019d53066ee5dd0be0b77bdc57fb5457ebb687eef1aac6119307be1e37ed; patch d31450a660b1bf8c7b0a3ee0967d467038f983ad1bd9d253e2f4a8c3dd4feae9.
Base 8a3eb01cf5cd9176e47099256181e2162cdef0a3c80694f6d0c2279c5a6d46a0; expected 64b6c22bf31804d35dcd24b5bd24a8d2c04212031ca96880bf8e2d7eb1926d6f.
86 fake-transport writer tests + offline DryRun PASS. Физических операций пока0;
на телефоне пока V5. Новая source-копия отличается только4 pins/image length;
DA/guard/standard protocol неизменны. Только[B000,F000), full fresh same-session
before equality gate ДО D3/D5, full after+independent audit. Никаких staged pauses,
retry/reset/FINISH/reconnect/clear-halt/rollback/auto-repin. При сбое STOP.
Карту и диски ноутбука НЕ трогать. Старые writers/authorization SPENT.

## DOOM TRACE V6 НЕ ЗАПИСАНА: устройство не найдено — 2026-11-19T13:57:53.711146+05:00

Одна разрешённая попытка C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_trace_v6_trial_20261119_135627 завершилась на open_once:
Need exactly one MediaTek 0E8D:0003, found 0. DA не запускалась; NOR read/erase/write НЕ начинались.
USB transfer log пуст. Никаких retries/reset/reconnect/FINISH. Trial SPENT, не rerun.
Installed record неизменён: последняя проверенная DOOM SD V5. V6 остаётся sealed offline.
Нужно физическое battery-out USB переподключение пользователем, НЕ повторное разрешение.
После готовности — НОВАЯ одноразовая attempt-wrapper с прежними V6 pins/guards,
не менять и не запускать spent writer. Same-session fresh full before equality
перед D3/D5 и full after+independent ELF audit обязательны; только[B000,F000).
Карту и диски ноутбука не трогать. Report C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_v6_device_not_found_20261119_135753\REPORT_RU.md.
Исторические статусы ниже не отменяют этот результат.

## DOOM TRACE V6: разрешение получено, ОДНА проба запускается — 2026-11-19T13:57:06.580958+05:00

Пользователь разрешил текущую V6: «Давай делай».
Свежая физическая готовность/переподключение не заявлены; одна попытка discovery/записи.
Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_trace_v6_trial_20261119_135627; новый authorization V6 израсходован на ОДИН запуск.
Base 8a3eb01cf5cd9176e47099256181e2162cdef0a3c80694f6d0c2279c5a6d46a0; expected 64b6c22bf31804d35dcd24b5bd24a8d2c04212031ca96880bf8e2d7eb1926d6f.
Протокол original standard physical_trial, full fresh same-session gate ДО D3/D5,
full readback после+независимый audit. Только[B000,F000). Результат пока НЕ получен.
Никаких staging pauses/retries/reset/FINISH/reconnect/clear-halt/rollback/auto-repin.
Пока НЕ объявлять V6 установленной. При ошибке STOP и сохранить сессию.
PREPARATION seal/authorization.json исторические, consumption marker physical-attempt.claimed.json авторитетен.

## DOOM TRACE V6: новое разрешение на ОДНУ запись получено — 2026-11-19T13:56:27.619163+05:00

Пользователь «Давай делай»
разрешил текущую V6. Свежая физическая готовность/переподключение НЕ заявлены;
это одна стандартная попытка обнаружения/записи, без повторов при ошибках.
Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_trace_v6_trial_20261119_135627; candidate C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_engine_trace_20261119_133922.
Image16356 SHA b037019d53066ee5dd0be0b77bdc57fb5457ebb687eef1aac6119307be1e37ed; patch d31450a660b1bf8c7b0a3ee0967d467038f983ad1bd9d253e2f4a8c3dd4feae9.
Base 8a3eb01cf5cd9176e47099256181e2162cdef0a3c80694f6d0c2279c5a6d46a0; expected 64b6c22bf31804d35dcd24b5bd24a8d2c04212031ca96880bf8e2d7eb1926d6f.
86 fake-transport writer tests + offline DryRun PASS. Физических операций пока0;
на телефоне пока V5. Новая source-копия отличается только4 pins/image length;
DA/guard/standard protocol неизменны. Только[B000,F000), full fresh same-session
before equality gate ДО D3/D5, full after+independent audit. Никаких staged pauses,
retry/reset/FINISH/reconnect/clear-halt/rollback/auto-repin. При сбое STOP.
Карту и диски ноутбука НЕ трогать. Старые writers/authorization SPENT.

## DOOM TRACE V6 готова ОФЛАЙН, НЕ ЗАПИСАНА — 2026-11-19T13:52:12.442269+05:00

V5 D007/RUN ENGINE persists by user confirmation; no physical game frame.
Exact root cause unknown. V6 C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_engine_trace_20261119_133922; image16356 SHA b037019d53066ee5dd0be0b77bdc57fb5457ebb687eef1aac6119307be1e37ed,
patch d31450a660b1bf8c7b0a3ee0967d467038f983ad1bd9d253e2f4a8c3dd4feae9, expected overlay 64b6c22bf31804d35dcd24b5bd24a8d2c04212031ca96880bf8e2d7eb1926d6f.
223 unit/model/packaging groups + two64frame models PASS. New late CMD17 fault
visible as WAD IO ERROR -> DOOM FATAL -> original fatal; not actual phone cause.
Card engine/doom tree unchanged. Startup hooks only RAM DATA print/exit pointers,
only if BOTH exact originals match. No opcode patches, card/USB/flash operations.
Attaches on SECOND WAD callback; a stall/fatal before it remains uninstrumented.
When engine frames>0: no startup PIO; original callbacks restored on next callback.
Idle-only PIO; no old framebuffer/DMA after handoff. NOR LCD/clock/MSDC additional
Thumb for size only, source logic/controller flags/GPT/PLL/VMC/SDdividerF0 unchanged.
Model time16us/GPTread +20ms/frame is synthetic, not phone timing/FPS proof.
Phone remains verified V5 NOR 8a3eb01cf5cd9176e47099256181e2162cdef0a3c80694f6d0c2279c5a6d46a0; old writer SPENT, NEVER rerun/repin.
Next action requires battery-out USB readiness, not redundant work permission.
Only[B000,F000), fresh full same-session gate beforeD3/D5, full after audit;
no retry/reset/FINISH/reconnect/clearhalt/rollback. V6 not yet hardware tested.
Report C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_engine_trace_v6_ready_20261119_135212\REPORT_RU.md.

## V5 D007 persists by user report; V6 OFFLINE diagnostics in development — 2026-11-19T13:39:22.954860+05:00

User confirms «Да, держит на этом». Exact continuous elapsed duration not measured.
V5 first WAD read passed; no game frame. Later WAD failures and Doom fatal/log
are invisible in current V5; D007 does not localize the current instruction.
V6 candidate C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_engine_trace_20261119_133922 is OFFLINE, NOT FLASHED; no USB/card/disk operations.
RAM DATA callback interposition only for exact original print/exit pointer values,
restored at first observed game frame; card engine/file bytes must stay unchanged.
Do not claim a root cause or fix. No PLL/voltage/divider experiment changes.
Original V5 writer remains SPENT, no automatic rerun/retry/repin.

## V5 VIDEO: ELF loaded, RUN ENGINE, D007; no game frame yet — 2026-11-19T13:27:52.468638+05:00

Video C:\Users\USER\Downloads\video_2026-11-19_13-23-47.mp4 (270x478,45.86s).
COPY ENGINE progresses, ZERO BSS, then RUN ENGINE entry00037D48. D007 overlay
proves RAM engine reached first WAD read and it returned requested count.
PH1100/ST09/ERR0/CS1/DS1. Other small digits not needed/transcribed.
Not FILE ERROR as prior V4. No physical game frame or completed Doom init yet.
RUN ENGINE is only visible in roughly last3s; DO NOT call this a proven hang.
D007 is NOT an error or full WAD/signature/game verification. SDdividerF0 remains
an experiment, not established cause/fix. No CPU/PLL/card changes; audio absent.
No USB/flash operations during analysis. Installed NOR remains verified V5;
spent physical trial must not be rerun. Observation C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_v5_video_20261119_132449\runtime-observation.json.

## DOOM SD V5 ЗАПИСАНА, full NOR и ELF проверены — 2026-11-19T13:19:10.488160+05:00

Пользователь разрешил текущую V5 без повторного подтверждения; одна проба завершена.
Fresh full same-session before 93c6bc351168e58c9c142f7f12daf3477a8ccd941fd0d420324036c339635854;
actual full4MiB after 8a3eb01cf5cd9176e47099256181e2162cdef0a3c80694f6d0c2279c5a6d46a0. Image16348 SHA 0a05f25129d614d81a74853a0737d676ae7905bcc29b402f1c9d19e132bf550c; patch 0c7317eed70bb4e36867394ed9356a5d9b7826acb249b852db0fdff3e3868894.
Все4194304байта совпали с V5 overlay; ELF PT_LOAD независимо сверены.
Только секторы11–14 [B000,F000); outer/NV/stock bootloader сохранены.
USB errors0/control0; одна D5/четыреACK; no retry/reset/FINISH/reconnect/clear-halt/rollback.
Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_sd_v5_trial_20261119_131634; расходные physical-attempt.claimed.json/authorization-consumption.json
авторитетны; подготовительные authorization.json/preparation исторические. НЕ rerun/repin.

На телефоне теперь V5, физические boot/SD/игровой кадр V5 ещё НЕ наблюдались.
ОтключитьUSB, аккумулятор+microSD, обычное включение БЕЗ STAR; снять видео/последний экран.
При FILE ERROR снять PH/CS/DS/LBA/WD/STA. При COPY/ZERO число=адресRAM.
D006=first WAD read begin; D007=read passed; ED07=read failed.
Предыдущая V4 на видео: identification passed, storage_open FR_IO/D210;
ELF-load не достигнут, причина CMD17 неизвестна. V5 latch диагностика и SDdividerF0
вместо post-identify0C — эксперимент, НЕ доказанный fix. CPU/PLL/voltage прежние.
DOOM.ELF/WAD прежние, карту/диски НЕ форматировать. Hardware audio отсутствует.
Report C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_doom_sd_v5_written_20261119_131910\REPORT_RU.md.
Исторические статусы ниже не отменяют этот результат.

## DOOM SD V5: готовность получена, ОДНА проба запускается — 2026-11-19T13:17:36.627590+05:00

Пользователь разрешил текущую V5: «Запускай без подтверждения, я того рот ебал каждый раз тебе разрешать».
Свежая физическая готовность/переподключение не заявлены; одна попытка discovery/записи.
Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_sd_v5_trial_20261119_131634; новый authorization V5 израсходован на ОДИН запуск.
Base 93c6bc351168e58c9c142f7f12daf3477a8ccd941fd0d420324036c339635854; expected 8a3eb01cf5cd9176e47099256181e2162cdef0a3c80694f6d0c2279c5a6d46a0.
Протокол original standard physical_trial, full fresh same-session gate ДО D3/D5,
full readback после+независимый audit. Только[B000,F000). Результат пока НЕ получен.
Никаких staging pauses/retries/reset/FINISH/reconnect/clear-halt/rollback/auto-repin.
Пока НЕ объявлять V5 установленной. При ошибке STOP и сохранить сессию.
PREPARATION seal/authorization.json исторические, consumption marker physical-attempt.claimed.json авторитетен.

## DOOM SD V5: новое разрешение на ОДНУ запись получено — 2026-11-19T13:16:34.824728+05:00

Пользователь «Запускай без подтверждения, я того рот ебал каждый раз тебе разрешать»
разрешил текущую V5. Свежая физическая готовность/переподключение НЕ заявлены;
это одна стандартная попытка обнаружения/записи, без повторов при ошибках.
Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_sd_v5_trial_20261119_131634; candidate C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\sd_cmd17_probe_20261119_130530.
Image16348 SHA 0a05f25129d614d81a74853a0737d676ae7905bcc29b402f1c9d19e132bf550c; patch 0c7317eed70bb4e36867394ed9356a5d9b7826acb249b852db0fdff3e3868894.
Base 93c6bc351168e58c9c142f7f12daf3477a8ccd941fd0d420324036c339635854; expected 8a3eb01cf5cd9176e47099256181e2162cdef0a3c80694f6d0c2279c5a6d46a0.
86 fake-transport writer tests + offline DryRun PASS. Физических операций пока0;
на телефоне пока V4. Новая source-копия отличается только4 pins/image length;
DA/guard/standard protocol неизменны. Только[B000,F000), full fresh same-session
before equality gate ДО D3/D5, full after+independent audit. Никаких staged pauses,
retry/reset/FINISH/reconnect/clear-halt/rollback/auto-repin. При сбое STOP.
Карту и диски ноутбука НЕ трогать. Старые writers/authorization SPENT.

## Видео V4: FILE ERROR/D210; V5 подготовлена ОФЛАЙН — 2026-11-19T13:12:03.415382+05:00

Физический V4 boot наблюдался на видео C:\Users\USER\Downloads\video_2026-11-19_12-58-38.mp4.
FILE ERROR00000001/ST09/PH0D05/ERR0000D210/CS1/DS0. SD identification прошла,
storage_open завершился FR_IO; ELF-load НЕ вызывался. PH/CS/DS — старый
identify snapshot, точная причина CMD17 и LBA неизвестны. Не объявлять WAD
потерянным/повреждённым или причиной CPU MHz без новых доказательств.
На телефоне остаётся V4 full NOR 93c6bc351168e58c9c142f7f12daf3477a8ccd941fd0d420324036c339635854; writer/разрешение SPENT.
V5 candidate C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\sd_cmd17_probe_20261119_130530; image16348 SHA 0a05f25129d614d81a74853a0737d676ae7905bcc29b402f1c9d19e132bf550c,
patch 0c7317eed70bb4e36867394ed9356a5d9b7826acb249b852db0fdff3e3868894, expected-overlay 8a3eb01cf5cd9176e47099256181e2162cdef0a3c80694f6d0c2279c5a6d46a0.
Латч CMD17 PH/CS/DS/LBA/WD/FIFO, без дополнительных read-to-clear чтений дляUI.
Убрано post-identify повышение SDdivider0C: остаётсяF0; CPU/PLL/voltage/EMI/
pinmux/LCD и файлы карты прежние. Снижение SDскорости — эксперимент, НЕ
доказанный fix. sd_board.c дополнительно Thumb для размера, interworking modelPASS.
212 offlinegroups + две64frame ARM модели PASS; это НЕ аппаратный запускV5.
Новых USB/flash операций0, разрешения на V5 НЕТ. Старые writers НЕ rerun/repin.
Для новой пробы нужно отдельное подтверждение, только[B000,F000), fresh full
same-session before gate ДО D3/D5, full after+audit; no retry/reset/FINISH/
reconnect/clear-halt/rollback. Диски/карту НЕ форматировать.
Report C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_sd_cmd17_v5_ready_20261119_131203\REPORT_RU.md.
Исторические статусы ниже не отменяют наблюдение этого видео.

## DOOM LOAD V4 ЗАПИСАНА, full NOR и ELF проверены — 2026-11-19T12:54:57.831594+05:00

Одна разрешённая проба verified_without_reset, USB errors0/control0.
Same-session fresh before 1c4fbefd5143b4424363275a96775bb3267eabc1859eb92c3239fd0023ae7205;
actual full4MiB after 93c6bc351168e58c9c142f7f12daf3477a8ccd941fd0d420324036c339635854.
Image16232 SHA 8e8d4c3592138ef844b9697c9db975e71dbf0e673df572621ab7e019be837536; patch c241f8e682567ed037337df713372d35211342e10a6a719e0ac2016c86a16fbe.
Все4194304байта после совпали с V4 overlay; ELF PT_LOAD независимо сверены.
Только секторы11–14 [B000,F000); outer/NV/stock bootloader сохранены из fresh before.
Одна D5/четыреACK; no retry/reset/FINISH/reconnect/clear-halt/rollback.
Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_load_v4_trial_20261119_125132; новое разрешение SPENT, НЕ rerun/repin.
Исторический authorization.json/preparation НЕ разрешают новый запуск;
physical-attempt.claimed.json/authorization-consumption.json авторитетны.
На телефоне теперь V4, но её физический boot/SD/игровой кадр пока НЕ наблюдались.
Ручной запуск: отключитьUSB, аккумулятор+microSD, обычная кнопка БЕЗ STAR.
Снять видео/последний экран COPY ENGINE/ZERO BSS/RUN ENGINE; число=адресRAM.
D006=first WAD read begin; D007=first WAD read passed; ED07=этот read failed.
V3 ранее физически прошла identify/storage_open, остановкуLOAD ENGINE не локализовали.
DOOM.ELF/WAD прежние; карту/диски НЕ форматировать. Hardware audio отсутствует.
Report C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_doom_load_v4_written_20261119_125457\REPORT_RU.md.
Исторические статусы ниже не отменяют этот результат.

## DOOM LOAD V4: готовность получена, ОДНА проба запускается — 2026-11-19T12:52:37.827697+05:00

Пользователь «Записывай» подтвердил именно V4; ранее сообщил подключение USB без аккумулятора.
Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_load_v4_trial_20261119_125132; новый authorization V4 израсходован на ОДИН запуск.
Base 1c4fbefd5143b4424363275a96775bb3267eabc1859eb92c3239fd0023ae7205; expected 93c6bc351168e58c9c142f7f12daf3477a8ccd941fd0d420324036c339635854.
Протокол original standard physical_trial, full fresh same-session gate ДО D3/D5,
full readback после+независимый audit. Только[B000,F000). Результат пока НЕ получен.
Никаких staging pauses/retries/reset/FINISH/reconnect/clear-halt/rollback/auto-repin.
Пока НЕ объявлять V4 установленной. При ошибке STOP и сохранить сессию.
PREPARATION seal/authorization.json исторические, consumption marker physical-attempt.claimed.json авторитетен.

## DOOM LOAD V4: новое разрешение на ОДНУ запись получено — 2026-11-19T12:51:32.951465+05:00

Пользователь «Записывай» после предложения именно V4. Ранее сообщил USB без
аккумулятора; это готовность к одной стандартной попытке, не разрешение повторять.
Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_load_v4_trial_20261119_125132; candidate C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_progress_20261119_123458.
Image16232 SHA 8e8d4c3592138ef844b9697c9db975e71dbf0e673df572621ab7e019be837536; patch c241f8e682567ed037337df713372d35211342e10a6a719e0ac2016c86a16fbe.
Base 1c4fbefd5143b4424363275a96775bb3267eabc1859eb92c3239fd0023ae7205; expected 93c6bc351168e58c9c142f7f12daf3477a8ccd941fd0d420324036c339635854.
86 fake-transport writer tests + offline DryRun PASS. Физических операций пока0;
на телефоне пока V3. Новая source-копия отличается только4 pins/image length;
DA/guard/standard protocol неизменны. Только[B000,F000), full fresh same-session
before equality gate ДО D3/D5, full after+independent audit. Никаких staged pauses,
retry/reset/FINISH/reconnect/clear-halt/rollback/auto-repin. При сбое STOP.
Карту и диски ноутбука НЕ трогать. Старые writers/authorization SPENT.

## DOOM LOAD V4 готова ОФЛАЙН; V3 LOAD ENGINE наблюдалась — 2026-11-19T12:48:36.243088+05:00

На телефоне остаётся DOOM SD V3, full NOR SHA 1c4fbefd5143b4424363275a96775bb3267eabc1859eb92c3239fd0023ae7205.
Фото V3: LOAD ENGINE /004006B4 (размер WAD4196020), ST09 PH0D05,
SDC50010200 CS1 DS0. SD identification и storage_open прошли; окончание
ELF-load/вход в движок и физический кадр НЕ подтверждены; время не измерено.
V4 candidate C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_progress_20261119_123458; image16232 SHA 8e8d4c3592138ef844b9697c9db975e71dbf0e673df572621ab7e019be837536,
patch c241f8e682567ed037337df713372d35211342e10a6a719e0ac2016c86a16fbe, expected-overlay 93c6bc351168e58c9c142f7f12daf3477a8ccd941fd0d420324036c339635854.
Только NOR UI/load progress/chunked16KiB ELF/word BSS zero64KiB progress;
storage.c теперь Thumb, реальный interworking проверен. Board/SD/SIEN/power/
voltage/PLL/EMI/LCD/startup/linker и карта DOOM.ELF не изменены.
208 offline groups PASS + две64frame ARM model integrations.
Физических операций0; нового разрешения на запись V4 НЕТ. Все prior writers SPENT.
Не запускать старые writers/launchers и не repin автоматически. Для V4 сначала
новое явное разрешение; только[B000,F000), fresh full same-session gate BEFORE
D3/D5 и full after+audit, без retry/reset/FINISH/reconnect/clear-halt/rollback.
Карту/ноутбук НЕ форматировать. Hardware audio не реализован.
Report C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_doom_load_v4_ready_20261119_124836\REPORT_RU.md. Исторические секции ниже не описывают новое состояние.

## DOOM SD V3 ЗАПИСАНА; full NOR и ELF проверены — 2026-11-19T00:25:11.007432+05:00

Одна разрешённая user-ready проба verified_without_reset, USB errors0/control0.
Same-session fresh before bf091a3f8c608fac947f43e4ddf791feeb7b3411494eceec4eefc4573bcdfdf3;
actual hardware full after 1c4fbefd5143b4424363275a96775bb3267eabc1859eb92c3239fd0023ae7205.
Image16148 SHA 2b0b015225ccf32716ffef28c5107e4c67a056f53792c72e64cbcde0e6f7d342; patch b3cf7a87b594666518e974aa46ec7a1920fe85927eb0a0dd61611e13a3921c1a.
Все4194304байта+ELF PT_LOAD совпали. Изменены только секторы11..14 [B000,F000),
внешние байты/NV из fresh before сохранены. Одна D5/четыре ACK.
No reset/FINISH/retry/reconnect/clear-halt/rollback; разрешение SPENT.
Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_sd_v3_trial_20261119_001901; authoritative consumption physical-attempt.claimed.json / authorization-consumption.json.
Исторические PREPARATION/authorization.json не обновляются, НЕ дают права rerun.
Текущий firmware DOOM SD V3. Physical V3 boot/SD/gameplay ещё НЕ наблюдались.
Ручной запуск: USB отключить, батарея+microSD, обычная кнопка БЕЗ STAR.
Нужно фото всего экрана: error/ST/PH/CFG/SDC/BUS/CS/DS. V3 включает SIEN;
физический успех ещё не проверен. Prior V2: D101/PH0003/SIEN0.
Карту/ноутбук не форматировать, Doom файлы подходят; hardware audio отсутствует.
Report C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_doom_sd_v3_written_20261119_002511\REPORT_RU.md. Предыдущие статусы ниже — история.

## DOOM SD V3: готовность получена, ОДНА проба запускается — 2026-11-19T00:22:48.554855+05:00

Пользователь «готов» после инструкции USB без батареи/кнопок.
Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_sd_v3_trial_20261119_001901; новый authorization V3 израсходован на ОДИН запуск.
Base bf091a3f8c608fac947f43e4ddf791feeb7b3411494eceec4eefc4573bcdfdf3; expected 1c4fbefd5143b4424363275a96775bb3267eabc1859eb92c3239fd0023ae7205.
Протокол original standard physical_trial, full fresh same-session gate ДО D3/D5,
full readback после+независимый audit. Только[B000,F000). Результат пока НЕ получен.
Никаких staging pauses/retries/reset/FINISH/reconnect/clear-halt/rollback/auto-repin.
Пока НЕ объявлять V3 установленной. При ошибке STOP и сохранить сессию.
PREPARATION seal/authorization.json исторические, consumption marker physical-attempt.claimed.json авторитетен.

## DOOM SD V3: ОДНА запись разрешена, готовность ещё не получена — 2026-11-19T00:19:01.777527+05:00

Пользователь разрешил одну запись V3 с исправлением SIEN в четырёх секторах.
Trial: C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_sd_v3_trial_20261119_001901. Никаких физических операций пока НЕТ; на телефоне остаётся V2.
Image16176 SHA 2b0b015225ccf32716ffef28c5107e4c67a056f53792c72e64cbcde0e6f7d342; patch b3cf7a87b594666518e974aa46ec7a1920fe85927eb0a0dd61611e13a3921c1a.
Base bf091a3f8c608fac947f43e4ddf791feeb7b3411494eceec4eefc4573bcdfdf3; expected 1c4fbefd5143b4424363275a96775bb3267eabc1859eb92c3239fd0023ae7205.
86 offline writer tests + DryRun PASS; протокол/DA/guard неизменны, только pins/length.
Ждать новой ручной готовности телефона; затем один original standard physical_trial,
без staging pause, full same-session fresh before equality gate ДО D3/D5,
полный readback после + independent audit. Только[B000,F000).
При любом сбое STOP; no auto-repin/retry/reset/FINISH/reconnect/clear-halt/rollback.
Фото V2: PH0003/SDC50000200. V3 включает SIEN; физический успех ещё не проверен.
Карту/диски не форматировать; файлы Doom на карте прежние и подходят.

## V2 фото: SIEN=0; V3 SIEN fix проверена ОФЛАЙН — 2026-11-19T00:15:52.419557+05:00

ФотоV2 D101/ST01/PH0003 CFG0400F081 SDC50000200 BUS8000 CS0 DS0 VMC0C42->8C43.
V2 boot/LCD наблюдались, SD identification не прошла. Подтверждён наш software bug:
SDC_CFG bit16 SIEN очищался и не включался. Datasheet3.16 и первичный header
SDC_SIEN=(1<<16). Фото подтверждает бит0. Единственная ли это физическая
проблема — пока НЕ проверено. Старые модели ошибочно игнорировали SIEN.
Новый кандидат C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\sd_sien_fix_20261119_001128: DOOM SD V3, SDC50010200;
только SIEN enable+preconditions и исправленная модель; power/voltage/pinmux/
clock/PLL/EMI/SFI/reset sequence прежние. Реальный старый V2 binary negative,
V3 positive на SIEN-aware модели;194 checks+два64frameARM integrations PASS.
Image16176 SHA 2b0b015225ccf32716ffef28c5107e4c67a056f53792c72e64cbcde0e6f7d342, patch b3cf7a87b594666518e974aa46ec7a1920fe85927eb0a0dd61611e13a3921c1a.
DOOM.ELF тот же, карту не переписывать. V2 manifest141 unchanged.
На телефоне остаётся V2 NOR bf091a3f8c608fac947f43e4ddf791feeb7b3411494eceec4eefc4573bcdfdf3.
V3 НЕ записана, USB/block devices НЕ открывали, нового flash authorization НЕТ.
Нужно отдельное V3 разрешение+готовность; original guarded writer только[B000,F000),
fresh same-session full before+full after+audit, no retry/reset/FINISH/reconnect/
clear-halt/rollback/auto-repin. Старые authorizations SPENT. Не форматировать
карту/диски ноутбука, hardware audio отсутствует.
Report C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_doom_sd_v3_sien_fix_20261119_001552\REPORT_RU.md. Предыдущие статусы ниже — история.

## DOOM SD V2 ЗАПИСАНА; full NOR и ELF проверены — 2026-11-19T00:02:31.631692+05:00

Одна разрешённая user-ready проба verified_without_reset, USB errors0/control0.
Same-session fresh before a2fe91453b19348805f23912ea3de5cfb7395f99a8722c0653bc1e001f7fa23d;
actual hardware full after bf091a3f8c608fac947f43e4ddf791feeb7b3411494eceec4eefc4573bcdfdf3.
Image16148 SHA 387af2bf924c6b09c1c087fdb46f5f2c339322bd077197cc037ab40e0425aea8; patch 459c1483085ccc5797acfd6232d685e4f1079283f46871558ba71353caaf5b00.
Все4194304байта+ELF PT_LOAD совпали. Изменены только секторы11..14 [B000,F000),
внешние байты/NV из fresh before сохранены. Одна D5/четыре ACK.
No reset/FINISH/retry/reconnect/clear-halt/rollback; разрешение SPENT.
Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_sd_v2_trial_20261118_235422; authoritative consumption physical-attempt.claimed.json / authorization-consumption.json.
Исторические PREPARATION/authorization.json не обновляются, НЕ дают права rerun.
Текущий firmware DOOM SD V2. Physical V2 boot/SD/gameplay ещё НЕ наблюдались.
Ручной запуск: USB отключить, батарея+microSD, обычная кнопка БЕЗ STAR.
Нужно фото всего экрана: error/ST/PH/CFG/SDC/BUS/CS/DS. V2 — диагностика,
не proven SD fix. Prior V1 SD D101 stage1; физическая причина пока неизвестна.
Карту/ноутбук не форматировать, Doom файлы подходят; hardware audio отсутствует.
Report C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_doom_sd_v2_written_20261119_000231\REPORT_RU.md. Предыдущие статусы ниже — история.

## DOOM SD V2: готовность получена, ОДНА проба запускается — 2026-11-18T23:58:36.474568+05:00

Пользователь «готов» после инструкции USB без батареи/кнопок.
Trial C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_sd_v2_trial_20261118_235422; новый authorization V2 израсходован на ОДИН запуск.
Base a2fe91453b19348805f23912ea3de5cfb7395f99a8722c0653bc1e001f7fa23d; expected bf091a3f8c608fac947f43e4ddf791feeb7b3411494eceec4eefc4573bcdfdf3.
Протокол original standard physical_trial, full fresh same-session gate ДО D3/D5,
full readback после+независимый audit. Только[B000,F000). Результат пока НЕ получен.
Никаких staging pauses/retries/reset/FINISH/reconnect/clear-halt/rollback/auto-repin.
Пока НЕ объявлять V2 установленной. При ошибке STOP и сохранить сессию.
PREPARATION seal/authorization.json исторические, consumption marker physical-attempt.claimed.json авторитетен.

## DOOM SD V2: ОДНА запись разрешена, готовность ещё не получена — 2026-11-18T23:54:23.033209+05:00

Пользователь «Разрешаю» на конкретную диагностическую V2 в четырёх секторах.
Trial: C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_sd_v2_trial_20261118_235422. Никаких физических операций пока НЕТ; на телефоне остаётся V1.
Image16148 SHA 387af2bf924c6b09c1c087fdb46f5f2c339322bd077197cc037ab40e0425aea8; patch 459c1483085ccc5797acfd6232d685e4f1079283f46871558ba71353caaf5b00.
Base a2fe91453b19348805f23912ea3de5cfb7395f99a8722c0653bc1e001f7fa23d; expected bf091a3f8c608fac947f43e4ddf791feeb7b3411494eceec4eefc4573bcdfdf3.
86 offline writer tests + DryRun PASS; протокол/DA/guard неизменны, только pins/length.
Ждать новой ручной готовности телефона; затем один original standard physical_trial,
без staging pause, full same-session fresh before equality gate ДО D3/D5,
полный readback после + independent audit. Только[B000,F000).
При любом сбое STOP; no auto-repin/retry/reset/FINISH/reconnect/clear-halt/rollback.
Фото V1 показало D101/STAGE01, причина пока неизвестна. V2 — диагностика, НЕ proven fix.
Карту/диски не форматировать; файлы Doom на карте прежние и подходят.

## DOOM SD V1: физический SD ERROR; V2 только офлайн — 2026-11-18T23:47:27.689118+05:00

Фото пользователя: DOOM SD V1, D101/STAGE01, SECTORS0, VMC0C42->8C43.
Boot/LCD физически наблюдались; SD identification НЕ прошла, Doom не запущен.
D101 не различает config/preidle/CMD0/postidle: физическая причина НЕ установлена.
VMC readback не доказывает фактическое напряжение или связь с microSD.
Новый кандидат DOOM SD V2: C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\sd_diag_20261118_233617. Только latched PH/CFG/SDC/BUS/CS/DS;
питание/voltage/pinmux/reset/CMD17 источники прежние, SD порядок/слова/лимиты прежние.
main Thumb, ARM interworking проверен; timing equivalence не заявлена.
Image16148 SHA 387af2bf924c6b09c1c087fdb46f5f2c339322bd077197cc037ab40e0425aea8, patch 459c1483085ccc5797acfd6232d685e4f1079283f46871558ba71353caaf5b00.
186 unit/model/packaging PASS + два64frame ARM Doom model. НЕ аппаратный успех.
DOOM.ELF тот же SHA9bc037...1c05a, переписывать карту не требуется.
180 baseline manifest entries неизменны. V2 НЕ записана; USB/card/block devices НЕ открывали.
Нового flash authorization НЕТ. Старая V1 installed NOR a2fe9145...f23d неизменна.
Все прежние writers SPENT, не rerun/auto-repin. Новый trial только после
конкретного разрешения V2+готовности, original guarded writer [B000,F000),
same-session fresh full before+full after+audit; no retry/reset/FINISH/reconnect/rollback.
Не форматировать SD и тем более laptop. Аппаратный аудиовыход не реализован.
Report: C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_doom_sd_v2_diagnostic_20261118_234727\REPORT_RU.md. Более старые статусы ниже — история.

## DOOM SD V1 ЗАПИСАНА и full NOR проверен — 2026-11-18T23:27:46.542546+05:00

Одна новая user-ready проба успешно verified_without_reset. Ноль USB ошибок.
Fresh before `6fce1362fd3dbbf2b6ab3b8ee0a5c2029a7e7753afe17d7659b9eaf284c47142`; аппаратный full readback `a2fe91453b19348805f23912ea3de5cfb7395f99a8722c0653bc1e001f7fa23d`.
Image16020 SHA `c7ce977a1475b6d63c721e0e7978cfe448437cdd1f593d13a2e17cd75ed031d6`; patch `99ae5ee75d16ce12ffc97b2d20cc8db74e6eddacb978d10940a2bd0f3c73b43a`.
Только секторы11..14 изменены; весь outer/NV свежего before сохранён.
Независимые4194304 байта+ELF PT_LOAD PASS. Одна D5/четыреACK; no reset/FINISH/
retry/reconnect/rollback/control transfers. Все использованные writer SPENT.
Текущий firmware DOOM SD V1, физический cold boot/SD/gameplay ещё НЕ наблюдались.
Теперь ручной запуск: USB отключить, батарея+microSD, обычная кнопка БЕЗ STAR.
Ошибка SD/FILE/LOAD: нужны фото code,VMC,STAGE,SECTORS. Не auto flash/rollback.
Аппаратный аудиовыход отсутствует; SD-последовательность пока экспериментальная.
Report `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_doom_sd_v1_written_20261118_232746\REPORT_RU.md`. Предыдущие статусы ниже — история.

## DOOM SD V1: новая готовность, одна стандартная проба — 2026-11-18T23:25:59.200992+05:00

Пользователь «готов» после USB-error-before-D3/D5. Предыдущая проба не писала NOR.
Trial `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_write_ready_20261118_232558`. Base `6fce1362fd3dbbf2b6ab3b8ee0a5c2029a7e7753afe17d7659b9eaf284c47142`; patch `99ae5ee75d16ce12ffc97b2d20cc8db74e6eddacb978d10940a2bd0f3c73b43a`;
expected `a2fe91453b19348805f23912ea3de5cfb7395f99a8722c0653bc1e001f7fa23d`. Те же проверенные86tests источники без правок.
Original standard physical_trial, без staging паузы; live geometry+full4MiB
строго должны совпасть с reviewed base ДО D3/D5; full4MiB после+audit.
Только [B000,F000); no auto-repin/retry/reset/FINISH/reconnect/clear-halt.
Разрешение израсходовано на один этот запуск; результат ещё не получен.
Doom experimental SD boot; audio hardware не реализован. Laptop/card не менять.

## DOOM SD V1: разрешена одна read-review-write проба — 2026-11-18T23:18:43.1612236+05:00

Пользователь: «делай брат» после инструкции входа для конкретного Doom loader.
Trial: C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\doom_trial_20261118_231815
NOR только [0xB000,0xF000), image16020, SHA c7ce977a1475b6d63c721e0e7978cfe448437cdd1f593d13a2e17cd75ed031d6.
Первый этап только geometry+fresh4MiB, NO D3/D5. Оператор отдельно проверяет
stock-code prefix/NV-only changes и вручную закрепляет новую базу/expected.
Процесс держит ТОТ ЖЕ original DA/USB handle и ждёт explicit offline pin job;
никакого auto-repin на ошибке и ExistingDA/reconnect/fallback. Перед D3 ещё
одна geometry+full4MiB equality gate; после full4MiB+independent audit.
Физическая SD/boot probe экспериментальная; аудиовыход не реализован.
No reset/FINISH/retry/reconnect/clear-halt/rollback. Laptop/card не меняются.
Результат пока НЕ получен, Doom пока НЕ объявлять установленным.

## microSD подготовлена — 2026-11-18T23:10:42.2671745+05:00

Родной USB mass storage появился после ручного запуска с батареей.
Карта: USB MINI_2 диск1 D: FAT32 15635841024 байта. E:22KiB internal НЕ тронут.
Скопированы D:\DOOM.ELF320208 и D:\DOOM1.WAD4196020, Flush(true)+reopen SHA PASS.
Форматирования/удалений/NOR/USB DA операций на этом этапе НЕТ. Laptop NVMe0 НЕ трогать.
Doom loader ещё НЕ записан. Разрешения на его запись пока НЕТ.
Текущий NOR d6f0 — последний readback ДО stock boot; NV после stock OS могло измениться.
Нужны новый согласованный fresh read/pin и отдельная конкретная Doom trial, не rerun old writers.
Report: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_doom_card_ready_20261118_231134\REPORT_RU.md`.

## Родной код ВОССТАНОВЛЕН — 2026-11-18T23:08:02.436358+05:00

Одна авторизованная bounded-stock проба успешно завершена verified_without_reset.
Fresh-before `bc942e7a3e8baa0564fd7fb0017d6665007cc5c3280904a406ac129a9f8f84e5`. Hardware full readback `d6f0ea242b07cd4bc747b269e1aed4e96bae72015e45bc2d99164d7c0754e245`.
Независимый аудит всех4194304 байт PASS; stock code [0,0x389000) совпал
с original9109aa. Только секторы11..14 изменены; весь outer/NV сохранён.
НЕ full restore. Ноль reset/FINISH/retry/reconnect/control transfers.
Текущий статус телефона: STOCK_CODE_RESTORED, ещё НЕ наблюдался холодный старт.
Разрешён ручной обычный старт с батареей, затем stock USB mass storage microSD.
Диски ноутбука НЕ изменять. Карта на ПК ещё не идентифицирована, копирования нет.
Doom НЕ записан. Оба writer (старый V3 и новый bounded-stock) SPENT; не rerun.
После запуска stock ОС может изменить NV — база d6f0 не гарантируется дальше;
для следующей записи нужен новый согласованный fresh read/pin, не auto-repin.
Report: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_stock_restored_20261118_230802\REPORT_RU.md`. Исторические записи ниже — не текущий статус.

## Временный возврат родной прошивки — ОДНА проба 2026-11-18T23:06:42.900508+05:00

Пользователь: «Загружай, да, причем старайся сделать быстро» после запроса
на один временный возврат stock ради USB mass storage microSD.
Trial: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\stock_restore_20261118_230514`. Original writer release не изменён и остаётся SPENT.
Отдельная копия ограничена [0xB000,0xF000), только pins+image length.
85 unit PASS + dryrun PASS. Base `bc942e7a3e8baa0564fd7fb0017d6665007cc5c3280904a406ac129a9f8f84e5`;
stock patch `32551e3af80f3b2fe2c7b9f280211c5e9694f29d4802f4b65604ca01326a47a2`; expected `d6f0ea242b07cd4bc747b269e1aed4e96bae72015e45bc2d99164d7c0754e245`.
Stock code [0,0x389000) восстановится побайтово из original9109aa;
весь outer NOR и текущее NV сохраняются. FULL NOR restore ЗАПРЕЩЁН.
Перед записью live geometry+fresh4MiB в этой же сессии, после full4MiB+audit.
Никаких retry/reset/FINISH/reconnect/clear-halt/автоотката.
Разрешение израсходовано на этот один запуск, результат ещё НЕ получен.
Doom этим запуском НЕ записывается. Диски ноутбука/карта не изменяются.

# Kenshi Mini 2: подключение, безопасная запись и управление

## V3 runtime:≈260MHz loop estimate, DRAW≈62ms/FPS11, NO physical vibration, SD16GB — 2026-11-18T22:03:15.225730+05:00

User photos:5released raw0,5held raw2000(bit13); VIB0001 both, user explicitly
reports NO VIBRATION. Control readback/restoration success is NOT motor success.
V3 trigger is50ms nominal rising-edge pulse, not sustained hold. Original VIBR
word/VOSEL not exposed; do not claim absent/broken motor or select new voltage.
TCM100K1542us/1M15388us: differential4cycle model=>≈260MHz, not26; inference
conditional on4cycle loop/GPT nominal26MHz, not precise independent clock meter.
DRAW62332us vs≈173880us before (~2.79x), DMA21695us, HUD11vs5FPS. NOT Doom FPS.
V3 boots, RAM/heap OK shown; MCU B621/B621 MPLL1401/1401 DIV0/0.
User reports installed phone memory card16GB; FS/partitions unknown, custom SD
readability NOT tested. Read-only SD/WAD/loader is next Doom priority, no format.
No USB/flash/firmware/writer changes, no NEW flash authorization; writer spent.
NOR last verifiedbc942e7a...f84e5 unchanged as last known, not fresh read now.
Report: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_v3_runtime_20261118_220315\REPORT_RU.md`. Older runtime-pending sections are historical.


## CLK DIAG V3 записана и полностью проверена — 2026-11-18T21:55:25.743039+05:00

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

V3 optimized renderer/TCM/numeric5VIBR; audio/SD absent, Doom NOT written.
Authorization consumed; no retry/reset/FINISH/reconnect/clear-halt/rollback.
Writer remains old-base pinned c1597dd2...cf075, DO NOT rerun/auto-repin.
Report: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_clk_v3_written_20261118_215525\REPORT_RU.md`. Earlier status sections remain historical.


## CLK DIAG V3: разрешена ОДНА запись — 2026-11-18T21:53:21.332206+05:00

Пользователь: «Записывай», в ответ на предложение именно V3.
Trial: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\clk_v3_trial_20261118_215049_071909`. Base `c1597dd261cdecff1f419b776eaeb37f8ba559856859c7b56031868895acf075`.
Patch `a8a8830bd57e9e23ecd1fee1ff06ee10163ac678a116add269590c4c62252c5e`; expected NOR `bc942e7a3e8baa0564fd7fb0017d6665007cc5c3280904a406ac129a9f8f84e5` пока НЕ readback.
Writer112 unit+17native PASS OFFLINE; protocol/USB/DA/range unchanged, pins only.
До USB нужен DryRun; затем ровно один original BootROM/stock DA заход.
Same-session geometry+fresh4MiB before D3/D5; full4MiB after+independent audit.
Ни UseExistingDA, ни FINISH/reset/retry/reconnect/clear-halt/rollback. STOP при ошибке.
V3 содержит TCM+renderer+numeric5 VIBR50ms/restoration, не меняет VOSEL.
PLL/EMI/SFI/cache/voltage init unchanged. Physical audio/SD absent; Doom НЕ пишется.
Пока установлен V2 NOR c1597dd2...cf075; не объявлять V3 установленной заранее.


## CLK DIAG V3 + Doom ARM — офлайн пакет, НЕ ЗАПИСАНО — 2026-11-18T21:45:51.447182+05:00

Единый пакет подготовлен: V3 optimized renderer + bounded TCM100K/1M +
user-triggered numeric5 VIBR50ms/restoration. Новый VIBR control pulse есть;
НЕ говорить PMIC completely unchanged. PLL/EMI/SFI/cache/voltage init unchanged.
V3 patch a8a8830bd57e9e23ecd1fee1ff06ee10163ac678a116add269590c4c62252c5e; ELF 09b7b2304ad9239e8d541977e6317aa8660632d8e8f28c93a95bc116d47a1cd5.
Image12256bytes; только[B000,F000), outer bytes/ELF/GFH PASS.
11packaging/26diag/10clock/11probes/heap controls PASS; same-pixels renderer
ARM instructions -55.50% (NOT hardware FPS). Stock BL1 profiles2/3/5
intentionally writeB621, not proof of26MHz; actual CPU MHz remains unmeasured.
Doom RAM ELF actual ARM E1M1 64frames+software PCM PASS, NOT bootable/flashed.
WAD4196020>RAM4194304; SD/FAT, RAM loader and physical PCM sink unsolved.
No USB/phone operations, no writer modifications or new flash authorization.
Phone remains VERIFIED V2 NOR c1597dd261cdecff1f419b776eaeb37f8ba559856859c7b56031868895acf075.
Spent writer must NOT rerun/auto-repin. Need exact V3 authorization+new readiness;
reuse original guarded writer, same-session full before/after and independent audit.
Report: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_game_platform_20261118_214329\REPORT_RU.md`. Earlier sections remain historical.


## GPT/SEC: внешняя грубая сверка сходится по сообщению пользователя — 2026-11-18T20:55:43.895454+05:00

На предложенную сверку SEC за60с внешним секундомером пользователь ответил
«Сходятся». Это USER-REPORTED COARSE MATCH, не новый USB read и не лог прибора.
Начальное/конечное SEC и численная погрешность не предоставлены: не выдумывать
точную калибровку26MHz или точность до микросекунд. Грубая ошибка×10 масштаба
таймера не поддерживается; DRAW≈174ms/DMA≈21.7ms можно использовать как
практические номинальные интервалы. CPU26vs260 всё ещё НЕ измерено.
Следующий безопасный шаг: отдельные CPU/PSRAM/raster/text microbench офлайн;
PLL/EMI/PMIC/voltage/кэш аппаратно не менять без проверки и нового разрешения.
Новых физических операций/firmware/writer edits/flash authorization НЕТ.
Последний verified NOR c1597dd2...cf075 неизменён; spent writer не rerun/repin.
Evidence: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\timer_check_20261118_205543_895454\observation.json`. Исторические reports/manifests не менялись.

## CLK DIAG V2: запуск по фото подтверждён — 2026-11-18T20:50:59.149824+05:00

User photo: MCU B621/B621, MPLL1401/1401, DIV0/0. DRAW≈173.9ms,
DMAX174120us, DMA21692us, XMAX21702us, SEC192, FRAMES988, FPS5,
P0/R0/raw0; RAM4096K OK, HEAP GUARDS OK. SD AUDIO NO TEST.
BOOT/main observed; RAM selftest PASS reported by firmware. A still does not
prove continuous motion/external elapsed time/key transitions/GPT accuracy.
DRAW≈89% of DRAW+DMA; includes PSRAM/code-fetch waits, NOT CPU MHz.
Diagnostic screen redundantly draws fullbars then clears144rows; font row
lookup is linear. Not Doom benchmark. GPT assumes26ticks/us.
MCU B621 differs from reference/classifier B620 bybit0: NOT decoded; neither
26MHz nor260MHz proved. Do NOT write PLL/EMI/PMIC/voltage/speculative routes.
No physical operation, firmware/writer edit or new flash authorization.
NOR remains last full-readback verified c1597dd2...cf075 (20:40:51+05).
Writer spent; no rerun/auto-repin. Next external60s SEC check + isolated
CPU/PSRAM/render microbench offline. Audio/vib/SD still absent.
Report: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_clock_v2_runtime_20261118_205059_149824\REPORT_RU.md`.
Older runtime-not-yet sections below are history; do not rewrite sealed evidence.

## CLK DIAG V2: CLK DIAG V2 записана и полностью проверена — 2026-11-18T20:41:00.443806+05:00

Ровно одна физическая запись завершилась `verified_without_reset`.
Независимый аудит сохранённых файлов подтвердил все **4 194 304 байта** NOR.

- Same-session fresh before SHA-256: `0ae74dc92ad51a33e48f2e78ba54c57b5c651f38f300027306d8f390a36dc1ec`.
- **Фактический полный readback** SHA-256: `c1597dd261cdecff1f419b776eaeb37f8ba559856859c7b56031868895acf075`.
- Patch SHA-256: `2f4b342c3c598c434c23dc32092319fd0a2fead3c0d5ee2792084a8190498fb0`.
- Перед записью проверены геометрия и полный свежий NOR в той же сессии.
- Изменились только секторы **11, 12, 13**; сектор 14 остался FF.
- Протокол передал все четыре пакета, один D5, четыре подтверждения ACK.
- Все байты вне [0xB000,0xF000) совпадают со свежим before этой сессии.
- Все ELF PT_LOAD совпадают с аппаратным readback.
- Ошибок USB и control transfers нет; FINISH/reset/retry/reconnect не выполнялись.

## Следующая ручная проверка

Отключить USB, установить батарею и включить обычной кнопкой **без STAR**.
Дождаться `CLK DIAG V2`; через 30–60 секунд прислать фото всего экрана,
особенно BOOT/NOW для MCU, MPLL, DIV и DRAW/DMAX/DMA/XMAX US.
Запуск и показания V2 на реальном экране пока не наблюдались.

Report: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_clock_diag_written_20261118_204100\REPORT_RU.md`.
Разрешение израсходовано. Writer остаётся с прежней spent базой; НЕ rerun/auto-repin.
Audio/vib/SD отсутствуют; CPU MHz не измерены, PLL/EMI/PMIC не менялись.
Предыдущие prepared/offline состояния ниже — история.

## CLK DIAG V2: разрешена одна запись — 2026-11-18T20:40:04.821791+05:00

Пользователь: «записывай эту хуйню». Ровно одна WriteFourSectors для V2.
Trial: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\clock_diag_trial_20261118_203448_253957`. Base `0ae74dc92ad51a33e48f2e78ba54c57b5c651f38f300027306d8f390a36dc1ec`.
Patch `2f4b342c3c598c434c23dc32092319fd0a2fead3c0d5ee2792084a8190498fb0`; expected NOR `c1597dd261cdecff1f419b776eaeb37f8ba559856859c7b56031868895acf075` пока НЕ readback.
Firmware native26+clock10; writer110+native17 PASS OFFLINE. Протокол/USB/DA
и диапазон [0xB000,0xF000) не менялись; только pins/assets/fixtures/base path.
До USB нужен DryRun; после этого один нормальный BootROM/original DA заход.
Same-session geometry + fresh4MiB перед D3/D5, full4MiB after + outer/ELF audit.
Ни UseExistingDA, ни FINISH/reset/retry/reconnect/clear-halt/rollback. STOP при ошибке.
Не изменять PLL/EMI/PMIC/напряжения. Audio/vib/SD отсутствуют. Пока установлен
V1 с проверенным NOR0ae74dc9...dc1ec, не объявлять V2 установленным заранее.
Предыдущие статусы ниже — история; новый результат добавить сверху.

## CLK DIAG V2 ready OFFLINE, NOT FLASHED — 2026-11-18T20:25:27.174447+05:00

User "Давай делай": prepared separate candidate, no hardware/flash action.
Candidate C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\clock_diag_20261118_201717_105722; source-only production diff src/main.c.
BOOT/NOW MCU A0010108, MPLL A0170100/divA0170104 read-only; DRAW/DMAX US
CPU framebuffer preparation timed separately from existing DMA/XMAX US.
No CPU MHz assertion. US assume GPT26MHz; DRAW one completed frame late.
DMA includes polling latency; UI workload differs from V1, not speed proof.
Image11592 bytes. C99/packaging11/native26+new10/heap+BL2/GFH/ELF PASS OFFLINE.
Installed remains CORE DIAG V1, actual NOR0ae74dc9...dc1ec, runtime photo PASS.
Writer untouched old-base spent pinned. DO NOT run/repin or flash new image
without NEW explicit version-specific write confirmation and physical readiness.
Original same-session geometry/fresh before/full after/outer gates required;
no retries/reset/FINISH/reconnect/clear-halt/rollback. Audio/SD/vib absent.
Report: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_clock_diag_v2_20261118_201717\REPORT_RU.md`.


## Runtime photo observed; CPU frequency UNKNOWN — 2026-11-18T20:12:01.362664+05:00

User photo: CORE DIAG V1, RAM4096K OK, HEAP GUARDS OK, RAM_MS11698,
HEAP_K4047, SEC475, FRAMES2797, FPS5, DMA_MS21/MAX21, P0/R0, RAW all0.
Boot/main screen and firmware full-RAM selftest PASS now photo-confirmed.
475 is SOFTWARE timer seconds, not independent external duration; a still
does not establish continuous movement or held/released key function.
GPT26M is a STATIC LABEL, NOT a CPU measurement. Boot snapshots read MCU
A0010108, MPLL A0170100/divA0170104, but screen does NOT show these.
Reached LCD init implies stored MPLL1401/div0 passed code preconditions;
this does NOT prove CPU source/divider/PLL-lock or actual 260MHz.
User asks about CPU26 vs260. Do not assume either or change PLL blindly.
Next useful offline diagnostic: raw MCU/MPLL/div + CPU rendering time apart
from DMA. FPS5 alone does not prove CPU26 or predict Doom FPS.
No USB/NOR/reset/power/driver/source changes this observation. NOR still
verified 0ae74dc9...dc1ec; writer stays spent old-base pinned, do not rerun.
Audio/vibration/microSD still absent. Report: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_runtime_clock_observation_20261118_201201_362664\REPORT_RU.md`.


## CURRENT NOR VERIFIED — separate READ-ONLY recovery, 2026-11-18 19:51:46 +05:00

Human "готов в другом порту": ONE InitializeOnly WITHOUT UseExistingDA
completed 4194304-byte acquisition via stock BootROM/original DA in RAM.
Independent DISK audit PASS: every byte exact expected CORE DIAG overlay;
actual full NOR SHA256 0ae74dc92ad51a33e48f2e78ba54c57b5c651f38f300027306d8f390a36dc1ec.
Only blocks11-14 differ from WRITE-session fresh_before; protected prefix
and suffix + all ELF PT_LOAD bytes verified. 6509 USB rc0, no control transfers.
Recovery did NOT program/erase NOR or reset/FINISH/retry/reconnect/clear-halt.
Raw InitializeOnly intentionally stopped AFTER persistence on OLD-BASE guard.
Do not rewrite raw result or call original write verified_without_reset.
Verification is a separate later full read, now authoritative; older UNKNOWN
headers below and sealed writer status pages are HISTORICAL, not current.
Writer remains old-base pinned; do NOT rerun/auto-repin or flash again.
Next: human unplug USB, insert/reseat battery, normal power-on WITHOUT STAR;
request CORE DIAG V1 / RAM4096K OK / HEAP GUARDS OK photo, then 5-10min
animation, external60sec vs SEC and held/released RAW KEYS checks.
Runtime not yet observed. Audio/vibration/microSD still NOT implemented/tested.
No speculative PMIC/PLL/EMI/SD/audio/vibration changes.
Report: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_critical_diag_verified_20261118_195146\REPORT_RU.md`.


## NEW READ-ONLY BootROM recovery — 2026-11-18T19:51:11.021839+05:00

User "готов в другом порту" confirms manual reconnect in another port without battery/buttons.
ONE InitializeOnly attempt WITHOUT UseExistingDA is now authorized. Original
stock DA upload to RAM allowed; no DA NOR D3/D5, reset, FINISH, retry, clear-halt,
automatic reconnect, rollback or repin. NOR remains UNKNOWN pending full audit.
A complete acquisition may intentionally fail old-base guard AFTER persistence;
audit against exact expected overlay, prior write fresh_before and ELF PT_LOAD.
Attempt: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\critical_diag_readonly_newport_20261118_195111_021839`. Earlier authorization/status sections are historical.


## Latest READ-ONLY recovery STOP — 2026-11-18 19:46:55 +05:00

User "Готов" authorized ONE InitializeOnly WITHOUT UseExistingDA after manual
reconnect. Runner stopped at open_once: MediaTek0E8D:0003 found0. No bulk
transfer, no DA upload, no NOR read/write, reset, FINISH, retry or auto reconnect.
Later OS-only PnP queries listed VID0E8D/PID0003 OK/WinUSB/oem51.inf, but a
separate IsPresent property was false. Do not infer stable presence or DA mode.
No driver changes or transport fallback. NOR remains UNKNOWN after prior D5.
This authorization consumed. Need NEW human connection/readiness before any
next physical attempt. User may reconnect without battery/buttons directly to
another USB port; do not boot normally yet. Next attempt remains read-only
InitializeOnly without UseExistingDA; original DA RAM upload only, no NOR write.
Keep old base pins. A saved complete D6 may fail the old-base guard: audit the
exact overlay and protected bytes/ELF independently; no automatic repin/retry.
Report: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_critical_diag_readonly_no_device_20261118_194655\REPORT_RU.md`. Earlier statuses below are historical.


## NEW READ-ONLY BootROM recovery — 2026-11-18T19:46:36.421174+05:00

User "Готов" confirms requested manual reconnect without battery/buttons.
ONE InitializeOnly attempt WITHOUT UseExistingDA is now authorized. Original
stock DA upload to RAM allowed; no DA NOR D3/D5, reset, FINISH, retry, clear-halt,
automatic reconnect, rollback or repin. NOR remains UNKNOWN pending full audit.
A complete acquisition may intentionally fail old-base guard AFTER persistence;
audit against exact expected overlay, prior write fresh_before and ELF PT_LOAD.
Attempt: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\critical_diag_readonly_bootrom_20261118_194636_421174`. Earlier authorization/status sections are historical.


## Latest READ-ONLY recovery STOP — 2026-11-18 19:43:16 +05:00

ONE authorized InitializeOnly + UseExistingDA invocation stopped at first B0
geometry response b101010101, expected 000000005a. No D6 acquisition; 0 NOR bytes.
No D3/D5/write/DA upload/reset/FINISH/retry/clear-halt/reconnect. Six bulk USB
transfers all rc=0: PROTOCOL mismatch, not a new USB transport error.
Prior post-D5 NOR remains UNKNOWN. Do not boot from battery or assert installed
image/protected bytes. This read-only authorization consumed; no auto retries.
User action needed: unplug USB, remove battery if present, reconnect WITHOUT
battery/buttons, confirm ready. ONLY after readiness: a NEW read-only attempt
via normal BootROM/original DA RAM path, InitializeOnly WITHOUT UseExistingDA.
Keep old base pins unchanged. Persist full acquisition even if old-base guard
then rejects; audit exact overlay and outer bytes vs write-session fresh_before.
No new write or speculative audio/vibration/SD power changes.
Report: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_critical_diag_readonly_stopped_20261118_194316\REPORT_RU.md`.


## READ-ONLY recovery authorization — 2026-11-18T19:42:50.829137+05:00

User "Разрешаю всё" responded to a separate READ-ONLY verification request.
Exactly ONE existing runner InitializeOnly + UseExistingDA invocation is prepared.
No D3/D5, BootROM upload, reset, FINISH, retry, clear-halt, reconnect or repin.
NOR still UNKNOWN until complete independent 4-MiB audit. Prior warnings below
remain historical evidence; this is NOT a new write authorization.
Attempt evidence: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\critical_diag_readonly_20261118_194250_829137`.


## ВНИМАНИЕ: после D5 фактический NOR НЕ проверен целиком

Четыре пакета получили ACK, но D6 прерван USB rc=-9 на 914/1024 блоках.
Нет full_after.bin: старый 070715... — свежий ДО этой записи, ожидаемый
0ae74d... — НЕ измеренный readback. Текущее содержимое NOR НЕИЗВЕСТНО.
Сохранять USB/питание; холодный старт пока не рекомендовать. Разовая проба
израсходована: без retry/reset/FINISH/reconnect/clear-halt/rollback или auto-repin.
Нужно отдельное разрешение на read-only контроль, а НЕ повторную запись.

## Последний физический результат диагностики — 18.11.2026 19:33:36 +05:00

ОСТАНОВЛЕНО: mandatory_full_readback_before_reset; USB read error rc=-9, actual=0; no retry.
NOR write attempted=True. Новая запись не подтверждена.
Отчёт: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_critical_diag_stopped_20261118_193336\REPORT_RU.md`.
Разрешение израсходовано. Без повторов/reset/FINISH/reconnect/rollback и auto-repin.
Аудио/вибро/SD не реализованы; их физические тесты НЕ выполнялись.
Исторические prepared/not-written статусы ниже не заменяют этот результат.

## Новая одна разрешённая проба диагностики — 18 ноября 2026

Пользователь разрешил: «Разрешаю ... Щас записывай». Ровно одна запись уже
подготовленной RAM/LCD/GPT/raw-key/heap guard диагностики. Аудио/вибро/SD
в ней НЕ реализованы; разрешение не даёт права угадывать их питание/регистры.
Trial: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\critical_diag_trial_20261118_192430`. Patch `f6bc3d0c8d51052aac2da5f97b65c748ec2808b7ae094cc26a20db4b6b1a2b06`.
Base `070715772e33c457fde486b0a3399786cee21816b96b098cebce91dfdf202a46`; expected `0ae74dc92ad51a33e48f2e78ba54c57b5c651f38f300027306d8f390a36dc1ec` пока НЕ установлен.
Firmware26, writer108+native17 PASS офлайн. Existing writer намеренно закреплён
на новые bytes ДО USB по новому запросу; протокол и диапазон не менялись.
Физического результата ещё нет. Fresh4MiB+geometry до D3/D5, full readback и
outer audit после. Без FINISH/reset/retry/reconnect/rollback; STOP при ошибке.

## Офлайн-диагностика готова, НЕ записана — 18 ноября 2026

Каталог: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\work\critical_diag_20261118_190825`.
Отчёт/выдача: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_critical_diag_20261118`.
26 native/model + 11 packaging + heap ASSERT controls + оригинальный BL2/GFH PASS.
Это НЕ аппаратный тест. При старте проверяются все 4 МиБ ДО runtime; затем
длительный экран/GPT/raw-key тест и два heap guard. SD/звук ещё не готовы.
Patch SHA-256 `f6bc3d0c8d51052aac2da5f97b65c748ec2808b7ae094cc26a20db4b6b1a2b06` НЕ установлен и НЕ разрешён к записи.
Рабочий keypad-образ и writer сохранены, USB/NOR/reset не выполнялись.
Для физической проверки необходимо НОВОЕ отдельное разрешение. Старый writer
израсходованную базу не менял: не повторять и не перепривязывать автоматически.
Все прежние ограничения диапазона и fresh before/full readback сохраняются.

## Подтверждение пользователя и приоритет проверок — 18 ноября 2026

Пользователь сообщил: «Управление с помощью крестовины работает образцово,
всё отлично!!!». Игровой запуск и управление теперь подтверждены пользователем.
Длительность, независимые FPS/частота таймера, полная RAM и отдельный bit ↑
при этом НЕ измерены. Прежние слова «runtime ещё не наблюдался» ниже — история.
Doom отложен по новому запросу: сначала критичные проверки платформы.
Установленный NOR остаётся 070715772e33c457fde486b0a3399786cee21816b96b098cebce91dfdf202a46.
Этот запрос НЕ разрешает новую запись. USB/NOR/reset не выполнялись;
writer не перепривязан, прежняя разовая flash permission израсходована.
Готовится отдельная офлайн-диагностика; установленный исходник не изменяется.
Полный RAM-тест допустим только до копирования vectors/data и очистки BSS,
из NOR на TCM-стеке. В игре его запускать нельзя. microSD/FAT32/audio ещё
не реализованы в текущей автономной прошивке. Старые отчёты не переписывать.

## Исправленная раскладка ЗАПИСАНА — 18 ноября 2026, 18:51 +05:00

После нового подтверждения «готов» и ручного переподключения выполнен один
новый заход. Сессия `C:\Users\USER\Documents\Codex\2026-11-16\senior-embedded-c99-developer-reverse-engineer\work\stock_da_trial_20261117\sessions\attempt_20261118_185043_391805`.
verified_without_reset + независимый disk audit PASS. Свежие full4MiB до записи
2d9f37c4a3507beb1dfde876f6cf88dff538f6ab7e91a444abb4e9b905bca2f3 и live geometry совпали; после full4MiB readback
070715772e33c457fde486b0a3399786cee21816b96b098cebce91dfdf202a46 побайтно равен точному overlay. Изменены только
блоки11–14; загрузчики/все внешние байты равны СВЕЖЕМУ before той же сессии.
Одна D5/четыре пакета; USB ошибок/F0/CDC/FINISH/reset/повторов/reconnect/
clear-halt/rollback НЕ было. Это успешная запись, пока НЕ тест холодного старта.

Установленный проект `C:\Users\USER\Documents\Codex\2026-11-16\senior-embedded-c99-developer-reverse-engineer\work\lcd_fps_20261117\keymap_photo_fix_20261118_183218\project`.
Patch 21fe2c57216da8a7b923e0f48e779287beed13c1011d4cb8ceb4ca8c0ae60b92; ELF 218943ed8552eac1d597a0149f0823c75e256a47d88d73519053c18f7dd1faf3.
←21/→30/OK42/↓15/2bit0/леваясофт33 = LEFT/RIGHT/TURN/DOWN/DROP/PAUSE;
дополнительно 8bit9=TURN,7bit6=DOWN,зелёная24=PAUSE. STAR при старте bit3.
На фото RIGHT/UP совпали30: UP пока тоже может быть вправо, полной уникальной
аппаратной карты нет. Красная не назначена. Production менялись только
input.c/main.c; PLL/EMI/PMIC/LCD/backlight и игровой цикл прежние.

Теперь вручную отключить USB, установить батарею, включить обычно БЕЗ *.
Проверить экран/движение/←→OK↓/2/паузу, отдельно ↑. Новый runtime/FPS/кнопки
на железе ещё НЕ наблюдались. Native keymap79/combinations64/learned79/boot3,
repeat45/one-backlight и прочая кампания PASS; writer106+native17/DryRun PASS.
Разрешение этой пробы израсходовано. Writer base2d9f...bca2f3 теперь SPENT;
НЕ повторять WriteFourSectors и НЕ перепривязывать автоматически к новому NOR.
Для любой новой записи отдельное разрешение и прежние проверки; границы
по-прежнему [0x00B000,0x00F000). Старые found0/NOT_WRITTEN отчёты ниже — история.
Актуальный отчёт `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_keymap_written_20261118_185104\REPORT_RU.md`.

## Новая раскладка собрана, но запись остановлена ДО USB — 18 ноября 18:44

Пользователь попросил: «Попробуй лучше запиши прошивку, будем на практике проверять».
Создана отдельная копия `C:\Users\USER\Documents\Codex\2026-11-16\senior-embedded-c99-developer-reverse-engineer\work\lcd_fps_20261117\keymap_photo_fix_20261118_183218`.
Defaults LEFT21/RIGHT30/TURN42/DOWN15/DROP0/PAUSE33, aliases9/6/24,
STAR boot bit3. Совпадение RIGHT/UP30 не решено; UP может двигать вправо.
Красная трубка не назначена. Другие production/peripheral настройки прежние.
C99/packaging11/heap+/negative/game304597/PSRAM/GFH/panels/RTC/repeat45 PASS;
keymap79/combinations64/learned79/boot-STAR3cases PASS; writer106+native17,
DryRun PASS. Это не новые аппаратные измерения.

Один разрешённый запуск существующего writer WriteFourSectors (без FINISH/
UseExistingDA) остановился open_once: Need exactly one MediaTek0E8D:0003,
found0. DA не загружался, transaction not_started, NOR write flag=false,
reads={}, fresh_before/full_after не получены. Стирания/записи не было.
Автоматических повторов/reset/reconnect/clear-halt/rollback НЕ было.
Сессия: `C:\Users\USER\Documents\Codex\2026-11-16\senior-embedded-c99-developer-reverse-engineer\work\stock_da_trial_20261117\sessions\attempt_20261118_184428_696059`.
PnP Windows видит запись устройства, WinUSB/oem51.inf; libusb writer её не
нашёл. Причина не установлена, драйверы не менялись. Это не отказ NOR.

Новый patch21fe2c...ae60b92 и expected NOR070715...02a46 НЕ УСТАНОВЛЕНЫ.
Последняя известная установленная сборка — game_once_backlight_20261118_162900,
NOR2d9f37...bca2f3 — старый readback, НЕ новое чтение. Writer pins подготовлены
намеренно до новой пробы по новому запросу; протокол/защиты не ослаблены.
Эта одна попытка остановлена и не подлежит автоматическому повтору.
Для отдельного нового захода: вручную отключить USB, снять батарею, подключить
без батареи и кнопок, подтвердить готовность в чате. Не обходить discovery.
Границы остаются [0x00B000,0x00F000), fresh full4MiB+geometry до D3/D5,
full bytewise readback/outer ranges после. Отчёт: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_keymap_trial_20261118\REPORT_RU.md`.

## Оставшиеся кнопки: фото по номерам файлов — 18 ноября 2026

Новый пакет уточняет/заменяет старые неопределённости ниже. Пользователь
задал соответствие номерами photo_N, а не порядком вложений.
→(фото1) и ↑(фото2) одинаковы: 0000 4000 0000 0000 0000 = bit30.
Различить их по этим снимкам нельзя; причина совпадения не установлена.
RIGHT30 раньше был синтетическим fixture; новая подпись появилась, но дубликат
UP запрещает объявлять всю карту полностью подтверждённой/уникальной.
Правая софт=39; 1=27; 3=51; 4=12; 5=13; 6=57; 9=48; 0=45; *=3; #=54.
Красная трубка(фото4): все нули; физический бит не определён. Не доказывает
неисправность/отсутствие иного пути ввода и не подтверждает старый кандидат72.
STAR=bit3, а установленный boot shortcut проверяет bit2 через raw[0]&4u.
Статически фото-маска STAR не включает learner; холодный запуск не проверяли.
DOWN15/LEFT21/OK42 остаются из прошлых подписанных фото. 2=0,7=6,8=9,
левая софт33/зелёная24 по-прежнему основаны на прежнем видео+user report.
Native установленного ELF: 79 idle/single-bit PASS, комбинации/reserved PASS,
13 новых фото-масок PASS; все13 дают NONE в текущих defaults. Это не новое
измерение железа. Прочитаны/хешированы оригиналы; отчёт с LCD-обрезками:
`C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_keypad_remaining_20261118\REPORT_RU.md`.

Полную серию повторять не надо: уточнить → и ↑ раздельно с отпусканием,
красную трубку кратко при видимом экране (не длинное удержание питания).
Новой сборки/firmware edits/NOR read/write/writer/USB/DA/physical sessions НЕТ.
Прошлые manifests223/98/4/4 проверены без исправления. Последний NOR hash
2d9f37...bca2f3 — исторический readback, НЕ свежее чтение. Нового разрешения
на запись нет; прежнее разовое израсходовано, защиту writer не менять.
Будущий допустимый NOR-интервал остаётся [0x00B000,0x00F000) и не расширен.

## Новые подписанные фото: вниз, влево, OK, idle — 18 ноября 2026

Порядок явно задан пользователем; прочитаны оригиналы 1920x2560.
Вниз: 8000 0000 0000 0000 0000 = bit15; влево: 0000 0020 0000 0000 0000
= bit21; OK: 0000 0000 0400 0000 0000 = bit42; idle все нули.
Точный установленный ELF даёт соответственно LEFT/NONE/NONE/NONE.
Это разрешает прежнюю неопределённость трёх кнопок. В частности, кандидат
bit42=RIGHT из видео ОТВЕРГНУТ, bit21=OK тоже ОТВЕРГНУТ.
bit15 теперь подтверждён НОВЫМ фото, старые OCR-гипотезы не стали надёжнее.

Для каждой из этих трёх кнопок на снимке один контакт; это не утверждение
об остальных клавишах и переходах. RIGHT/UP физически пока неизвестны.
Следующий минимальный сбор данных — только фото вправо; DROP можно оставить
на наблюдавшейся 2. План LEFT21,RIGHT?,TURN42,DOWN15,DROP0,PAUSE33.
Native текущий79 + четыре фото-маски PASS; RAM learner после шести назначений
79/79 PASS, но RIGHT30 в нём строго синтетический fixture, не физическая карта.
Никаких новых firmware/writer/USB операций или flash permission.
Отчёт: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_keypad_photos_20261118\REPORT_RU.md`.

## Продолжение в другом чате, 18 ноября 2026 — разбор видео

Видео 16-46-21 разобрано частично и проверено на точном установленном ELF.
Подтверждённая совокупностью прежнего user report и видео раскладка:
2=bit0/DROP, 7=bit6/DOWN, 8=bit9/TURN; левая софт=bit33/PAUSE,
зелёная=bit24/PAUSE. Экранные маски и кадры — в новом отчёте.
Физические LEFT/DOWN/OK ещё не установлены достаточно надёжно для прошивки.
Читаемые дополнительные bits21/30/42/72/12/13/45/57/48/54 не имеют действий
в установленном matrix_poll; их физические подписи пока только кандидаты.
В размытых кадрах decoder путает 0/8/B: bit15/bit51 из его отдельных
гипотез НЕ считать новым аппаратным подтверждением. Нулевой кадр НЕ доказывает
отказ сканирования; multibit contacts НЕ исключены.

Native точного ELF: 79/79 idle+single-bit, комбинации и reserved bits PASS;
ELF load segments совпали с историческим readback 2d9f37...bca2f3.
Heap из ELF 4144576, не новое измерение физической RAM. MS HUD не включает
CPU ui_game до frame_start; частоту ARM/FPS аппаратно не измеряли.
USB/firmware/writer/physical sessions НЕ изменялись, новой flash permission НЕТ.
Следующий сбор данных: чёткие фото KEYS для ←, ↓, OK и idle без перепрошивки.
Отчёт: `C:\Users\USER\Documents\Codex\2026-11-18\new-chat\outputs\kenshi_keypad_20261118\REPORT_RU.md`.

## Аппаратное наблюдение: игровой цикл и фактические кнопки, 18 ноября

Пользователь подтвердил сохранение изображения с повторными кадрами,
движение/управление деталями. Текущая игровая once-backlight сборка не гаснет
в рамках его наблюдения. Время наблюдения не измерено; это не длительный
стресс-тест. Нового чтения/записи NOR или USB операций в этом ходе НЕТ.

Фактические действия в установленной сборке (со слов пользователя):
| Физическая кнопка | Реальное действие |
| --- | --- |
| 8 | Поворот |
| 2 | Мгновенный сброс вниз |
| 7 | Ускорение падения |
| Крестовина вниз | Сдвиг влево |
| Верхняя левая софт-клавиша | Пауза |
| Зелёная «поднять трубку» | Пауза |

Прежние обещания «5=поворот,8=ускорение,4/6=сдвиг» НЕ считать физически
подтверждёнными. Цифровые подписи исходной таблицы/алиасы не соответствуют
наблюдаемой раскладке платы. Источник расхождения (таблица/режим сканирования/
контакты) ещё не установлен. Прошивать угаданные новые indices нельзя.
Native 79/79 idle+single-bit cases точного установленного matrix_poll:
LEFT={8,15}, RIGHT={22,41}, TURN={9,26,46,50}, DOWN={6,11}, DROP={0,28},
PAUSE={24,33,52}. Одно реальное действие не определяет уникальный matrix bit;
несколько замкнутых контактов при одной кнопке пока также не исключены.

Экранный FPS по сообщению пользователя 14–25; не внешнее измерение.
Текущий main задаёт программный интервал 33 ms (~30 FPS), НЕ цель60.
На dirty ui_game заново очищает/рисует полный framebuffer; keypad-изменения
также dirty. Вклад CPU-отрисовки vs DMA/шины пока не измерен, причина колебаний
не доказана. Полезно снять одновременно FPS и MS/!! на экране; не менять
PLL/EMI/cache/PMIC вслепую по этим цифрам, 260MHz не подтверждать.

Повторный game DMA теперь работает в наблюдаемой конфигурации. Избыточная
повторная ISINK/backlight init остаётся главным программным отличием от
старого погасающего game path, но причинность не доказана электрически;
добавленные read-only snapshots и layout/timing также нельзя игнорировать.

Следующий безопасный шаг без перепрошивки: заснять верхние KEYS hex-группы
при всех отпущенных кнопках, затем по одной LEFT, RIGHT, OK, DOWN, UP,
левая софт-клавиша; отпускать между нажатием, держать около секунды. Это
позволит восстановить точные masks/индексы и не угадывать исправление.
Существующий KEY SETUP допускает шесть обучаемых одиночных bit-keys, только
RAM. Вход сейчас проверяет raw MEM1 bit2 (комментарий STAR); физическая «*»
для входа НЕ подтверждена. Поэтому не обещать работающий STAR shortcut,
а при multi-bit контакте существующий learner может отвергать кнопку.

Firmware/writer pins/physical sessions не изменялись; текущий NOR остаётся
последним известным 2d9f37...bca2f3. Новая запись не выполнялась/не разрешалась.

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

## Аппаратное наблюдение пользователя, 18 ноября 2026

Установленная first-frame hold сборка: пользователь сообщил «Счётчик А идет,
изображение не пропадает, анимации нет, управления нет» и прислал фотографию.
На фото видны игровой кадр и PIO hex-столбец. Движение счётчика и сохранение
изображения — сообщение пользователя; один фотокадр сам по себе не измеряет
динамику/длительность. Время наблюдения, FPS и MCU Hz не измерены.

Это ожидаемый режим first_frame_hold, НЕ новая неисправность управления:
CPU продолжает опрос KPAD и PIO heartbeat, но не вызывает tetris_tick /
matrix_poll / ui_game и не запускает следующие игровые DMA. KEYS/FPS/MS/BOOT
в основном игровом кадре заморожены и не являются живой телеметрией.
Стабильная картинка и advancing heartbeat подтверждены в рамках наблюдения
пользователя, не как длительный стресс-тест или независимая проверка PMIC.

В этой сборке одновременно убраны повторная настройка подсветки и следующие
DMA. Причинность НЕ разделена: нельзя объявить виновным только ISINK или
только DMA, а WDT/питание полностью исключёнными.
Следующая ограниченная проба: вернуть игровой цикл, обработку матрицы и
повторные кадры, СОХРАНИВ ровно одно раннее включение подсветки; PLL/PMIC
и другие периферийные функции не менять. Физическая раскладка кнопок всё
ещё не подтверждена, даже после возврата обработки потребует проверки.
Новых firmware bytes/USB operations/writer repin в этом ходе нет.
Старая авторизация consumed, новый физический опыт требует согласия.

## Актуальное состояние: 18 ноября, 16:21 +05:00

Один разрешённый диагностический first-frame hold ЗАПИСАН.
Сессия: `work/stock_da_trial_20261117/sessions/attempt_20261118_162050_279542`.
Проект: `work/lcd_fps_20261117/first_frame_hold_20261118_161300/project`.
Свежая same-session база: `e08f0b8383d7d87a2f94f3284432c3a8031981eef952325feda04fb53140fb07`.
Patch: `b900b87de89bfda704516a890e71d2e7d8d50bc7bca75f3d166f92c35f15aaf6`.
Полный NOR/readback: `7b312161b8fccf69eade0a24db8a5e9eb95724cd9f53c3ca5d82d752ada2f736`.
Геометрия и fresh 4 MiB совпали; полный readback побайтно и независимым
аудитом подтверждён. Изменены только сектора 11–14. Защищённые внешние
диапазоны равны свежему before; хвост не «ремонтировали» относительно эталона.
Одна D5, четыре подтверждённых блока. USB ошибок, CDC/F0, FINISH/reset,
повторов/clear-halt/reconnect/автоотката не было. После записи пользователь подтвердил advancing A-counter и сохранение
изображения. Длительность наблюдения не измерена, причина старого погасания
ещё не установлена.

### Что смотреть на экране
- B001/B002 — нормальные стартовые метки.
- После первого игрового кадра картинка Тетриса НАМЕРЕННО замирает.
- A001,A002,... — маленький PIO heartbeat продолжающего работу CPU;
  последующих игровых DMA и повторного включения подсветки нет.
- Девять hex-строк ниже: WDT_MODE, WDT_STA, RTC_BBPU, KEY1, KEY2,
  TEST_CON0, CHR_CON9, ISINK0, ISINK1. Это не коды ошибок.
- Маппинг клавиш не менялся, физическая раскладка всё ещё не подтверждена.
- Холодная проверка: отключить USB, снять/вернуть батарею, включить кнопкой;
  снять видео 10–15 секунд, зафиксировать счётчик или точку погасания.

103 writer offline + 17 native cases, DryRun и native hold проверены;
MMIO fixtures не эмулируют реальное питание/PMIC/WDT reset/FPS.
Разрешение на ОДНУ пробу использовано. Runner base e08f...40fb07 теперь
ИЗРАСХОДОВАНА: НЕ повторять WriteFourSectors и не перепривязывать автоматически.
Новый образ/reset/rollback требуют применимого нового разрешения.
Нижние разделы — исторические состояния, данный раздел имеет приоритет.

Обновлено: 18 ноября 2026 года, после записи 16:20:50–16:21:10 (UTC+05:00)
и сообщения пользователя о стабильном first-frame hold. Это рабочая инструкция для данного телефона,
а не универсальная инструкция для всех MT6261. Исторические отчёты в outputs
могут описывать уже заменённые образы; текущий статус указан здесь.

## Новое: офлайн-карта периферии и аудит первого кадра (18 ноября)

Телефон/NOR/firmware/writer в этом проходе НЕ менялись. Новая физическая
авторизация отсутствует. Последний известный readback остаётся e08f0b...40fb07;
это не свежий дамп устройства.

- Повторный board_backlight_init после frame_count=1 подтверждён исполнением
  точного установленного ELF: два входа, 14 ISINK writes. Это избыточная
  настройка, НЕ установленная причина реального погасания. Видеозапись не
  доказывает достижения второго вызова/завершения полного DMA на телефоне.
- Нативная проверка board_keypad_read: idle + все 78 бит, 79/79; читаются
  пять LDRH вплоть до A00D0014. Физический mapping кнопок ещё не подтверждён.
- Оригинальный PMU setter 1003635D: 1248/1248 модельных RMW-cases на явно
  подставленных VIBR/VMC bases/fields. ROM rail index8/id11 -> A07001B0;
  index9/id12 -> A07001C0. Напряжение/разводка мотора и SD power-up неизвестны.
- Родной setter использует veneers в TCM 70008685/700086C1; в bare-metal
  проекте здесь ARM-стеки. НЕЛЬЗЯ просто вызывать его как готовый HAL API.
- 1003066C — строка audio_service.c, не DAC-init. AFE/ABB/SPK reference map
  восстановлен отдельно от неподтверждённого PCM/DSP потока. Не выключать
  весь modem-address-range clock domain: reference audio использует VAFE.
- Старый Step2-дамп SHA9109aa... и эталон SHA44f7... совпадают на [0,389000).
  Их полный SHA различен из-за хвоста; ни один локальный файл не заменяет
  свежий same-session read перед новой записью.
- У последней записи наружные байты совпадают с её fresh_before. Системный
  хвост НЕ равен целиком старому эталону: отличия уже были во fresh_before;
  последняя запись их не меняла. Bootloaders [0,B000) и код [F000,389000)
  совпадают с эталоном. Не утверждать глобального равенства хвоста эталону.

Единый отчёт: C:\Users\USER\Documents\Codex\2026-11-16\senior-embedded-c99-developer-reverse-engineer\work\peripheral_audit_20261118\REPORT_RU.md.
Машинная карта: C:\Users\USER\Documents\Codex\2026-11-16\senior-embedded-c99-developer-reverse-engineer\work\peripheral_audit_20261118\hardware_map.json.
Никаких измеренных hardware FPS/напряжений/источника reset пока нет.
Новый firmware candidate в этом проходе не создан; запись не запускать.

## 1. Подтверждённое состояние

## Новое: надписи прочитаны по правильному видео 15:32:59

Покадрово видны B001 → B002 → игровое содержимое → погасание.
B001/B002 — нормальные метки, не ошибки. KEYS/CPU?/LINES/SCORE/NEXT и нули
соответствуют ui_metrics/ui_game. E0C-код в проверенных кадрах НЕ найден;
предыдущее пользовательское «ошибки» теперь не считать расшифрованным кодом.
CPU? означает только нераспознанную классификацию частоты в нашем UI.
Первые игровые элементы около 18,033 с файла, темно с 18,367 с; это временные
позиции ролика, не измерение реальных задержек или FPS/полного DMA.
Причина погасания/необходимости снять батарею ещё неизвестна. Повторный вызов
backlight init после первого распознанного завершения кадра есть в main,
но факт достижения этого вызова и его причинность пока не подтверждены.
Отчёт: work/power_failure_20261118/video_153259/REPORT_RU.md.
Видео/исходники анализировались офлайн, USB/firmware/writer pins не менялись.


## Уточнение пользователя: кнопка не влияет, нужен съём батареи

18 ноября 2026: экран гаснет и при удерживаемой, и при отпущенной кнопке.
Следующий запуск возможен только после извлечения и повторной установки батареи.
Это исключает прежнюю простую гипотезу «гаснет только при отпускании кнопки»,
но не различает аппаратный reset, исчезновение питания и зависание с погасшим LCD.
Код ошибки не прочитан; надписи пользователя не считать декодированным E0C5.

### Что действительно проверено офлайн
- Точный установленный ELF: нормальные три кадра в синтетической модели.
- После первого модельного кадра: зависание следующей передачи и отдельно
  пропущенное событие завершения приводят к C5. Это искусственные контрпримеры,
  а не установленная причина сбоя телефона.
- После C5 обработчик рисует диагностику и выполняет 10000 инструкций halt
  без новых MMIO-записей; backlight/RTC hold в модели остаются включёнными.
- Единственная запись WDT в этих путях: 16-битная 0x2200 в 0xA0030000 при старте.
  Родной код 0x1001BAB8..0x1001BAE6 в эталоне использует тот же ключ 0x2200
  и в ветви disable очищает EN/IRQ_EN. Команда disable выбрана не наугад;
  фактического hardware readback MODE/STATUS после отказа по-прежнему нет.
- board_power_hold выставляет BBPU|AUTO с родным ключом 0x430C. По локальному
  datasheet RTC_BBPU.AUTO допускает снятие BBWAKEUP при SYSRST. Поэтому «в нашем
  C нет power-off» НЕ исключает выключения вследствие аппаратного reset.
  Наличие самого SYSRST, его источник и напряжения питания НЕ измерены.

WDT/SYSRST/PMIC/brownout моделью не эмулируются. Реальные FPS не заявляются.
Нельзя объявлять ни watchdog, ни PMIC, ни LCD установленной причиной.
Не отключать AUTO/защиты и не менять PMU-напряжения вслепую. Бинарник и writer pins
не менялись; USB после предыдущей записи не использовался, новая запись запрещена.
Для следующего обоснованного шага нужен читаемый первый код (видеозапись запуска
с замедлением может дать его без новой прошивки) либо отдельно согласованный
диагностический образ со снимками WDT/RTC до попытки вывести сообщение.


# Текущее состояние: completion fix записан; кадр появился, затем экран погас

18 ноября 2026, запись 15:01:59–15:02:20 (Asia/Yekaterinburg), одна попытка.
Сессия: `work/stock_da_trial_20261117/sessions/attempt_20261118_150159_812773`.
Patch: `ce17f52a8d180b306f7137a8e68e6acaecd69243bd51fb3c3a8edc1b78c0b743`.
Свежая база: `9c49f41e37c6e3d13186e5909325ad5aa63650a8bd4f53d030d13110bc613200`.
Текущий NOR: `e08f0b8383d7d87a2f94f3284432c3a8031981eef952325feda04fb53140fb07`.
Полные 4-МиБ before/readback и independent bytewise audit прошли: только блоки
11–14, исходные загрузчики и все байты внешних диапазонов сохранены.
Никаких USB-ошибок/F0/CDC/FINISH/reset/повторов. Статус verified_without_reset.
102 offline writer tests + 17 native DA cases и DryRun прошли для этих pins.
Полная игровая/PSRAM/heap кампания заново НЕ выполнялась; реальный FPS не измерен.
Пользователь после старта: появляется Тетрис и нечитаемые ошибки меньше секунды,
затем телефон/экран гаснет и повторно не включается. Это пользовательское наблюдение;
физическое отключение питания против сброса/погасшей подсветки пока не различены.
Первый кадр сообщён, но стабильная игра НЕ подтверждена. Код ошибки неизвестен.
Разрешение одной записи использовано, база 9c49...13200 SPENT. Никакой новой
записи/автоотката/сброса/переподключения без отдельного согласования.

### История до completion fix

17 ноября 2026 в 22:47 по отдельному разрешению пользователя записан E0C1 fix.
Полный свежий NOR до/после и независимая побайтная проверка прошли.
Сессия: `work/stock_da_trial_20261117/sessions/attempt_20261117_224726_399606`.
Текущий полный NOR: `9c49f41e37c6e3d13186e5909325ad5aa63650a8bd4f53d030d13110bc613200`.
Patch: `1d8013659958355726dd02c0de3238eaf8d4617d84dd6e6b814f778e7de22eba`.
База до D3/D5: `20e600f8db8cad39b5620a2c8bb664a5dd1b105abfcea089bbbb47c1df5ecb65`.
Сохранены загрузчики и все байты вне [0xB000,0xF000), изменены только сектора 11–14.
USB-ошибок, F0/CDC/FINISH/reset/повторов нет. Это verified_without_reset, не запуск игры.
После холодного старта пользователь сообщил E0C5 и полностью ЧЁРНЫЙ фон.
Переписанные строки: B621 / 1410 / 0000 / 0000 / 0000 / 0000.
Сбой ожидания раннего LCD engine, ДО memory init; игра не запустилась.
Чёрный фон указывает на возможную выполненную заливку, но время/частота не измерены.
Проверяется потеря read-to-clear INTSTA и ожидание при masked IRQ; PLL не менять.
Разрешение одной записи израсходовано. Повтор/автооткат/автоподмена базы запрещены.

История: предыдущая изолирующая версия 20e600... давала B001->E0C1, шум за меткой;
пользователь оценил подсветку ~0,25 с, B001 ~0,75 с, E0C1 ~2,25 с. Это не скорость
рисования метки: интервал включает memory-init. Старые хеши ниже — история.

## 2. Неприкосновенные границы

Разрешены стирание и запись ТОЛЬКО [0x00B000, 0x00F000), ровно 16 384 байта,
четыре сектора по 4096 байт. Правая граница не включается.

НИКОГДА не изменять [0, 0x00B000) и [0x00F000, 0x400000).
Не выполнять format, full erase, операции с загрузчиками или автоматический откат.
Использовать только неизменённый оригинальный IoT DA; никакого обхода защиты.

## 3. Подключение для записи

1. Не запускать одновременно dump tool, SP Flash Tool, mtkclient и наш writer:
   USB-интерфейсом должен владеть только один процесс.
2. Для входа в использованный BootROM-режим отключить USB и питание телефона,
   снять батарею и вновь подключить USB к ПК. Ранее чтение выполнялось без
   зажатия клавиш; необходимости зажимать неизвестные комбинации не установлено.
3. VID:PID 0E8D:0003 сам по себе не доказывает фазу протокола. После холодного
   подключения нужен штатный BootROM-хандшейк и загрузка DA в RAM; нельзя
   посылать DA-команды непосредственно BootROM. Активность DA проверяется
   протоколом, а не одним именем USB-устройства.
4. Если DA остался активен после успешной сессии, режим UseExistingDA допустим
   только для действительно подтверждённой текущей сессии. Не угадывать состояние.
5. Любой STALL, тайм-аут, короткая передача или неожиданный ответ — немедленный
   stop. Не повторять автоматически, не делать clear-halt, reset или reconnect.
   Сохранить каталог сессии. Новый физический заход — отдельная осознанная проба.

## 4. Обязательный порядок bounded writer

- Сначала офлайн-проверка, проверка файлов/хешей и точного диапазона.
- В одной живой DA-сессии проверить геометрию и снять СВЕЖИЙ полный NOR 4 МиБ.
  Дамп на диске с известным хешем не заменяет свежую предпроверку устройства.
- Его SHA-256 должен точно совпасть с закреплённой базой текущего кандидата.
  При несовпадении остановиться ДО D3/D5; не добавлять новую базу автоматически.
- D3/D5 разрешены только внутри четырёх указанных секторов.
- Рабочий D5: packet_length=4096; маркер отдельно; данные 64 отдельных USB OUT
  по 64 байта; BE16 checksum отдельно; ожидание ACK69 с ограниченным тайм-аутом
  стирания 60 секунд. Не отправлять всё одним 4099-байтным USB transfer.
- Ни F0, ни CDC SET_LINE_CODING/SET_CONTROL_LINE_STATE для этого транспорта.
- После записи, ДО перезапуска: сохранить полный NOR 4 МиБ, сравнить побайтно
  с expected overlay, проверить полный SHA-256 и неизменность внешних областей.
- По принятой политике следующих проб НЕ посылать FINISH/reset автоматически.
  Холодный старт выполняется вручную только после `verified_without_reset`.
- НЕ повторять физический запуск текущего runner: база изолирующей сборки
  `20e600...ecb65` использована; текущий NOR `9c49f41e...613200`.
  Не подменять базу автоматически; старые runner тоже не применять.
  DryRun проверяет файлы на диске, НЕ состояние телефона.

## 5. Проверка запуска от батареи

После успешной полной верификации отключить USB, установить батарею и включить
телефон штатной кнопкой. Не принимать подсветку или белый экран за запуск игры.
Зафиксировать на видео: время до кадра, остаётся ли питание после отпускания
кнопки, изображение поля и реакцию на каждую управляющую клавишу.

## 6. Управление установленной изолирующей сборки

Сразу стандартная игра: влево/вправо — сдвиг, вниз — мягкое падение,
вверх — сброс, центральная OK — поворот (кандидаты матрицы ещё требуют
физической проверки). Цифровые дубли: 4/6 — сдвиг, 5 — поворот,
8 — мягкое падение, 2 — сброс, 0 — пауза. Для переназначения удержать «*»
при старте и следовать шести подсказкам, отпуская клавиши между назначениями.
Привязки только в RAM. Опрос KPAD_MEM1..5. Физическое соответствие кнопок
и работоспособность игрового цикла в этой сборке ещё не подтверждены.
PIO-метки: B001 — панель до memory init, B002 — память готова до LCD DMA.
E0C1 — ошибка memory init; E000|код — ошибка RAM probe.
Белая подсветка без B001 не определяет точную причину отказа.


### 6.1. Архив предыдущей медленной версии — Сейчас установлена возвращённая медленная версия

Ранний тест: красная/зелёная/синяя полосы и белая Т-фигура до полного RAM-теста.
Затем KEY SETUP: обязательно назначить LEFT, RIGHT, TURN, DOWN, DROP, PAUSE,
выбирая разные клавиши и отпуская каждую по RELEASE KEY. Только после шести
назначений начинается игра. Настройка хранится в RAM. При неизвестном LCD ID
сначала перебор профилей и подтверждение картинкой/клавишей. Это логика исходника,
не подтверждение работы каждой кнопки на телефоне. Опрос здесь только MEM1..4.
Цифровые дубли ускоренной версии здесь не заданы.

### 6.2. Архив: управление снятой ускоренной версии

- Влево/вправо: сдвиг; вниз: ускоренное падение; вверх: мгновенный сброс.
- Центр OK: поворот. Точное соответствие заводского CSK enum физической кнопке
  ещё не подтверждено: в коде включены три кандидата и цифровой дубль «5».
- Цифровые дубли: 4 — влево, 6 — вправо, 5 — поворот, 8 — вниз, 2 — сброс,
  0 — пауза. Кандидаты дополнительных аппаратных клавиш также дают паузу.
- Если штатная раскладка не подошла: удерживать «*» при старте новой версии,
  отпустить и назначить по экранным подсказкам LEFT, RIGHT, TURN, DOWN, DROP,
  PAUSE. Между назначениями отпускать клавишу. Привязка хранится только в RAM.
- Опрос читает все KPAD_MEM1..5. В MEM5 два старших бита зарезервированы.
- Новая версия должна показывать FPS, MS передачи, BOOT до завершения первого
  кадра, raw-маску клавиш и снимок регистров MCU/MPLL. Эти показатели получают
  смысл аппаратного результата только после реального запуска.

## 7. Где хранится работа

- Проект C99: `outputs/kenshi_tetris_bootfix_20261117/project`.
- Существующий bounded writer: `outputs/kenshi_stock_da_d3fix_20261117`.
- Текущие материалы ускорения: `work/lcd_fps_20261117`.
- Снимок ДО правок ускорения:
  `work/lcd_fps_20261117/before_204747_185230/{package,writer}`.
- Сессионные сырые дампы и USB-журналы: `work/stock_da_trial_20261117/sessions`.
  Их сохранять локально, целиком в публичные отчёты не выкладывать.

Эту инструкцию обновлять после каждого изменения управления, протокола,
проверенного полного NOR или результата физического запуска. Никогда не
переписывать «проверено в модели» как «проверено на телефоне».

## 8. Архив ускоренной версии — снята после чёрного экрана

Сейчас эти артефакты НЕ установлены, сохранены для расследования.

Image: 12 896 байта; patch: 16 384 байта; heap: 4 144 576 байт.
Image SHA-256:
`4465a7ddb82cb4045854caf729a9e65276d545ac3325d8e4ac17e2c9eae304fc`.
Patch SHA-256:
`c3c6ced9524fde7dca9ce52ad4c70a7a7d57227f6578274ee8ba10028f73187d`.
Проверенный физическим readback полный NOR SHA-256:
`67114fc85f0911655fdd82c384b0676e7601a20cac7ce07e45963404609b1daf`.
Полный технический отчёт: outputs/kenshi_tetris_bootfix_20261117/LCD_FPS_REPORT_RU.md.

Готовая команда только для офлайн-предпроверки (USB не открывает):

```powershell
& 'C:\Users\USER\Documents\Codex\2026-11-16\senior-embedded-c99-developer-reverse-engineer\outputs\kenshi_stock_da_d3fix_20261117\run_trial.ps1' -WorkspaceRoot 'C:\Users\USER\Documents\Codex\2026-11-16\senior-embedded-c99-developer-reverse-engineer' -Mode DryRun
```

Ускоренная проба и последующий возврат завершены. Повторять команду с
WriteFourSectors не нужно. Закреплённая база runner относится к состоянию ДО
возврата и намеренно не обновлялась после него. Для текущей проверки нужен только
ручной холодный старт от батареи по разделу 5, без новой записи и без FINISH.
Результат USB/readback не доказывает появление игры на LCD.

Коды новой диагностики: C1 — cache/remap init, C2 — GPT, C3 — неизвестные
MPLL/divider, C4 — engine busy/start, C5 — DMA completion timeout.
Чёрный экран при раннем отказе не определяет код сам по себе: он хранится в
TCM mailbox, и не все отказы успевают нарисовать диагностический кадр.
BOOT измеряется от раннего GPT нашего boot_main, не от кнопки питания и не
включает время загрузчиков до передачи управления нашему Reset_Handler.


## 9. Архив офлайн-разбора ДО разрешения и физической записи

Рабочий каталог: work/lcd_fps_20261117/black_screen_isolation_20261117_220136.
Подробности: ANALYSIS_RU.md; точные хеши/ограничения: candidate.json.
На исходном ускоренном ELF воспроизведены C2/GPT и C1/cache без подсветки;
какой из них (или другой отказ) был на устройстве, НЕ установлено.

Изолирующий patch SHA-256:
`04068ada781211847c696fe01c95df73623eba9a4c3c1693072e50295bfe1ea3`.
Это НЕ установленная версия. Cache/MPU оставлены выключенными, подсветка ранняя,
B001 — панель готова до memory init, B002 — память/data/BSS готовы до DMA.
Маленькие метки рисуются PIO, не требуют framebuffer в PSRAM.
Белая подсветка без B001 не определяет точную причину отказа.
C99/11 packaging/4 модельных старта/5 отказов/57 keypad/304597 game checks,
BL2 handoff и положительный/отрицательный heap ASSERT прошли офлайн.
Аппаратная причина и FPS не подтверждены. Разрешения на новую запись нет;
runner на этот образ НЕ перенастроен. Сейчас в телефоне прежняя видимая версия.
После переподключения PnP видит 0E8D:0003, Status OK; активность DA не проверена.

## 10. Завершённая физическая проба

Разрешение «Заливай, но быстро» использовано на одну успешную запись
в 22:19. Актуальные хеши и сессия — в разделе 1. Изолирующая сборка теперь
установлена; прежние статусы «не разрешено / не записано» раздела 9 исторические.
Повторный WriteFourSectors НЕ запускать: закреплённая база уже использована.
Пока нужен только ручной холодный старт, не новая запись или автоматический reset.

## 11. Новая разрешённая проба E0C1
Пользователь разрешил одну запись новой сборки: patch 1d801365...e22eba.
База 20e600...ecb65, ожидаемый NOR 9c49f41e...613200.
Физический результат пока не получен. Без FINISH/reset/повторов и автoотката.

## 12. Результат E0C1 fix и новый офлайн-разбор
E0C5 на чёрном фоне подтверждён пользователем. Новая офлайн-работа: `work/lcd_fps_20261117/lcd_completion_fix_20261117_225542`.
Это НЕ разрешение и НЕ новая физическая запись. Контрольные строки при ошибке:
ошибка, MCU, MPLL, divider, cache-before, cache-after, memory-step. Нули последних
трёх ожидаемы, если ранняя заливка остановила код до memory init.

## 13. Готовый офлайн-фикс ожидания LCD
`work/lcd_fps_20261117/lcd_completion_fix_20261117_225542/REPORT_RU.md`.
Фикс запоминает CPL и переход BUSY->IDLE, но не принимает исходный IDLE
без события за успех. PLL не меняется. Дополнительные диагностические строки
после memory-step: STA / INTSTA / START / flags (1=BUSY видел, 2=CPL видел).
Новая сборка ещё не разрешена и не записана.

## 14. Completion fix: актуальное наблюдение
Раздел 1 новее исторических «не разрешён/не записан» разделов 12–13.
Ищем причину краткого кадра и погасания только офлайн; новые физические пробы не разрешены.
