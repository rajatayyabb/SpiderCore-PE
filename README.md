# SpiderCore PE

**SpiderCore PE** is a personal Windows PE recovery, diagnostics, backup, and maintenance environment created by **Tayyab Ali** (`rajatayyabb`). It preserves the complete bundled toolset from its Hiren's BootCD PE base while adding a distinct original red/blue web-inspired identity.

> **Important:** This is a recovery environment, not a normal desktop operating system. Many included utilities can modify partitions, overwrite disks, reset Windows credentials, erase data, or access networks. Use only on systems you own or are authorized to repair.

## Included capabilities

The project keeps the existing bundled tools, including disk and partition utilities, backup and cloning tools, file recovery tools, antivirus scanners, registry and password-recovery utilities, hardware diagnostics, file managers, networking tools, and general-purpose utilities. No bundled tool was intentionally removed during the rebrand.

## Cybersecurity skills demonstrated

SpiderCore PE presents a practical Windows security and recovery skill set:

- **Digital forensics and evidence handling** — inspecting disks, partitions, file systems, deleted files, and Windows artifacts while minimizing unnecessary changes to source media.
- **Incident response and system recovery** — isolating a damaged or compromised Windows installation, collecting useful information, restoring access, and returning systems to a known-good state.
- **Malware triage and endpoint analysis** — using offline scanners, portable diagnostics, process and system inspection tools, and file analysis utilities before allowing a damaged installation to boot normally.
- **Disk and file-system forensics** — partition analysis, SMART health review, low-level disk diagnostics, cloning, imaging, recovery, and safe data copying.
- **Windows internals and administration** — registry backup and analysis, boot repair, startup troubleshooting, driver support, offline Windows maintenance, and system configuration.
- **Data protection and cryptography** — encrypted-volume access with VeraCrypt, backup validation, secure copying, and recovery planning.
- **Network and remote-support operations** — controlled use of WinSCP, PuTTY, AnyDesk, and related utilities for authorized troubleshooting and file transfer.
- **Operational safety** — using checksums, backups, write-minimizing workflows, isolated testing, and documented change control before destructive operations.

These are capabilities represented by the tools and workflow in the project; they are not a claim of a particular professional certification. Use all tools only on systems and data you own or are explicitly authorized to examine.

## Booting

1. Use a trustworthy imaging tool such as Rufus to write the project image to a spare USB drive.
2. Back up important data before using any disk or partition operation.
3. Boot the target computer from the USB drive using its one-time boot menu.
4. Prefer UEFI mode on modern systems; legacy BIOS support is retained where the firmware supports it.
5. Test first in a disposable virtual machine and verify the USB on more than one machine before relying on it for recovery work.

The current tree retains both BIOS and UEFI boot structures. The SpiderCore theme is embedded in the PE image through the desktop wallpaper, boot initialization logo/status screen, WinXShell configuration, and image metadata. Boot-critical executables and third-party application binaries were not modified.

## Project structure

- `boot/`, `efi/`, `bootmgr*`, `sources/` — boot environment
- `Programs/` — bundled portable utilities
- `branding/` — original SpiderCore PE visual assets
- `BRANDING.md` — identity and attribution notes
- `THIRD-PARTY-NOTICES.md` — licensing and redistribution guidance
- `checksums.sha256` — integrity hashes for the published tree metadata

## Legal and licensing

SpiderCore PE is an original project identity and documentation layer. The included Windows PE components and third-party utilities remain subject to their respective owners' licenses, trademarks, and redistribution terms. Do not imply that the third-party software is authored by Tayyab Ali. Review `THIRD-PARTY-NOTICES.md` before publishing a public binary release.

This project does not include official Spider-Man or Marvel artwork, logos, character images, or quotes.

## Credits

- SpiderCore PE rebrand and documentation: Tayyab Ali — https://github.com/rajatayyabb
- Base environment: Hiren's BootCD PE v1.0.8 — https://www.hirensbootcd.org/
- Third-party utilities: their respective authors and vendors
