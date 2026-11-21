# RalyxOS

RalyxOS is a customized Debian Bookworm amd64 system with Linux, GRUB, XFCE, Debian APT repositories, and a branded desktop. The image is built from this repository; it is not a renamed Debian download.

## Included by default

- XFCE desktop, terminal, settings, Thunar file manager and LightDM
- NetworkManager, Wi-Fi firmware packages and audio controls
- Calendar: Orage
- Settings: XFCE Settings Manager
- Calculator: Galculator
- FFmpeg
- Flatpak
- LibreOffice with GTK integration and Russian localization
- Optional keyless `ralyx-ai` terminal utility for Groq-compatible API access

## Ralyx AI

The utility is included without an API key. Configure a key locally only when needed:

```bash
export GROQ_API_KEY='your-key'
ralyx-ai 'Как проверить драйвер Wi-Fi?'
```

The key is deliberately absent from the repository and ISO. `GROQ_MODEL` can select another model. Network access is required.

## Build

GitHub Actions runs `auto/config`, builds the customized filesystem with `live-build`, and uploads `ralyxos-amd64.iso` plus its SHA-256 checksum. Test the result in Limbo using an amd64/x86_64 guest and a blank virtual disk. This is a build configuration and should be validated by a successful Actions run before production use.
