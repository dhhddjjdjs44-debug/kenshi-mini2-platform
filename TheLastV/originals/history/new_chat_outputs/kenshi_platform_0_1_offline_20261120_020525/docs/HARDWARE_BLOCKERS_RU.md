# Железо: что известно и чего не выдавать за результат

Ночью физические операции запрещены: пользователь спит. В новой device-прошивке
**нет драйвера, который вслепую включает динамик/мотор или меняет PLL**.

## PCM

Есть полный общий software тракт: WAV/KVID/Doom→mono16→ограниченная очередь→HAL,
backpressure/partial writes/errors, pause/EOF, actual played cursor для AV-sync.
Нет доказанного аппаратного consumer этой очереди. Тоногенератор не равен PCM FIFO.

Локальные доказательства:
- старое read-only peripheral audit в исходном research workspace;
- первичные исходники, закреплённые commit/hash в `research/source-acquisition.json`;
- найденный `pcm_player.c` сам помечает FIFO/status offsets как assumptions и содержит
  placeholder rate programming. Портировать его как проверенный sink нельзя.
- AFE reference base0x82CD0000, не наугад0xA07C; AFE_DAC_TEST+0x30 — tone generator,
  не доказанный data FIFO. Аналоговый/power/digital routing тоже нужен.
- Modem/DSP domain clocks связаны; закрывать/открывать весь домен случайными записями нельзя.
  Даже чтение незапитанного domain может зависнуть, поэтому current diagnostics его не трогает.
- Beep sample с делителем AMP_DIV(25) не является доказанным тихим уровнем:
  поле3bit маскирует25 в1. Его не запускали.

Следующее полезное доказательство: документированный digital buffer/interface,
stock routine с восстановленным runtime/TCM или независимый рабочий board driver
с точной маршрутизацией. Затем один ограниченный тихий тест при пользователе,
не обещание «звук точно есть» на основании ненулевых PCM.

## Мотор

PMIC VIBR reference A07001B0, EN0/ON_SEL1/VOSEL5:4 — это карта регистра, не доказательство
схемы/напряжения/наличия мотора на конкретной плате. Старый readback не равен ощущению.
Текущий HAL unsupported и не подаёт питание. Software haptic deadline кооперативный;
будущему драйверу нужен независимый safety-off/restore при зависании игрового кода.

## Частота

Сохраняется исходный profile B621 / MPLL1401 / DIV0. Дополнительные clock chain raw
поля читаются без перенастройки. Значение hz=0 и надпись UNKNOWN намеренные.
PLL reference описывает номинальный генератор, но полная ARM source/mux/div chain
для этой платы независимо не доказана. GPT26MHz — частота таймера, не доказательство
26MHz CPU. Счёт цикла в TCM тоже не превращается в MHz без обоснования ISA/cache/waitstates.
Старые veneers нельзя live-call: их оригинальная decompressed/relocated TCM среда
не восстановлена, часть её занята нашими стеками.

## Заводской runtime

Read-only literal scan и ограниченный RAW/LZMA probe не дали проверенного runtime.
«Не нашли literal» не доказывает отсутствия периферии в compressed firmware.
Ничего декомпрессированного не выполняли. Результаты в research JSON — отрицательный
исследовательский результат, не драйвер и не аппаратная готовность.

Именно эти blockers, а не кнопки красивого меню, остаются до полной платформы.
