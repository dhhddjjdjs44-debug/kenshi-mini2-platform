# 7. Карта памяти, файлы и подготовка медиа

## Что уже известно, а что нужно проверять заново

Пользователь сообщил microSD16GB. Последнее read-only наблюдение: MINI_2 USB,
LUN0, FAT32,157MP3 в My Music, общий размер этих треков 1 306 308 295B.
Начальные фреймы всех 157: MPEG1 LayerIII,44,1kHz, stereo; в выборке 320kbps.
Это не полное декодирование/проверка каждого трека и не доказательство CBR.
Треки не менялись/не конвертировались/не удалялись. Буква D: была только в том сеансе.

CIM показал странность: конец reported partition выходит за reported physical size.
Не исправлять геометрию, не делать chkdsk/format/прямого исправления носителя на основании этого факта:
последняя операция ограничивалась чтением обычных файлов.

## Новая read-only идентификация

Пример команд для просмотра, НЕ для записи:

```powershell
$disks = Get-CimInstance Win32_DiskDrive
$disks | Select-Object Index,Model,InterfaceType,MediaType,Size
foreach ($disk in $disks) {
    Write-Output ("DISK: {0} / {1}" -f $disk.Index,$disk.Model)
    $parts = @(Get-CimAssociatedInstance -InputObject $disk -Association Win32_DiskDriveToDiskPartition)
    $parts | Select-Object DeviceID,DiskIndex,Size,StartingOffset
    foreach ($part in $parts) {
        Get-CimAssociatedInstance -InputObject $part -Association Win32_LogicalDiskToPartition |
            Select-Object DeviceID,VolumeName,FileSystem,Size,FreeSpace
    }
}
```

Нельзя выбирать карту только по букве, свободному месту или слову USB.
Сопоставить модель телефона/USB ancestry/LUN/размер, раздел и том; внутренний
маленький LUN телефона не microSD. Диск ноутбука не цель. Если соответствие
неоднозначно — остановиться, не пробовать запись на первом съёмном диске.

Только после новой надёжной идентификации разрешено read-only перечисление
нужной папки; не подставлять старое D: из этой инструкции автоматически.
Чтение карты и BootROM-прошивка — разные режимы и разные подтверждения готовности.

## Контракт платформы на карте

Корень FAT для новой пары:
- `PLAT.ELF` — ровно ELF, для которого собран этот loader;
- `KDATA.PAK` — выбранный набор ресурсов;
- `DOOM1.WAD` — только для Doom, собственная законно полученная копия;
- старый `DOOM.ELF` и прочие файлы сохраняются, их не подменять новым именем.

Базовый допустимый список разрешённых обновлений — PLAT.ELF/KDATA.PAK, один flavor за раз.
Никакого форматирования, удаления музыки, переименования тома, переразметки или операций
с laptop disks. Для каждого файла: сохранить старую версию локально, сверить
источник/хеш/свободное место, выполнить только согласованную запись, flush,
закрыть/reopen и полный SHA256-перечитанный файл. Это отдельная операция,
**здесь она не выполнялась**. USB физическую карту перед каждой операцией определить заново.

Нельзя заменить PLAT.ELF при старом loader и ожидать совместимости. Pins
проверяют entry/размер/PT_LOAD; произвольное обновление только SD пока не реализовано.

## Подготовка медиа только на ПК

Из папки SDK, с отдельно установленным FFmpeg и существующим локальным входом:

```powershell
python tools/media_pack.py --sample --out stage/NEW_SAMPLE.PAK
python tools/convert_media.py --audio 'C:/music/song.mp3' --seconds 30 --out stage/MUSIC.PAK
python tools/convert_media.py --video 'C:/clips/clip.mp4' --silent --seconds 10 --out stage/SILENT.PAK
python tools/convert_media.py --video 'C:/clips/clip.mp4' --seconds 10 --out stage/CLIP.PAK
```

Это примеры путей; сначала заменить их на свой локальный input и НОВЫЙ output.
Существующий output конвертер не перезаписывает. Не указывать device/volume/UNC
paths и не превращать out в путь к носителю. Эти команды не копируют на SD/NOR.
FFmpeg допускает file/pipe; подготовка ограничена 300 сек/256MiB.

По умолчанию 128×96,10FPS, RGB565LE, mono16PCM8000Hz; это формат подготовки, не
замер телефона. Картинка с 10FPS и звуком 8000Hz требует порядка 262KB/s без
служебных накладных расходов; реальную SD/LCD пропускную способность ещё измерять.

## Форматы и паковщик

KDATA.PAK: KPA1 v1, максимум 16 ресурсов, имена uppercaseA-Z/0-9/._ длиной 1..11;
типы 1raw,2WAV,3KVID,4PHONE.ID. Имена уникальны, диапазоны payload не пересекаются.
CRC32 — для контроля целостности, не подпись. `k_asset_verify` вызывается явно.

WAV: RIFF/WAVE PCMformat1, mono, int16LE,8..48kHz. Stereo/float/ADPCM/MP3 не
поддержаны на телефоне этим парсером. Не предполагать заголовок всегда 44 байта.
KVID: RGB565LE records,1..128 по ширине/высоте,1..30FPS;0 или 8..48kHzmonoPCM,
при звуке rate делится на FPS, точные header/stride/границы проверяются.
Полное побайтовое описание сохранено в originals/development/docs/MEDIA_FORMATS_RU.md.

Манифест для `tools/pack_assets.py`:

```json
{"assets":[
  {"name":"SPRITE.RGB","type":1,"path":"sprite.rgb"},
  {"name":"TRACK1.WAV","type":2,"path":"track1.wav"},
  {"name":"CLIP.KVD","type":3,"path":"clip.kvd"}
]}
```

```powershell
python tools/pack_assets.py --manifest assets.json --out stage/MY_DATA.PAK
```

Пути внутри манифеста относительно его файла. В готовом runtime конечное имя
выбранного пакета — KDATA.PAK; packer сам носитель не выбирает. Demo sprite8×8RGB565
занимает 128B. PC fixture ограничивает целый pack2MiB, физическое чтение потоковое.

`PHONE.ID` хранит исходный ID открытым текстом внутри pack. Для документации
цифры не нужны, не добавлять их в общий архив/логи/публичный пакет. Валидный Luhn
не подтверждает, что ID принадлежит телефону. Ни NV, ни IMEI не записывать.
