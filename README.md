<div align="center">

<img src="branding/spidercore-emblem.png" width="180" alt="SpiderCore PE emblem">

# SPIDERCORE PE

### Windows PE Recovery and Cybersecurity Toolkit

**Created by Tayyab Ali** · [`rajatayyabb`](https://github.com/rajatayyabb)

[![Release](https://img.shields.io/github/v/release/rajatayyabb/SpiderCore-PE?style=for-the-badge&color=e3262e&label=LATEST%20RELEASE)](https://github.com/rajatayyabb/SpiderCore-PE/releases)
[![Downloads](https://img.shields.io/github/downloads/rajatayyabb/SpiderCore-PE/total?style=for-the-badge&color=168bff)](https://github.com/rajatayyabb/SpiderCore-PE/releases)
[![License](https://img.shields.io/badge/branding-MIT-168bff?style=for-the-badge)](LICENSE)

**A red-and-blue web-inspired rescue environment for digital forensics, incident response, Windows recovery, and secure troubleshooting.**

[Download the complete package](https://github.com/rajatayyabb/SpiderCore-PE/releases/tag/v1.0.0) · [How to reassemble](DOWNLOAD.md) · [Security guidance](SECURITY.md)

</div>

![SpiderCore PE boot artwork](branding/spidercore-boot-background.png)

## What is SpiderCore PE?

SpiderCore PE is a bootable Windows Preinstallation Environment designed for authorized computer repair and cybersecurity operations. It runs independently of a damaged Windows installation, giving you a controlled workspace for investigation, recovery, backup, diagnostics, and maintenance.

The project preserves the complete bundled toolset from its Hiren's BootCD PE base while adding a distinct SpiderCore identity, original web-inspired visuals, and a practical cybersecurity-focused workflow.

> **SpiderCore principle:** inspect first, preserve evidence, back up before destructive work, and change only what you are authorized to change.

## Cybersecurity skills represented

| Capability | What SpiderCore PE supports |
|---|---|
| **Digital forensics** | Disk, partition, file-system, deleted-file, and Windows artifact analysis |
| **Incident response** | Offline investigation, containment support, recovery, and restoration to a known-good state |
| **Malware triage** | Offline antivirus scanning, endpoint inspection, process analysis, and suspicious-file review |
| **Disk forensics** | SMART health checks, imaging, cloning, partition analysis, and secure data copying |
| **Windows internals** | Boot repair, registry analysis, startup troubleshooting, driver support, and offline administration |
| **Data protection** | Backup validation, recovery planning, encrypted-volume access, and secure file transfer |
| **Network operations** | Controlled troubleshooting with WinSCP, PuTTY, browsers, PENetwork, and authorized remote support |
| **Operational security** | Checksums, write-minimizing workflows, isolated testing, and documented changes |

## Included toolkit

The complete package keeps the existing utilities, including:

- Disk diagnostics, SMART monitoring, partition management, and low-level disk tools
- Backup, imaging, cloning, and Windows deployment utilities
- File recovery, RAID recovery, Linux file-system access, and secure copying
- Offline antivirus and malware-scanning utilities
- Registry, boot, password-recovery, and Windows repair tools
- Hardware information, system monitoring, process analysis, and troubleshooting tools
- File managers, editors, archive tools, browsers, networking utilities, and encryption tools

No bundled tool was intentionally removed during the SpiderCore rebrand.

## Download the complete bootable package

GitHub limits individual files, so the full package is published as three release parts.

1. Open the [SpiderCore PE v1.0.0 release](https://github.com/rajatayyabb/SpiderCore-PE/releases/tag/v1.0.0).
2. Download every file named `SpiderCore-PE-v1.0.0.zip.part-*` and the `.sha256` manifest.
3. Put all files in one folder.
4. Follow the [complete reconstruction guide](DOWNLOAD.md).
5. Verify the SHA-256 checksum before extracting or writing the package to USB.

### Linux or Kali Linux

```bash
cat SpiderCore-PE-v1.0.0.zip.part-* > SpiderCore-PE-v1.0.0.zip
sha256sum -c SpiderCore-PE-v1.0.0.zip.sha256
unzip SpiderCore-PE-v1.0.0.zip -d SpiderCore-PE
```

### Windows PowerShell

```powershell
$parts = Get-ChildItem SpiderCore-PE-v1.0.0.zip.part-* | Sort-Object Name
$out = [System.IO.File]::Create("SpiderCore-PE-v1.0.0.zip")
foreach ($part in $parts) {
    $input = [System.IO.File]::OpenRead($part.FullName)
    $input.CopyTo($out)
    $input.Dispose()
}
$out.Dispose()
Get-FileHash SpiderCore-PE-v1.0.0.zip -Algorithm SHA256
Expand-Archive SpiderCore-PE-v1.0.0.zip -DestinationPath .
```

## Test it safely in a virtual machine

The extracted package is a bootable USB/DVD tree. It is not itself an ISO. To create an ISO on Kali Linux, install `xorriso` and use:

```bash
xorriso -as mkisofs \
  -iso-level 3 \
  -o SpiderCore-PE.iso \
  -volid SPIDERCORE_PE \
  -eltorito-boot boot/etfsboot.com \
  -no-emul-boot \
  -boot-load-size 8 \
  -boot-info-table \
  -eltorito-alt-boot \
  -e efi/microsoft/boot/efisys.bin \
  -no-emul-boot \
  .
```

Use a disposable virtual disk and start with networking disabled. A VM with 4 GB RAM and two CPU cores is recommended. Never attach your real system disk for the first test.

## Safety and authorization

SpiderCore PE includes powerful disk, partition, credential-recovery, cloning, erasure, encryption, and remote-support utilities. Incorrect use can permanently destroy data or expose sensitive information.

Use it only on systems and data you own or are explicitly authorized to examine. Preserve original media where possible, work from a verified image or clone, keep backups, record your actions, and test unfamiliar operations in a disposable VM. Read [`SECURITY.md`](SECURITY.md) and [`THIRD-PARTY-NOTICES.md`](THIRD-PARTY-NOTICES.md) before use or redistribution.

## Project identity

- **Project:** SpiderCore PE
- **Creator:** Tayyab Ali
- **GitHub:** [@rajatayyabb](https://github.com/rajatayyabb)
- **Visual language:** deep navy, electric blue, web red, geometric spider emblem
- **Artwork:** original web-inspired fan-style design; no official Marvel or Spider-Man assets are included
- **Base environment:** Hiren's BootCD PE v1.0.8

## Repository guides

- [Download and reconstruct the complete package](DOWNLOAD.md)
- [Branding and identity](BRANDING.md)
- [Security and responsible use](SECURITY.md)
- [Third-party notices](THIRD-PARTY-NOTICES.md)
- [Contributing](CONTRIBUTING.md)
- [Release notes](RELEASE_NOTES.md)

## License

The MIT license in this repository applies to the original SpiderCore branding and documentation only. Windows PE components and bundled third-party utilities remain subject to their respective owners' licenses and redistribution terms.

<div align="center">

**Built for authorized recovery. Designed for the web.**

</div>
