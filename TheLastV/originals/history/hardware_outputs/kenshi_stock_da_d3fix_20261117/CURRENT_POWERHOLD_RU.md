> Historical candidate. Current: CURRENT_EARLY_LCD_RU.md

# Current powerhold/LCD Tetris trial — 2026-11-17

This existing writer now pins the newly prepared powerhold/LCD candidate.
Historical reports and prior authorization records are preserved, not current pins.
Range, original DA, USB transport, guard, D3/D5 framing, timeouts and fail-stop policy are unchanged.
Only exact candidate hashes/length/assets, runner backup path and regression fixtures changed.
No automatic FINISH/reset or fallback is requested.

Required fresh baseline SHA256: b05dc8477ca3ae811f0c1c612e951403a5c53f33bd23f7d576c734d31cae39f4
Image SHA256: a73fa7e7259269948df33f3905341024c70e56c1fe926dd4175394f67bbc8dc3
Patch SHA256: 6e5edc6d41a41d0a939d3e17f52d6f7a36964b2d7b8940a514ce23c2810b84f9
Expected complete 4-MiB readback SHA256: 4ed6777c3438649172c21965ecf2091dbce07c94d3def9b161634765ea54c0dc
Allowed interval: [0x00B000,0x00F000), exactly 16384 bytes.
Hardware boot has not been verified.
Prior writer snapshot: C:\Users\USER\Documents\Codex\2026-11-16\senior-embedded-c99-developer-reverse-engineer\work\stock_da_d3fix_before_powerhold_20261117_183516_443746
