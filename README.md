# RalyxOS

RalyxOS is a Debian-based Linux distribution using the Linux kernel, GRUB, and Debian's official APT repositories. It provides an **installer ISO**, not a live system. The installer installs Debian Bookworm with the XFCE graphical desktop environment.

## Build ISO locally

On a Debian 12 (Bookworm) or newer build host:

```sh
sudo apt update
sudo apt install -y live-build debootstrap xorriso grub-pc-bin grub-efi-amd64-bin
sudo lb clean --purge
sudo lb config
sudo lb build
```

The resulting ISO is typically named `live-image-amd64.hybrid.iso` (the exact name can vary by live-build version). The image boots the Debian text installer; it is not a live desktop. During installation, select XFCE in tasksel if it is not selected automatically. An internet connection is required to download the desktop and other packages.

## GitHub Actions

Push to `main`, open a pull request, or manually run **Build ISO** from Actions. The workflow uploads the ISO as an artifact. A manually run workflow can optionally publish an ISO as a GitHub Release by supplying a tag such as `v0.1.0`.

## Installed system

The installed system uses Debian Bookworm, Linux, GRUB, systemd, XFCE, and APT configured for Debian's official repositories. Package availability and security updates come from Debian mirrors.

## Scope / limitations

This repository provides a reproducible starting configuration, not a separately maintained kernel or package archive. The installer configuration and resulting ISO should be tested in a VM before installing on physical hardware.
