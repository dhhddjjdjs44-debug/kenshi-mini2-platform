# DOOM PLAY V8: исправление выравнивания спрайтов готово, НЕ ЗАПИСАНО

2026-11-19T14:41:37.119318+05:00

V7 на фото остановилась с R_ProjectSprite invalid sprite frame28, RD041E.
28 — индекс спрайта PLAY; оставшаяся часть ошибки на LCD обрезана.
В отдельной модели legacy rotating LDR по исходной инструкции0x29B40 воспроизведены
та же ошибка (полная: sprite28:13) и тот же RD1054=041E, без единого display frame.
Обычный Unicorn читал невыровненные слова иначе и потому пропустил этот дефект.

V8 копирует138 исходных имён в выровненный persistent low-RAM буфер и меняет
ТОЛЬКО указатели RAM DATA таблицы sprnames. До публикации любого указателя
проверяется полная исходная таблица/содержимое (range, NUL, FNV integrity gate —
не криптографическая аутентификация). Плохие данные -> SPRITE DATA BAD / E801,
без частичной публикации. Изменений opcodes и файлов DOOM.ELF/WAD НЕТ.
Файлы на карте копировать заново не нужно. Буфер ниже0x10000, engine выше него.

Реальный C shim, без host-side relocation, прошёл64 игровых кадра при той же
legacy семантике sprite-name LDR; PLAY имеет23 кадра, unaligned loads0, fatal0.
Ещё две обычные ARM-интеграции по64 кадра PASS.
Всего 234 unit/model/packaging групп PASS.
Это ещё НЕ подтверждение исправления/скорости на физическом телефоне.

NOR-only sd_init дополнительно скомпилирован Thumb ради размера; исходный алгоритм,
CPU/PLL/напряжения/SDdivider/controller неизменны. Аудиовывод не реализован.
Прежний guarded callback trace остаётся, hooks только со второго WAD callback.

Образ 16008байт, FF padding 376, BSS end 0xeba0.
Image SHA cb2aa23014ca5b0f08173dceb1480ac305d58515ba09175ed872cff4d76a24d3. Patch SHA e3f2fb9ded8b983b5faf10eee5cbd115a43c267ea88d020031fec73f858144b2.
Base V7 NOR SHA ca37304d6109bb70ed9b7a1fa482e087b069364171749929cd604b4665657d06. Expected V8 NOR SHA cf0e0cc4aeff8a8f74a3127a7e6bc87f414d2622e2d229c575a1affabba932f0.
Только [B000,F000), full fresh same-session before equality gate перед D3/D5,
full after + независимая ELF-проверка. Никаких retries/reset/FINISH/reconnect.
Сейчас installed остаётся проверенной V7. Записи V8 ещё НЕ было.
