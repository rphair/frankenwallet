---
layout: page
nav_order: 20
parent: Preparation
title: BIOS settings
---
# Check your BIOS settings

Select one of the following 2 approaches based on how familiar you are with OS and PC booting principles:

{: .note }
If neither of these approaches seems possible to verify based on your level of experience, you are welcome to do what most developers and enthusiasts will do: assume it will be possible to improvise around any difficulty you have in bootingthe system you are building, and continue on to the next step anyway. 🤠

## 1. The simple (beginner) approach {#bios-1-beginners}

Most computers in use today — unless they are more than several years old or have been deliberately set to "Legacy Mode" to suppress it — boot operating systems with UEFI.

Depending on which is set by default on your computer's BIOS settings, you will get one of these configurations when you install Frankenwallet or any other Ubuntu installation in which "whole disk encryption" is selected:

➤ if **UEFI** is active, it will be able to encrypt the `/boot` partition as well the main partition used for the Ubuntu operating system & data.

➤ if UEFI is not active (**legacy mode**), though the main partition will still be encrypted, the  `/boot` partition will remain unencrypted, due to constraints described at the "advanced" links below.

Therefore, you should check your BIOS settings especially on older computers to see if UEFI mode is missing or disabled, and if you go ahead to install your Frankenwallet without UEFI you should:

- (**if** **`/boot`** **is not encrypted**, or if you're not sure) **Never put your Frankenwallet into a system that was not booted from it**... since malicious software on that computer might be able to write to and compromise the unencrypted `/boot` partition.
- In your host computer's BIOS settings, move the USB / removable disk higher up in the "boot order" or "boot priority" than your computer's disk... to avoid accidentally booting from the host operating system while the Frankenwallet is still connected as an ordinary writable drive.

➤ **Warning** in case you plan to use your Frankenwallet on multiple host computers: If your Frankenwallet is installed in UEFI mode, it will not boot on (usually very old) computers whose BIOS is set to boot only in Legacy Mode.

- The reverse is also true — Legacy Mode installations won't boot on computers that can only boot UEFI formatted disks & media — but most UEFI compliant computers are set to search for boot devices in Legacy Mode after failing to find any UEFI devices… so that isn't so much of a problem.

Therefore, if you have a mix of Legacy Mode and UEFI computers, be sure your Frankenwallet is installed on one of the computers set to use Legacy Mode.

## 2. The complicated (expert) approach {#bios-2-experts}

Notes on whether encrypted partitions are bootable or accessible through GRUB vs. UEFI Secure Boot, particuarly if you think you would prefer the entire disk (including the `/boot` partition) to be encrypted:

- [Grub 2 fails to boot a kernel on a luks encrypted volume with Secure Boot enabled](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1565950)

Notes on whether full disk encryption can be set up by the installer (i.e. whether it's possible to encrypt the `/boot` partition as well):

- [Ubuntu Documentation \> Full Disk Encryption Howto (2019)](https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019#Selecting_UEFI_boot_mode)
- Note this problem was identified here the year before the current (2021-09-21) Ubuntu installer 20.04 … in which the "fail to boot encrypted volume" problem was fixed with the most current release of GRUB at the time.

Without a detailed reading & understanding of these two links above, you might not be able to predict whether your Frankenwallet installation (with full disk encryption, of course) will have an encrypted `/boot` partition... until you try it.

➤ If you have more insights about this issue that you would like to see included in these instructions, based on experience or experimentation, please report them [here](https://github.com/rphair/frankenwallet).

### Notes on Secure Boot and UEFI

For troubleshooting or advanced configuration:

- [ManualFullSystemEncryption](https://help.ubuntu.com/community/ManualFullSystemEncryption) (another Ubuntu up to date article... installer not mentioned)
- [Migrating an unencrypted PureOS Debian install to fully encrypted](https://github.com/jjakob/wiki/blob/master/Linux/Migrating-an-unencrypted-PureOS-Debian-install-to-fully-encrypted.md)
- [Encrypting disks on Ubuntu 19.04](https://medium.com/@chrishantha/encrypting-disks-on-ubuntu-19-04-b50bfc65182a)
