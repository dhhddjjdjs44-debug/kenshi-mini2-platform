# Current authorized bootlight Tetris transaction — 2026-11-17

This existing writer is now pinned to the bootlight-fixed candidate. Historical
reports/evidence describe earlier transactions and are retained unchanged.
No transport, D3 descriptor, D5 framing, timeouts, DA, range, or retry policy was changed.
Only candidate-specific preflight pins, runner input paths, and offline regressions were updated.
The candidate deliberately uses FF padding after its 0x3418-byte image within the
fully authorized four sectors, rather than preserving the prior partial-sector suffix.

- Allowed range: [0x00B000,0x00F000), exactly 16384 bytes.
- Required fresh full NOR SHA256: e47fc02881547a3cc949afb06fcdb02ca3124721d04bbf2be229b707685cfb60
- Candidate image SHA256: a4b1e8e2a8b830d1991bd505b848448161d0540516159d3e81ed6d9664824659
- Four-sector patch SHA256: f8f96f1bda9b6a1e729be30d50a882d64c2c2283fe0406ab44e668d0f66929ad
- Required complete readback SHA256: b05dc8477ca3ae811f0c1c612e951403a5c53f33bd23f7d576c734d31cae39f4
- Default run is offline; physical mode requires WriteFourSectors.
- No automatic FINISH/reset is requested; manual power-cycle only after full verification.
- Hardware boot/LCD are not yet confirmed.
- Prior release snapshot: C:\Users\USER\Documents\Codex\2026-11-16\senior-embedded-c99-developer-reverse-engineer\work\stock_da_d3fix_before_bootlight_20261117_175123_894711
