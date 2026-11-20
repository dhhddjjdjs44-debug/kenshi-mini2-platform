# Проверка целостности публичного TheLastV

Из папки TheLastV на системе с sha256sum:

```sh
sha256sum -c MANIFEST.sha256
```

Из PowerShell, находясь в папке TheLastV:

```powershell
$failures = @()
foreach ($line in Get-Content -LiteralPath './MANIFEST.sha256' -Encoding UTF8) {
    if ($line -notmatch '^([0-9a-f]{64})  (.+)$') { throw 'Invalid manifest line' }
    $expected = $Matches[1]
    $path = Join-Path (Get-Location).Path $Matches[2]
    if (-not (Test-Path -LiteralPath $path -PathType Leaf)) {
        $failures += "Missing: $path"
        continue
    }
    if ((Get-FileHash -LiteralPath $path -Algorithm SHA256).Hash.ToLowerInvariant() -ne $expected) {
        $failures += "Changed: $path"
    }
}
if ($failures.Count) { $failures; throw 'Integrity check failed' }
'PASS: all listed files match'
```

Манифест включает все файлы TheLastV, кроме самого MANIFEST.sha256.
Это контроль случайных изменений, не цифровая подпись и не аппаратная приёмка.
После редактирования документов хеши нужно пересоздать.
