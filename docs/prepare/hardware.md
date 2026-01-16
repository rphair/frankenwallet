---
layout: page
nav_order: 10
parent: Preparation
title: Hardware requirements
---
# Hardware requirements
{: .no_toc }
- TOC
{:toc}

## 1. a USB removable, writable disk {#hardware-disk}

with the following qualifications:

{: .highlight }
**USB revision**: the fastest supported by the host computer(s) you will most commonly use.

You should have one of these:
- USB 3.1 — if your computer is very new (otherwise the 3.1 drives are sometimes not recognised on earlier USB ports built for the 3.0 standard)
- USB 3.0 — otherwise (since the speed improvement will be *huge* vs. USB 2.0, and the USB protocol will always fail back to 2.0 if a much older machine doesn't support 3.0)

USB 2.0 memory sticks, including [absurdly obsolete configurations](/intro/name) (e.g. HD SATA drives with a USB cable) will also work with Frankenwallet... though in these cases you should be patient enough for a 1-2 minute `fsck` on every boot.

Note not all drives with the same USB revision have the same real-world speeds.  If you have the option of choosing your memory stick for a fast Frankenwallet, I recommend going to [USB UserBenchmark](https://usb.userbenchmark.com/) to look for the highest possible read/write bandwidth.

{: .highlight }
**Size of drive**: 32 GB is adequate as long as you intend only to support the Cardano CLI or a secured light wallet.

This includes, with a flexible margin in each (since they'll all be on the root filesystem):
1. 15+ GB for a standard Ubuntu desktop partition
1. 12+ GB in case you want to _build_ the Cardano node in the Frankenwallet (not required or recommended)
1. plenty of room leftover for:
  - other blockchain software and toolkits
  - operational data & backups you want to keep securely on the Frankenwallet.

An SSD drive attached over USB would be required to run a node wallet effectively in the Frankenwallet.  Required sizes, at the time of site last update:
- [for Cardano](https://developers.cardano.org/docs/get-started/infrastructure/node/installing-cardano-node#hardware-requirements): a 512GB drive
- [for Ethereum](https://etherscan.io/chartsync/chaindefault): a 2TB drive

Estimates for other blockchain environments will emerge as soon as maintainers can test them: in the meantime you are welcome to [make suggestions](https://github.com/rphair/frankenwallet#community-discussion-questions-and-support) about other configurations to support.

{: .new-title }
> hint
>
> An **SSD drive attached over USB** (SATA or integrated) has shown the best performance ever observed on an external Frankenwallet (eSATA should be equally performant).

However, it can leave you with a lot of space unusable on the drive: since by default its `/boot` partition will be unencrypted & shouldn't be attached to a running system, since it would be vulnerable to tampering.  Advanced users can reclaim that space by [encrypting `/boot` on an external drive](/install/internal/#alternatives).

## 2. a second memory stick {#install-media}

... to be used _once_ for the installation.

This is not essential — since you can install from optical media, TFTP boot server, etc. — but typical admins will find it easiest to use one.  Only 8GB capacity is needed (still; as of 2026), and the slowest memory sticks on the market will be fine for this purpose.

## 3. a Windows PC to attach it to {#hardware-pc}

{: .note }
If you have a made-for Windows PC — whether it runs Windows, Linux or both — you can skip to the next section. 😎

### What if I have a Mac? {#mac-problems}

Since the conception of the Frankenwallet in 2020 we haven't have enough Apple machines available locally to test whether the boot software on an Apple desktop or laptop will ever properly recognise a bootable Linux partition (either legacy / GRUB or UEFI) on any removable media without specially formatting it with a tool like [Etcher](https://www.balena.io/etcher/):

- Etcher may work very well for the installation media itself, but the Frankenwallet is not just *bootable*… it is [persistent](https://askubuntu.com/questions/295701/what-would-be-the-differences-between-a-persistent-usb-live-session-and-a-instal) — with a live, modifiable file system — as well as created dynamically.
- So **we know of _no way_** that a boot disk creation tool like Etcher, designed to work on fixed ISO images, could ever make the Frankenwallet bootable after its creation through the Ubuntu installation process.

Again, we hope Apple Mac users interested in the Frankenwallet will find some approaches to this problem and [report on their learning experiences](https://github.com/rphair/frankenwallet#discussions).  In the meantime these links may provide some starting points:

- [Create a bootable USB stick on macOS](https://documentation.ubuntu.com/desktop/en/latest/how-to/create-a-bootable-usb-stick/#on-macos)
- [How to Create and Boot From a Linux USB Drive on Mac](https://www.makeuseof.com/tag/how-to-boot-a-linux-live-usb-stick-on-your-mac/)
- [How to Install and Dual Boot Linux on Your Mac](https://www.makeuseof.com/tag/install-linux-macbook-pro/)
  - suggests how you might set up the encrypted Linux partition by hand.
  - if Mac can't use GRUB it should be able to use [rEFind](https://sourceforge.net/projects/refind/)...?
