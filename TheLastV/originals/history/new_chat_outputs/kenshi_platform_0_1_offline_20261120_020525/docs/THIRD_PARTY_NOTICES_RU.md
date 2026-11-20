# Происхождение / сторонние компоненты / передача

Это локальный разработческий пакет для пользователя, не юридическое заключение
и не заявление о полностью проверенной лицензии всех унаследованных компонентов.

- Родитель: sealed V12 `doom_v12_20261119_200415`; SHA manifest/lineage в
  PLATFORM_PROVENANCE.json и read-only audit. V11/V12 не пересобирались/не менялись.
- `sdk`, `apps`, `ports` — новая C99-платформа/адаптеры данной итерации.
  `sdk/src/k_memory.c` и `ports/loader_runtime.c` происходят из generic memory routines
  родителя; это не типы/логика/heap Doom. Полный sdk ELF не линкует PureDOOM.
- `project/src`, `project/include`, `src/*` — унаследованные LCD/board/SD/FAT/ELF/
  clock/boot-код и board-derived tables. Исключение Doom из линковки само по себе
  **не доказывает** снятие всех сторонних ограничений. До публичного релиза нужен
  отдельный license/provenance audit, особенно извлечённых board metadata/tables.
- `doom/vendor/PureDOOM.h` и интегрированный Doom — сторонняя кодовая база;
  рядом сохранён upstream `doom/vendor/LICENSE` (GPL version2). Сохранять исходники,
  уведомления и условия upstream при распространении. В заголовке есть исторические
  copyright/DOOM Source Code License notices; их не удаляли. Не выдаём это за
  самостоятельное разрешение перераспространять game-data WAD.
- DOOM1.WAD **не включён** ни в SDK source, ни в утренний пакет: использовать свою
  законно полученную копию; на существующей карте файл сохраняется.
- Оригинальный4MiB stock/NV dump, реальные IMEI, USB logs, физические writers,
  acquisition/session binaries **не включены**.
- Исследовательские FFmpeg и clang-format **не включены** в передаваемые архивы.
  Локальная FFmpeg7.1 build объявляет GPL version3-or-later; его происхождение/hash
  сохранены локально в research-tools provenance. При самостоятельном распространении
  FFmpeg нужны его собственные лицензии/source obligations; здесь предлагается
  использовать отдельно установленный экземпляр на ПК.
- Python Unicorn/pyelftools/Pillow и ARM GCC не упаковываются: используются как
  отдельно установленные tools со своими лицензиями.

Этот пакет не меняет IMEI/NV и не выдаёт сотовую связь за работающую.
