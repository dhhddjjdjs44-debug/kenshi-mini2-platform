# HW0.3: диагностика / ограничения

Эта копия UNSEALED, новая пара loader+PLAT.ELF **не установлена**. Сейчас STOCK,
battery present USER_REPORTED; USB/NOR/card readiness и freshbaseline не получены.
Полный результат: `../REPORT_HW03_RU.md`. Физических операций в этом checkpoint0.

## Меню

DIAGNOSTICS:4/6 перелистывают6страниц, правая софт72 возвращает. OK/левая софт33/5
на нужной странице выполняют явный запрос; render/hold/idle сами его не запускают.
1. SOUND/PCM: безопасный analog snapshot8регистров. Это не тон, не PCMdriver.
   PCM NO SINK; DSP/AFE domain тут не читается и не включается.
2. MOTOR TEST: старый blocking50ms PMU probe. **Уже был NO FELT VIBRATION по
   пользователю**, повторение readback не означает исправления. Найден DSPoverride
   стока, genericPMU путь ему не эквивалентен. Не менять voltage/discharge вслепую.
3. CPU TEST: новый TCM A/B,N/2N estimate. См. ниже; фотография результата нужна
   только после отдельно согласованной установки, сейчас частота UNKNOWN.
4. KEY CAPTURE:21шаг EXPECT/DETECTED/contact/held/release, схема ниже.
5. ASSETS: read-only pack диагностика, без записей на SD.
6. PROFILE US: последние игровые UPDATE/CONVERT/LCD DMA и FPS×10. Меню не
   подменяет snapshot игры; это ещё не новый приростFPS и не внешний замер.

## CPU

`ports/cpu_tcm.c` и `ports/cpu_work.S` используют существующий16B
`boot_mailbox.tcm_probe_code`; исходные4слова восстанавливаются на всех выходах.
A=SUBS/BNE, B=ADD/SUBS/BNE; N65536/2N,3серии. Разность N/2N убирает общий
call/MMIO overhead, B-A выделяет добавочный ADD. При zero-wait ARM7TCM циклах4/5
и GPT26MHz это оценка CPUHz. Проверяется взаимная согласованность2%, стабильность
clockregs, checksum и ходGPT; все несогласованные случаи возвращают UNKNOWN.
**2% — критерий согласования, НЕ абсолютная погрешность.** На реальном телефоне
ещё не выполнялось; не выдавать искусственные26/260MHz из теста за физические.

IRQ/FIQ должны уже быть masked исходным loader; unsafecontext отвергается доMMIO
и записиTCM. Probe не меняет CPSR control/PLL/cache/EMI/voltage. ARM-disassemblyaudit
не допускает MSR/MCR/CPS/SVC/SWI, кроме чтенияCPSR однимMRS. ALU flags могут меняться.
UI: EST MHZ, TCM DELTA TICKS, REF26M CONSIS2%; при отказе TCM REJECTED/reason.
exact_cpu_hz остаётся0. Старый dependent-ADD lower-bound API оставлен отдельно,
но CPUстраница теперь вызываетK_HW_CPU_TCM, а не старыйMIN MHZ.

## Кнопки

Единая фото-authority `sdk/include/k_keys.h` / `sdk/src/k_keys.c`:
UP39 DOWN15 LEFT21 RIGHT30 OK42 LEFT_SOFT33 RIGHT_SOFT72 CALL24; END unknown255.
1=27 2=0 3=51 4=12 5=13 6=57 7=6 8=9 9=48 *=3 0=45 #=54.
Это decimalcontact, не HEXmask. В SDK левая софт выбирает, праваяBACK; в Doom
леваяESC-menu, праваяshell. UP никогдаBACK. Карта уже применена в новом коде,
но не прошита. По новой таблице DETECTED показывает фактическое название, а не
старое RIGHT/UP? и не подменяет егоEXPECTED.

Перед мастером отпустить всё. Снимок5active-low rawwords, ghost/multi/rolling и
повторный контакт отклоняются. Сохранение после полного release, holdпри входе
не записывается. BACK/OK/CALL внутримастера не управляютshell.
21шаг: крестовина/OK,двеsoft,CALL,END,1..9,*0#. END только короткийтап,
не удерживать power;0+#коротко пропускает,0+#1.2s выходит.2/8 листают итог.
РезультатмастераRAM-only, неautoapply, неSD/NVwrite. Эта диагностика нужна для
подтверждения карты, не для очередной слепой перестановки.

## Мотор и звук

Productionmotor_set/audioHAL остаютсяK_UNSUPPORTED. Старый50msprobe сохраняет
voltage/calibration, проверяетGPT доenable, все обычныеpost-enableвыходы ведут
черезOFF/readback, GPTstall/общийiterationlimit конечные. Это не автономный
hardwareone-shot и не защита от остановившегосяCPU/висящейшины.

Native stock motor override идёт черезaudioDSP; bootpatch/wakeup/ring/mapping
разобраны офлайн. DSPready/analogroute/реальныйconsumer ещё не доказаны. Стоковые
PSRAMокна пересекаютDoomBSS и егоcache-регион; доliveнуженрезерв/ребюджет.
НельзяlivecallстарыеF0*/TCMveneers или считатьmodelACK аппаратным. PrivateDSPpatch
иdecodedstockне включать вSDK/пакет. Детали: `../research/hw/RESEARCH_NEXT_RU.md`.
