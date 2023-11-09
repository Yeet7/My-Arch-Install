# How I create a new Arch linux partition (with some post-setup)

# Table of Contents
- [Requirements](#Requirements)
- [Creating the Bootable Drive](#Creating-the-Bootable-Drive)
- [Booting into the Environment](#Booting-into-the-Live-Environment)
- [Creating Arch Linux](#Creating-Arch-Linux)

## Requirements
- A computer
- A flash drive
- The latest Arch ISO

## Creating the Bootable Drive
The first step is to create this, you need three things, Rufus, a flash drive, and the latest Arch ISO. Here's the steps:
1. Copy ISO to desktop (or some other location)
2. Run Rufus, select the ISO and flash drive
3. Set any other settings you would like 
   1. Ex. BIOS vs UEFI, filetype, etc.
3. Wait for program to finish.

## Booting into the Live Environment
1. Restart your PC/Laptop
2. Enter BIOS/UEFI setup
3. Select USB as boot device
4. Select the install type you would like

## Creating Arch Linux
1. Connect to the Internet
   1. Ensure connection via `ping www.google.com` (exit via CTRL+C)
   2. If not connected, plug in ethernet cable or 
   3. Follow [this](https://wiki.archlinux.org/title/Iwd#iwctl) `iwctl` guide for wifi
2. Partitioning the Disk
   1. Check that the disk you want to install on is available by using `lsblk`
   2. If not, troubleshoot some how idfk
   3. Check Partitions and make sure you have free space
   4. Run `fdisk` for graphical menu of partition creation
   5. Create two partitions, a 1 GB (/boot) and then however much else (/).
      1. Note that you should place the 1GB after the main partition, that way you can expand or shrink the partition as needed without deleting your bootloader. 
   6. Write and quit `fdisk`.
3. Setting the rest of the parameters.
   1. Run `archinstall`
   2. Set locale and such to United States or New York
   3. Enter Disk Partitioning
   4. Select Manual Disk Partitioning and the correct disk
   5. Select your main partition (/), select mark for formatting and then reselect and set root to "/"
   6. Select the 1GB bootloader partition (/boot), and repeat step 5, but changing "/" to "/boot"
   7. Finish setting up the rest of the settings to your liking
      1. Packages I recommend installing here:
         - Rofi
         - Alacritty
         - Polybar
         - Neovim
         - Chromium
         - Networkmanager
         - xorg & xorg-xrandr
   8. Save & Continue, let it install.