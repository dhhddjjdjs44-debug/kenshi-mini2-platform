# Аппаратные блокеры — HW0.3 /20ноября2026

Устройство сейчасSTOCK, последняяNORauthority834bf…1fd85 неfreshпослеstockboot.
Speakerplayerслышен безнаушников иSnakevibощущается поUSER_REPORTED. Snakeaudio
позднееNOT_AUDIBLE, причинаUNKNOWN. BatteryinstalledNOW не доказывает предыдущую
batterytestconfiguration или USBreadiness. В этомofflinecheckpoint0deviceoperations.

## AudioPCM / music

SoftwareWAV/KVID/Doom→mono16queue, boundedwrites/backpressure/pause/EOF/cursor
есть; productionaudioHAL всё ещёK_UNSUPPORTED. ПодготовленныйWAVвKDATA.PAK не
означаетплеерпроизвольныхтрековнаSD/MP3decoder. НужныfreshSDidentity+read-only
файловыйinventory, directfilesAPI/decoderлибо согласованнаяконвертациянаПК.

Родныеmainkernel и19DCMGраспакованыnativeкодом иbyteequalсверкой. OriginalPCMring
producer/consumerпроанализирован; отдельныйC-transportмоделируется, вfirmwareне
включён. Nativepatchbootstrap/wakeupисследован, ноDSPнеисполнялся. `F027A6F0`
ждёт`82207400=5555`бесконечно; boundedmodelбезACKправильноостаётсявwait.
ARMselftest`82207E92/94=5555/6666`НЕDSPACK. Доphysicalнужныdomainpower/clock/reset,
boundedhandshake,actualmodule/PCMconsumer,analogDAC/speakerroute иmute/stop.
Readнеподготовленногоdomainтоже можетповеситьшину; «timeoutпослеread»неисправляет
самвисящийMMIOдоступ. Неungateвесьmodemнаугад.

Найденные`pcm_player.c`сA07C+70/74иplaceholderrate/fullbit — предположения, не
рабочий exact-boarddriver. Новыйultra700sourceтожеявнооставляетэтиassumptions;
егоуспехвREADMEнепроверяетниэтоткод,нинашу плату. AFEreference82CD0000,
DAC_TEST+30тоногенератор,неPCMdataFIFO.

## DSPRAM/cache collision

Nativegetter3EB000/3F1000,size2000/4000→mappingокна3E8000..3F0000 и3F0000..3F8000.
CurrentDoombss3E9A48:overlap6728B. ExistingDoomcacheдо400000перекрываетобаокна.
Передпортомвыделитьотдельныеaligned/uncachedbuffers,проверитьlinkerASSERT,все
PT_LOAD/pins/RAMslack иcachecoherency. Сейчасрезервовнет,stockconstantsнеиспользуются.

## Мотор

HW0.2genericPMU50msprobeНЕощущался. ПолныйnativePMUinit/fallbackoutput6меняет
EN0,неvoltage;17→mapindex8. Однакоstockрегистрируетhandler10260159через100344F1
вF00967BC;wrapper100344CCвыбираетего. Этотasyncaudio/DSPpathотличаетсяотPMU.
Proofв`stock-vibration-override-audit.json`сoneallocatorcallback/message,не
имитируетOSsend/success. Запрос/stopDSPmailboxизвестен,boardmotorrouteнеподтверждён.
`1003B57C`PMUopen,НЕI2C. Voltage/dischargeнеперебратьвслепую. Нуженbounded
запуск/отключениеидоказанноенезависимоеsafety-off;softwarepollнедостаточенприCPUhang.

## CPU / input

НоваяESTMHZоценкапостроена,нонаphoneнеизмерена. GPT26MнеравноCPU;4/5cycleTCM
допущенияисогласование2%неабсолютнаяточность. exactHz0. Неутверждать260M.
Общий20-contactmapпоphotoприменёнSDK/Doom/tester,ENDunknown;hardware-retestpending.

Доказательства/порядокв`../REPORT_HW03_RU.md`и`HW_DIAGNOSTICS_RU.md`; nativeDSP
blobs/patchнераздаватьвSDK. Сборка/modelPASS/PMICreadback≠speaker/motor/clockproof.
