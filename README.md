# RalyxOS

RalyxOS is a Debian-based Linux distribution using the Linux kernel, GRUB, and Debian's official APT repositories. It provides an **installer ISO**, not a live system. The installed system is designed around the XFCE desktop.

## Build ISO

Push to `main`, open a pull request, or manually run **Build ISO** from GitHub Actions. The workflow uploads the resulting ISO and SHA-256 checksum as artifacts. A manually run workflow can optionally publish the ISO to a GitHub Release by supplying a tag such as `v0.1.0`.

To build locally on Debian:

```sh
sudo apt update
sudo apt install -y live-build debootstrap xorriso grub-pc-bin grub-efi-amd64-bin
sudo lb clean --purge
sudo lb config
sudo lb build
```

## Testing in Limbo PC (Android)

Use the `ralyxos-amd64.iso` artifact from a successful Actions run. Configure Limbo as an x86_64 PC, attach the ISO as a CD-ROM, create a blank virtual hard disk (at least 20 GB recommended), and allocate at least 2 GB RAM (4 GB is preferable for XFCE). Try both BIOS/SeaBIOS and UEFI firmware options if the boot menu does not appear. The installer needs internet access to fetch Debian packages; networking support depends on Limbo's virtual network setup. This is an installer, not a live desktop, and installation writes to the virtual disk. Do not point it at a device containing data you need.

The image is amd64; it will not run as an ARM guest. Limbo performance and firmware/device emulation can differ from real hardware.

## Desktop style

RalyxOS uses a simple dark XFCE look: Adwaita-dark controls and window borders, Adwaita icons, and a custom RalyxOS navy/teal/blue wallpaper. These defaults are staged for new user accounts. This is a branded configuration using Debian's available theme assets, not a separately authored GTK theme engine.

## Hardware

The target is amd64. Hardware support varies; Debian's `non-free-firmware` repository area is enabled. This does not guarantee every Wi-Fi adapter or NVIDIA device will work out of the box. Test the installer on the intended hardware or in a VM first.
