# RalyxOS

RalyxOS is a minimal, terminal-first Debian-based Linux distribution. It uses the Linux kernel, GRUB, and Debian's APT repositories. The ISO is an **installer image**, not a live system: it boots the Debian Installer and installs to the target disk.

## Build ISO locally

On a Debian 12 (Bookworm) or newer build host:

```sh
sudo apt update
sudo apt install -y live-build debootstrap xorriso grub-pc-bin grub-efi-amd64-bin
sudo lb clean --purge
sudo lb config
sudo lb build
```

The resulting ISO is under `live-image-amd64.hybrid.iso` (the exact filename may vary by live-build version). The image is installer-only; use the boot menu's Install option. An internet connection is required during installation to fetch Debian packages.

## GitHub Actions

Push to `main`, open a pull request, or manually run **Build ISO** from Actions. The workflow uploads the ISO as an artifact. A manually run workflow can optionally publish an ISO as a GitHub Release by supplying a tag such as `v0.1.0`.

## Installed system

The target system is a Debian installation with a Linux kernel, GRUB, systemd, a text console (no desktop environment), and APT pointed at Debian's official repositories. The installer can offer additional Debian packages based on its network and mirror configuration.

## Scope / limitations

This repository provides a reproducible starting configuration, not a separately maintained kernel or package archive. RalyxOS tracks Debian Bookworm and relies on Debian mirrors for packages and security updates. The installer configuration and resulting ISO should be tested in a VM before installing on physical hardware.
