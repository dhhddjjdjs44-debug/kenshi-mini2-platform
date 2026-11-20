# Медиа/ресурсы: подготовка на ПК, не кодеки телефона

## Готовые команды

```powershell
python tools/media_pack.py --sample --out stage/NEW_SAMPLE.PAK
python tools/convert_media.py --video "C:/clips/clip.mp4" --seconds 10 --out stage/CLIP.PAK
python tools/convert_media.py --video "C:/clips/clip.mp4" --silent --seconds 10 --out stage/SILENT.PAK
python tools/convert_media.py --audio "C:/music/song.mp3" --seconds 30 --out stage/MUSIC.PAK
python tools/convert_media.py --video "C:/clips/clip.mp4" --audio "C:/music/track.wav" --out stage/COMBINED.PAK
```

FFmpeg запускается **на ПК**, subprocess argv без shell, stdin выключен,
протоколы ограничены file/pipe. Можно указать `--ffmpeg C:/ffmpeg/bin/ffmpeg.exe`.
Обрабатываются существующие обычные входные файлы; выход — **новый** .pak,
перезапись существующего файла запрещена. Не задавай device/volume/UNC paths.
Никакой команды копирования на карту, форматирования или записи NOR в этих tools нет.
Конвертация ограничена300сек/256MiB. Обработка построчная/покадровая через временные файлы,
не материализует все декодированные кадры в RAM. Старый PNG-folder helper для коротких
клипов держит список кадров в памяти ПК; не использовать его для неограниченного потока.

По умолчанию128×96,10FPS, RGB565LE, mono16PCM8000Hz. Aspect ratio сохраняется,
свободная область чёрная. Это **выбранный формат теста**, не измеренная пропускная
способность телефона. Видео10FPS128×96 со звуком8000Hz ≈262KB/sec + FAT/PIO overhead;
реальную скорость надо измерить утром. Дорожка дополняется тишиной/обрезается по кадрам.
Отсутствующий audio stream допустим; явный неправильный --audio завершает с ошибкой.
MP4/H264/MP3 на самом телефоне не поддержаны. Пока аппаратный sink отсутствует,
подготовленный звук остаётся данными и видео показывает SILENT.

## Свои наборы ресурсов

`tools/pack_assets.py` принимает JSON-манифест, пути относительно файла-манифеста:

```json
{
  "assets": [
    {"name":"SPRITE.RGB", "type":1, "path":"sprite.rgb"},
    {"name":"TRACK1.WAV", "type":2, "path":"track1.wav"},
    {"name":"CLIP.KVD", "type":3, "path":"clip.kvd"}
  ]
}
```

```powershell
python tools/pack_assets.py --manifest assets.json --out stage/MY_DATA.PAK
```

До16 записей. Для готового runtime конечное имя на карте **KDATA.PAK**; выбирать
какую локальную версию установить надо отдельно. Сам packer не выбирает накопитель.
Комбинировать sprite+свои треки/клипы можно этим общим инструментом.
Исходный пример использует8×8 sprite=128bytes RGB565LE.

## KPA1 v1 (little endian)

Header16B: `4s magic="KPA1", u32 version=1, u32 count<=16, u32 entry_size=32`.
Далее count записей32B: `char name[12], u32 type, u32 offset, u32 bytes,
u32 crc32, u32 reserved=0`. Name uppercase A-Z/0-9/._,1..11 символов, NUL-terminated;
имена уникальны, payload не пересекает header/entries/другие payload.
Types:1 general/raw sprite,2 WAV,3 KVID,4 PHONE.ID.
Все границы/overflow проверяются в SDK. CRC генерируется packer и проверяется
по требованию `k_asset_verify`, не автоматически для всего контента при mount.
CRC32 не защищает от намеренной подмены.

## WAV

RIFF/WAVE PCM format1, mono,16bitLE,8000..48000Hz. Проверяются blockAlign,
byteRate, RIFF/chunk sizes, padding нечётных чанков. Не предполагай фиксированный
44-byte заголовок в своём коде. Streaming reads ограничены; float/stereo/ADPCM/MP3
не поддерживаются на устройстве, заранее конвертируй на ПК.

## KVID v1

Header32B `<4sHHHHIIIII>`:

| Поле | Значение |
|---|---|
| magic | KVID |
| version |1 |
| width/height |1..128 |
| fps |1..30 |
| frame_count |1..360000 |
| sample_rate |0=нет звука или8000..48000 |
| frame_pixel_bytes |width×height×2 |
| audio_samples_per_frame |rate/fps или0 |
| reserved |0 |

После header — фиксированные records: RGB565LE-кадр, затем mono16PCM samples кадра.
При audio rate должен делиться на fps нацело. Размер файла должен точно совпасть
с header+records; overflow/truncation отвергаются. Это raw, без межкадровой компрессии.
Video UI pause/resume/restart/EOF/back реализован; seek/универсальные codecs не входят.
Полноценная sample-clock AV-sync включается только при рабочем sink+actual played cursor.

## Конфиденциальный PHONE.ID

Только type4,15 ASCII-цифр с правильным Luhn, без newline. Значение нужно **сверить
с исходной заводской системой пользователя**, не генерировать на основе checksum.
Packer читает его из отдельного файла и не печатает в лог, но сам pack содержит
открытый ID: не публикуй такой файл. Исходный демонстрационный pack не содержит ID.
UI помечает источник ID FROM CONFIG; это не authenticated extraction и не NV write.
