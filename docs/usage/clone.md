---
layout: page
nav_order: 35
parent: Usage
title: Cloning a Frankenwallet
---
# Using Clonezilla to make copies of a Frankenwallet
{: .no_toc }
- TOC
{:toc}

When originally considering the best methods for making multiple copies of a Frankenwallet (in [this discussion](https://github.com/rphair/frankenwallet/discussions/5)), the idea of "build scripts" or sets of installation parameters was ruled out early because:

➤ Users and working groups interested in maintaining several Frankenwallets would likely want to replicate installations *including their own chosen software* (e.g. the [Cardano CLI](/cardano/software) or certain [operator tools](/cardano/scripts)): which wouldn't be covered by a general installation script.

➤ The act of copying an existing installation also presents the opportunity to make a working backup of an original device *including all data that it contains*: preventing the need to securely make copies of that data between installed devices afterward.

➤ Continuing to use low-level tools to build and copy the Frankenwallet — rather than ISO builders and installers which would work through networked environments — will allow operators to maintain air gap consistency while avoiding the use of general-purpose tools not audited for security.

## Clonezilla basics {#general}

[Clonezilla](https://clonezilla.org/) is a best-in-class, open-source option which has been the go-to choice of system admins for decades and whose secure operation can be easily verified through the years.

The modes of running Clonezilla present additional benefits to operators and agencies who want to distribute their operations among multiple Frankenwallets, as well as individuals simply using it to back up a single device's operations or data.

{: .highlight }
on Wikipedia: [Clonezilla](https://en.wikipedia.org/wiki/Clonezilla) and its elementary component [Partclone](https://en.wikipedia.org/wiki/Partclone)

The program is highly flexible, with even more flexibility if users are able to revert to the Linux command line to arrange custom environments to create and extract images of disks & partitions.

But since Linux images for Full-Disk Encryption are so consistent (from [installation with LVM and encryption](https://ubuntu.com/tutorials/install-ubuntu-desktop#6-type-of-installation)), you will likely want Clonezilla to simply make an entire disk (`device-to-device`) copy in "beginner mode" so that the procedure will work almost automatically.

{: .important }
Though Clonezilla has the ability to decrypt a filesystem, the device-to-device copy doesn't do this.

When making a simple copy from one device to another, Clonezilla will clone one LUKS partition to another by copying the encrypted data block-for-block.  This has the following consequences:

- advantage: It will be secure, without exposing the Frankenwallet password or encrypted data to the application or the environment where it's running.
- disadvantages: The new disk size must generally be equal to or larger than the old one, and any space difference at the end of a larger partition will be generally left unused.  Also, unallocated space will also need to be copied (since `clonezilla` won't know it's unallocated).

There will be opportunities [later](#sparse-copy) to adjust sizes if they are different: but to get started the recommendation would be to use external drives of roughly the same size (and try to always install on the smallest one first).

## General cloning procedure for the Frankenwallet {#procedure}

➤ Get a Linux install disk: preferably the one you originally installed the Frankenwallet from (so it's familiar).

**Linux Mint** is the current best choice since it's the easiest to run Clonezilla rom, it includes `gparted` by default (if needed), and it's the currently preferred platform for the Frankenwallet itself.

{: .note }
There is a dedicated [Clonezilla Live](https://clonezilla.org/clonezilla-live.php) which can also be used by booting from its ISO, but...

Clonezilla Live offers a text-only, menu-driven interface that requires "dropping to a shell" to run commands... so most operators will prefer the flexibility of the OS install media with graphics, and multiple windows... with the ability to more easily customise the setup, make image backups, adjust filesystem sizes ([with `gparted`](/install/internal/#gparted)), etc.

➤ Ensure you have **3 free USB ports** for all the drives you will need concurrent access to:

- the installation media
- the Frankenwallet you want to clone from
- the blank device you want to clone it to

➤ Boot from the OS installer drive and attach the "from" and "to" drives.

➤ Install `clonezilla` from its repository package, typically with:

```  
apt install clonezilla  
```

If using Ubuntu or another Debian variant besides Mint, the Debian "Universe" repository might not be selected by default & so you would have to add it from the Software Manager (see [first 3 steps here](https://askubuntu.com/questions/1500034/how-do-i-image-a-luks-system-disk-with-clonezilla-without-including-all-the-empt#answer-1526068)).

➤ Run `clonezilla` (as root or with `sudo`) and select basic whole-disk cloning from the text menus:

1.  choose `device-to-device` from the initial menu
2.  select `Beginner` mode (all default options)
3.  choose `disk_to_local_disk` (vs. copying partitions one at a time)
4.  select the Source and Target disks

In case you've not chosen the Beginner mode, this page ([Disk to disk clone](https://clonezilla.org/fine-print-live-doc.php?path=clonezilla-live/doc/03_Disk_to_disk_clone)) shows some of the other options you will be presented with.

In any case, if there are no warnings or errors (generally for obvious reasons) the process will:

- set up the new device with the same copy of GRUB so it's also bootable;
- copy the unencrypted `/boot` and EFI (`/boot/efi`) partitions;
- copy the encrypted volume: byte-for-byte, without changing anything inside, so it doesn't need to be decrypted in the process.

➤ Shut down the OS, remove the other drives, and test & enjoy your newly cloned Frankenwallet.

## Other methods of duplicating the Frankenwallet with Clonezilla {#other-methods}

The Clonezilla documentation section [step- by-step examples](https://clonezilla.org/clonezilla-live-doc.php) shows menu selections and screenshots for other methods of copying, including these most relevant to Frankenwallet workflow:

### Simply [save a disk image](https://clonezilla.org/fine-print-live-doc.php?path=clonezilla-live/doc/01_Save_disk_image) {#image}

If deliberate backups of Frankenwallet data become too complicated to manage with differently encrypted and saved files, you can also use Clonezilla to make a complete copy of the partition and encrypt the image.

{: .warning }
Since files in the image itself may not be encrypted, make sure you always specify that this file should be saved with a passphrase!  Otherwise, if the LUKS volume is decrypted and the image saved on your host machine, your confidential data will be exposed.

### Clone [one image to multiple disks](https://clonezilla.org//fine-print-live-doc.php?path=clonezilla-live/doc/03_One_image_to_multiple_disks) {#multiple}

These steps will guide you through producing an image file from your original Frankenwallet and then cloning that image to as many disk devices as you can attach at the same time.

{: .new-title }
> tip
>
> If the original image is from a "cold" frankenwallet, any of the copies can become "cold" or "cool" according to whether or not you later choose to break their "air gap" for Internet use.

### Clone with [massive deployment from an image via multicast](https://clonezilla.org/fine-print-live-doc.php?path=clonezilla-live/doc/11_lite_server) {#multicast}

This will run the cloning *over any network*, so you won't be limited by the number of drives that can be attached to a computer at the same time.

With the appropriate network setup, this should also allow working groups to replicate an original Frankenwallet across long distances so that the basic configuration and/or data of a single device can then be used in multiple locations (e.g. for managing institutional crypto wallets).

## Fine-tuning clone partition sizes {#fine-tuning}

### Adjusting the size of cloned Frankenwallet encrypted partition {#resizing}

Though Clonezilla won't size the encrypted partitions for you, you can use `gparted` which has already been illustrated [here](https://frankenwallet.com/install/internal/#gparted) by running it from the installation media after `clonezilla` finishes.  Just follow this extra step before running `gparted` to resize the partition: [gparted: Opening an Encrypted Partition](https://gparted.org/display-doc.php%3Fname%3Dhelp-manual#gparted-open-encrypted-partition)

{: .important }
Using `gparted` for this task avoids [a very difficult manual process](https://wiki.archlinux.org/title/Resizing_LVM-on-LUKS) of changing the size of a LUKS partition with raw Linux commands.

{: .new-title }
> tip
>
> Depending on how you intend to use the copies and original, you might also choose to shrink the original Frankenwallet partition _first_ so the Clonezilla copies fit in a smaller external drive size: also using `gparted` from the installation media.

### Efficiently cloning a large Frankenwallet to a smaller device {#sparse-copy}

Since Clonezilla will copy all the "empty space" in an encrypted filesystem, you could first [save an image](https://clonezilla.org/fine-print-live-doc.php?path=clonezilla-live/doc/01_Save_disk_image) of the original Frankenwallet and then restore that image into a pre-built encrypted partition on a smaller drive.  See this excellent guide: [Clonezilla Imaging onto a LUKS Encrypted Filesystem](https://gock.net/blog/2025/clonezilla-save-on-luks-filesystem)
