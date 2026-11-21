# RalyxOS

RalyxOS is a customized Debian Bookworm amd64 **installer ISO**. It is not a live system. GRUB boots the Debian Installer kernel from `/install.amd/vmlinuz` and `/install.amd/initrd.gz`; installation writes RalyxOS to the selected virtual or physical disk.

The installer configures an XFCE desktop and installs the default RalyxOS application set: Orage calendar, Galculator calculator, FFmpeg, Flatpak, LibreOffice, Thunar, NetworkManager, PipeWire/Pavucontrol, firmware packages and the optional keyless `ralyx-ai` utility. Packages are downloaded from Debian mirrors during installation.

## Test in Limbo

Use an x86_64/amd64 machine profile, attach the generated ISO as CD-ROM, create a blank virtual disk, and boot with BIOS/SeaBIOS first. Choose **Install RalyxOS**. This image does not start a desktop without installation and does not use `/live/*` paths.

## Build

GitHub Actions runs `auto/config`, creates the Debian Installer image with GRUB, and uploads `ralyxos-amd64.iso` and its SHA-256 checksum. The installer needs network access to download XFCE and applications.

## AI

`ralyx-ai` is keyless by design. Configure `GROQ_API_KEY` locally after installation; no API key is included in the repository or ISO.
