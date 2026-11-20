# SDK API v1 — контракт для своей игры

Заголовки: `sdk/include/k_platform.h`, `k_media.h`, `k_shell.h`.
C99/ARMv5TE/soft-float, без ОС и без зависимостей от типов Doom.
Не вызывай HAL напрямую из игровой логики: она использует `k_runtime`.

## Lifecycle / память

- `k_boot`: magic/version/bytes, read-only callback-потоки pack и WAD; loader хранит
  их и FAT-state ниже64KiB. Callback синхронный, возвращает точное число байт или
  отрицательную ошибку; не сохраняет указатель на буфер назначения.
- `k_shell_init/tick/close`: общий poll → update → render; при смене приложения
  останавливаются media и haptic; Doom имеет suspend/resume с вычетом времени меню.
- `demo_init/update/render`: минимальный образец. Время — `r->now`, движение считает dt,
  clamp100ms защищает от огромного скачка после задержки. Это политика примера, не частота CPU.
- Статические массивы — допустимая память игры. `k_arena_init` даёт caller-owned
  линейный allocator; `alloc(bytes, alignment)` поддерживает alignment1..4096, степень2.
  Нулевой размер, переполнение/нехватка → NULL, состояние не изменено.
  `reset` инвалидирует **все** указатели, сохраняет high_water. Индивидуального free нет.
  Буфер должен реально существовать и жить дольше arena. SDK не проверяет права по произвольному адресу.
- Приложение стартует с0x10000, верх проверенной PSRAM0x400000; стек в TCM,
  не в оставшихся после heap байтах. Фактический запас проверяется map/stack-usage.
  У integrated Doom запас около100KB, это не место для неограниченных ресурсов.

## Video

`k_video_begin` получает **единственную** RGB565 128×160 lease. K_BUSY означает
LCD/DMA ещё занят: вернись к poll, не пиши в framebuffer и не крути блокирующий wait.
`r->pixels` действителен только до `k_video_end`. Повторный begin/end без правильной
пары → K_STATE. Рисование clipped: `k_rect`, `k_text`, `k_number`, `k_hex`.
Текст — простая uppercase ASCII7×7, шаг8px; Unicode/русский шрифт пока не добавлены.
`k_video_draw` читает кадровые строки ограниченным256B scratch, не целый ролик в RAM.

Независимая shell-сборка пока использует полный экран. Частичные80 игровых строк и
packed scaler сохранены **в Doom-приложении**. Это не обещание60fps для всех приложений.
Shell статические страницы обновляет1Hz/dirty, demo~30Hz, music5Hz, diag10Hz,
видео только на новый кадр/dirty. Цифры — программные ограничения, не измеренные FPS.

## Input / время

`input.held`, `.pressed`, `.released` — логические битовые маски. Raw5×uint16 всегда
доступны; аппаратный keypad active-low, поле raw сохраняет исходное представление.
`input.digits` — фронты12 цифровых клавиш0..9,*#. Не дублируй ввод в оба поля без причины.
Numeric2/8/4/6 — fallback направлений. Неоднозначный physical UP/right оставлен на калибровку.
Ввод не имеет универсальной автоповторной клавиатуры; движение использует held.

`now` — monotonic uint32 milliseconds с wrap. `k_due(now, deadline)` использует
модульную разность; интервалы должны быть не более2^31-1ms. Это НЕ CPU frequency.
`hal.wall_time` — optional coherent read-only секунды от полуночи; иначе UI показывает UPTIME.

## Assets

`k_asset_find` → указатель на запись текущего mount. `k_asset_read` проверяет принадлежность
записи, границы, переполнения и short read. Содержимое только читается. `asset_status`
сохраняет реальный mount result; отсутствие pack не мешает запустить игру с fallback sprite.
Не изменяй таблицу/mount, пока приложение хранит указатели в неё.

`k_asset_verify` — **явная** потоковая CRC32-проверка (256B stack buffer).
При старте все payload CRC автоматически не перечитываются: это могло бы долго читать SD.
CRC для целостности, **не подпись/не аутентификация**. Внешний allowlist содержит SHA256 файлов.

## Audio PCM

- `k_audio_start(rate)` поддерживает8..48kHz mono int16. На физическом adapter сейчас
  возвращает **K_UNSUPPORTED**: реального PCM sink нет.
- `k_audio_queue` возвращает принятое количество samples, включая частичный приём,
  или отрицательную ошибку. Ring capacity2048 samples, без allocation. Повторно ставь
  непоместившийся хвост; не считай частичный приём полным.
- Громкость `r->volume`0..8; default2/8. Масштабирование при помещении в очередь.
  Не записывай значения вне диапазона. Громкость не заменяет аппаратный лимит усилителя.
- `k_poll` отправляет непрерывный участок HAL; 0 — backpressure. Ошибка или HAL ответ
  >предложенных samples → stop, очередь сбрасывается, error виден приложению.
- HAL `audio_write` **немедленно копирует/потребляет** данные; не сохраняет указатель
  в SDK ring. Будущий DMA-драйвер обязан иметь собственные DMA-safe буферы/ownership.
- HAL `audio_played` — реальный DAC-cursor с последнего успешного start, НЕ queued/submitted.
  Если его нет, гарантированная sample-clock AV-sync недоступна; video работает SILENT.
- Music pause сохраняет позицию реально проигранных samples, а не чтения с упреждением.
  EOF ждёт actual played при наличии cursor. Back/другое приложение/close → stop.
- Doom-адаптер переводит stereo512frames в mono512 и пользуется той же очередью.
  При unsupported он не делает вид, что звук успешно проигран.

## Haptic

`k_haptic_pulse(1..100ms)`/cancel. Сейчас физический adapter unsupported и не включает PMIC.
Программный deadline обслуживается `k_poll`, в том числе через wrap; уход из приложения
вызывает cancel. **Это кооперативный deadline, не аппаратный watchdog.** Пока не реализовано
автономное ограничение/надёжный off при сбоях, API-тест на fake HAL не разрешает подключать
мотор вслепую. Перед настоящим драйвером нужны схема/напряжение/ограниченный физический тест.

## Результаты / evidence

K_OK=0, K_IO=-1, K_FORMAT=-2, K_RANGE=-3, K_NOTFOUND=-4,
K_UNSUPPORTED=-5, K_BUSY=-6, K_STATE=-7. Кнопка подтверждения **K_CONFIRM**, не K_OK.
`k_clock_info` даёт raw MCU/MPLL/DIV/cache + raw chain; hz=0 означает UNKNOWN.
`k_evidence`: NOT_IMPLEMENTED / IMPLEMENTED_UNVERIFIED / HARDWARE_VERIFIED / FAILED.
Ни один модельный PASS не переводит аппаратную возможность в HARDWARE_VERIFIED.
Полная матрица этой итерации — `CAPABILITIES.json`.
