---
layout: page
nav_order: 10
parent: Usage
title: Host Folder
---
# How to use the Host Folder in the Frankenwallet

The most important benefit of the Frankenwallet besides its "cold" environment is a gateway to your host machine, by reading & writing files to the [host folder](/prepare/#host-folder), so you should find & bookmark this first.

## **Everybody**{: .text-green-200}: How to find your host folder {#find-host-folder-auto}

➤ Run the file manager (`Files`) to see all drives as the Frankenwallet sees them.

If unfamiliar with Linux/Ubuntu, the `Files` application looks like a folder: in the default installation, this is a program called `Nautilus` which automatically mounts disk partitions _only as they are needed_.

{: .important }
This means none of the files on your host computer — either your "host folder" or anything else in your Windows user profile or Linux home directory — will be visible by default: _even if you have it bookmarked_.

➤ Select `Other Locations` which will show a list of disk partitions by their names.

Then choose the disk where your user files are:
- Windows partitions will generally match the name by which they appeared in Windows along with the `C:` drive as a "disk label".
- Linux partitions will also generally match the disk label, which will likely be called `HOME` if the installation of Linux on your PC put `/home` on its own partition (a common choice).

➤ Find the exact location of your user files.
- Once you see this folder in your file manager, you can "Bookmark" it from the file manager menus.
- Bookmarks will be visible from the left sidebar of the File Manager: but can only be clickable if that filesystem is already mounted as above!

{: .new-title }
> tip
>
> You can bookmark _both_ your PC's user directory _and_ the subdirectory within it that you have designated as the "host folder" — and if you give them distinctive bookmark names, it'll be harder to confuse them with Linux home directory on the Frankenwallet itself... which you might never use at all.

Files you store in the Frankenwallet can be stored anywhere: on the `Desktop` that you see when you log in (the folder with path `~/Desktop`), or in a folder that you create as an icon on that desktop or anywhere else.

## **Linux experts**{: .text-red-300}: Permanently mount your host folder (optional) {#mount-host-folder-static}

{: .important }
This procedure likely on makes sense if you're always using your Frankenwallet on the same machine: since the reference you'd be making wouldn't generally be valid on other machines.

If created, this provides a convenient reference so your "bookmarked" files above can always be reference immediately: rather than selecting them first for "auto-mount" through the File Manager.

➤ open Terminal
```bash
sudo lsblk
```
From the partition sizes and perhaps other information here, you can probably tell which `sd??` (or `nvme??`, or whatever kind of drive you have) device names is the disk partition where you keep your files on the host computer..

Please note you can substitute any term you like for `dirty` — suggested because it reminds you, the operator, that files stored here are potentiall exposed in a security hostile envioronment as soon as the computer boots regularly again.
```bash
mkdir /dirty
```
➤ Add a line to the end of your `/etc/fstab` file (e.g. if your disk partition name is `sda2`:

If host system is Linux:
```text
/dev/sda2 /dirty ext4 defaults 0 1
```
If host system is Windows:
```text
/dev/sda2 /dirty ntfs defaults 0 1
```

{: .warning-title }
> Windows user warning - for both beginners and experts
>
> By default NTFS permissions are wide open, so as with all Linux mounting of a Windows partition you’ll be able to read & write system files, including Windows OS files
... so keep an eye on where you are and bookmark a safe user directory ASAP where you will do all your work.
