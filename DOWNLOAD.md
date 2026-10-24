# Download the complete SpiderCore PE package

The complete SpiderCore PE package is published in the GitHub release assets as several numbered parts because GitHub rejects files larger than 2 GB and normal repository files larger than 100 MB.

Download **all** assets named `SpiderCore-PE-v1.0.0.zip.part-*` from the release and place them in one folder.

## Linux/macOS

```bash
cat SpiderCore-PE-v1.0.0.zip.part-* > SpiderCore-PE-v1.0.0.zip
sha256sum -c SpiderCore-PE-v1.0.0.zip.sha256
unzip SpiderCore-PE-v1.0.0.zip
```

## Windows PowerShell

```powershell
$parts = Get-ChildItem SpiderCore-PE-v1.0.0.zip.part-* | Sort-Object Name
$out = [System.IO.File]::Create("SpiderCore-PE-v1.0.0.zip")
foreach ($part in $parts) { $input = [System.IO.File]::OpenRead($part.FullName); $input.CopyTo($out); $input.Dispose() }
$out.Dispose()
Get-FileHash SpiderCore-PE-v1.0.0.zip -Algorithm SHA256
Expand-Archive SpiderCore-PE-v1.0.0.zip -DestinationPath .
```

The reconstructed archive contains the full bootable tree, all bundled tools, and the SpiderCore PE theme embedded into `sources/boot.wim`.
