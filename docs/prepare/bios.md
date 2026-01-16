---
layout: page
nav_order: 20
parent: Preparation
title: BIOS settings
---
# Check your BIOS settings
{: .no_toc }
- TOC
{:toc}

## 1. Ensure your computer boots in UEFI mode (if possible) {#use-uefi}

Most computers in use today — unless they are more than several years old or have been deliberately set to "Legacy Mode" to support older OS installations — boot operating systems with UEFI.  This allows booting information to be kept in a single disk partition shared by multiple operating systems.

The alternative is called (ambiguously) BIOS mode: in which much simpler boot parameters are stored in the first block on the disk.  Any Windows or Linux installation today will _always_ install systems to boot in UEFI mode unless the disk partitioning or BIOS settings make this impossible.

Still, most modern computers can be forced to boot in "Legacy mode" — which, in the days of almost universale UEFI booting, is another term for "BIOS mode" — if the BIOS parameters select this as a default and/or a manual booting process forces it to look for a BIOS boot block on the connected drives.

Since your first priority is for your Frankenwallet to work on _your_ computer, it's not likely that you'll have to change the Legacy Boot parameter in your BIOS settings.  If you're like most users today (as of 2025) Legacy Boot is only a little-used compatibility flag in case you connect a standard computer to a _very old_ bootable drive.

{: .note }
If you **do** (inadvertently?) install your Frankenwallet on a computer in Legacy / BIOS mode, it won't have a UEFI partition and therefore will only work on computers set up to boot in Legacy Mode.

{: .warning }
**If** you have one of these very old systems, **and** you unset Legacy Mode so you can boot your system with UEFI for a proper Linux installation on your Frankenwallet, you will likely lock yourself out of the older host operating system that you had been booting.

➤ If you are in this latter unusual situation, at this point it would be an operational advantage to upgrade that older OS — generally also reinstalling its disk with a modern (GPT) partition table — to assure proper UEFI booting, more extensible disk partitions, and other modern conveniences.

## 2. Ensure an ideal boot order for booting from removable media {#boot-external-first}

{: .warning }
As mentioned several other places in this guide, unless you are willing to take [extraordinary security measures](/install/internal) your Frankenwallet will be built with an unencrypted `/boot` partition: meaning that a compromised system could tamper with the files there and "hack" your Frankenwallet.

{: .important }
Therefore, the general advice is to **never insert the Frankenwallet into your host system or any other running system**.

To help avoid doing this accidentally — _and_ to make switching into the Frankenwallet from your host system more convenient — you can adjust your host computer's BIOS settings to **move the USB / removable disk higher up in the "boot order" or "boot priority" than your computer's disk**.

In this case, if your Frankenwallet is still connected when your computer boots, it will try to boot into the Frankenwallet rather than starting your insecure system and potentially violating the unencrypted `/boot` partition of the still-attached Frankenwallet drive.

## 3. Feel free to use Secure Boot: but if in doubt, turn it off {#secure-boot}

If necessary, familiarise yourself with this institutionalised feature of commercial boot environments: **[UEFI Secure boot](https://wiki.ubuntu.com/UEFI/SecureBoot)** — 
which you can think of as a security measure to avoid the `/boot` file tampering described in the previous section.

Sometimes older systems, or Linux PCs long detached from the influence of Microsoft Updates, will have a BIOS version whose Secure Boot mechanism doesn't recognise the signatures of a newer system's boot images.

{: .new-title }
> hint
>
> If your first boot of an installed Linux, or any boot of your Frankenwallet on a different system, indicates a "Secure Boot" problem, the most effective way of solving the problem is to return to the BIOS settings and **disable the "Secure Boot" flag**.

For more competent users looking for a more deliberate solution while still preserving this "security" feature (a complicated choice, considering it comes from the same institutions who [allow BIOS itself to be tampered with](https://learnlinuxandlibreoffice.org/news/the-fight-for-a-secure-linux-bios)):
1. First, you can follow standard references like the documentation link above to somehow ensure your Ubuntu (Debian, Mint) boot images are properly signed.
2. When this appears to be effective, you should be able to turn Secure Boot mode back on.
