---
layout: page
nav_order: 40
parent: Installation
title: Package installation
---
# Manual settings & tuning package environment for security
{: .no_toc }
- TOC
{:toc}

## Open a shell {#shell}

Select & run **Terminal** from the list of Activities.

- Right-click the icon on that list, or where you see it appear on the Dock at the side of the screen, to add it to the list of Favorites to keep it on the Dock... you're going to need it!

{: .highlight }
Commands to type in the Terminal (also called the Shell or "command line") appear here like this:
```text
type this stuff into Terminal
```

## Check & set time zone {#time-zone}

(**optional**) If you want to **set local UTC time zone**, to match timestamps on your node software, for instance):

``` plaintext
sudo timedatectl set-timezone UTC
```

## Remove standard packages which may be security risks {#remove-insecure-packages}

Some of these may have side effects and/or security consequences if we ever connect to the Internet.

(**optional**) **Uninstall** **`snap`** **and remove all snaps**

[Snaps](https://snapcraft.io/) are prefabricated images containing all components of an application, including libraries which may supersede the security vetted libraries of the OS itself.  Snaps may contain closed source components.

{: .important }
Anyone in favour of installing software this way should please keep in mind that the security breach described in [our origin story](/frankenwallet/intro/history) was also the result of using images assembled from dependencies specified somewhere else... which is pretty much how `snap` works.

Specific removal instructions are likely to change with Ubuntu patch levels so please follow instructions here ([How do I turn off snap in Ubuntu?](https://linuxhint.com/turn-off-snap-ubuntu/)) or search the Internet on another machine for a proper installation method.  (This is not urgent so you can wait until the next time you've booted the Frankenwallet.)

## Uninstall CUPS printer management services

This runs a printer manager service & opens up a web port intended for browser-based administration:

```bash
sudo apt remove cups
```

## Disable unattended upgrades

This ensures you'll never be spontaneously checking for packages, even if the software update check settings you made earlier (to the **Software & Updates** app) are changed or reverted:

    sudo apt remove unattended-upgrades

## System software installation & update

{: .note }
> It is likely this step may be done more securely by arranging _both_ particular software installations _and_ a timely Ubuntu upgrade to be downloaded to the "host folder" and installed from here without ever connecting, even once, to the Internet.  This possibility is left as a though experiment for the reader and may be addressed in future revisions of the Frankenwallet documentation.

Unless you have chosen to continue without that extra software and without a current update of the Ubuntu software baseline: 

➤ **connect your Internet cable now** *or* **turn on your regular WiFi** — and *get ready to disconnect it again* as soon as you get to the end of the instructions on this page.

Then execute:

```bash
sudo apt update
```
... to prepare for all the OS & essential application packages that have come out since the last Ubuntu official release.

{: .highlight-title }
> uncommon, but possible
> 
> If you get a message about having to run `sudo dpkg --configure -a` - usually seen after it reports a package glitch during the installation - do so now.  This may also happen if system is interrupted in the middle of adding or removing a package.

... and then execute ...

```bash
sudo apt upgrade
```

... to do all those installations (answer `Y` to confirm).

## Essential added packages

### Secure file deletion

```bash
sudo apt install secure-delete
```
This makes sure you can delete original key files in a way that zero-writes their file data, and randomises the directory entries before deleting them.

{: .important-title }
> question
>
> Why would we ever need to do this on the Frankenwallet, on which the entire drive is encrypted?

You _don't_ need this _for Frankenwallet files_... it's for the Frankenwallet to use on files *on the host computer* which may be accidentally written there unencrypted or improperly encrypted!

➤ What you'd do in that case: as soon as possible (before rebooting into that computer): random-write and then zero-write that file, as well as the directory entry pointing to it, to be sure it can never be accessed on the host machine even through unclaimed disk space:

```
srm mySecretFile
```

### AES encryption for both documents and archives {#libreoffice-7z}

The greatest benefit of the Frankenwallet is to use LibreOffice and the 7z archive for encrypted storage of keys and passphrases, or other confidential material about your transactions, private addresses, etc... given that you now have an environment on which to cold-encrypt these documents:

```bash
    sudo apt install libreoffice p7zip-full p7zip-rar
```

➤ Now you can ****disconnect again from the Internet****, and leave it unconnected indefinitely… until if and when you need to download any CLI software or install network dependent applications for a "cool" environment.

## Reboot (for the first time) {#first-reboot}

Especially for those with older or slower USB drives:
- Don't reboot by typing `sudo reboot`, or with `reboot` or `shutdown -h now` at a root prompt.
- The system is more likely to have type to `sync` the pending disk write (important to avoid having the fsck when booting) if you shut down via the GNOME interface.

{: .new-title }
> suggestion
>
> Simply click Power Off from the upper-right GNOME menu just to give it time to `sync` & unmount the root partition gracefully.
