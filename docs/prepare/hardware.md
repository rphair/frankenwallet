---
layout: page
nav_order: 10
parent: Preparation
title: Hardware requirements
---
# Hardware requirements
To create the basic Frankenwallet you will need both these 2 things:

## 1. a USB removable, writable disk {#hardware-1-disk}

with the following qualifications:

{: .highlight }
**USB revision**: the fastest supported by the host computer(s) you will most commonly use.

You should have one of these:
- USB 3.1 — if your computer is very new (otherwise the 3.1 drives are sometimes not recognised on earlier USB ports built for the 3.0 standard)
- USB 3.0 — otherwise (since the speed improvement will be *huge* vs. USB 2.0, and the USB protocol will always fail back to 2.0 if a much older machine doesn't support 3.0)

USB 2.0 memory sticks, including [absurdly obsolete configurations](/intro/name) (e.g. HD SATA drives with a USB cable) will also work with Frankenwallet... though in these cases you should be patient enough for a 1-2 minute `fsck` on every boot.

Note not all drives with the same USB revision have the same real-world speeds.  If you have the option of choosing your memory stick for a fast Frankenwallet, I recommend going to [USB UserBenchmark](https://usb.userbenchmark.com/) to look for the highest possible read/write bandwidth.

{: .highlight }
**Size of drive**: a 32 GB is more than adequate as long as you intend only to support the Cardano CLI or a secured light wallet.

This includes, with a generous margin:
- 8+ GB for a sparse Ubuntu desktop partition
- 12+ GB in case you want to _build_ the Cardano node in the Frankenwallet (not required or recommended)
- plenty of room leftover for:
  - other blockchain software and toolkits
  - operational data & backups you want to keep securely on the Frankenwallet.

An SSD drive attached over SATA would be required to run a node wallet effectively in the Frankenwallet.  Required sizes, at the time of site last update:
- [for Cardano](https://developers.cardano.org/docs/get-started/cardano-node/installing-cardano-node#hardware-requirements): a 512GB drive
- [for Ethereum](https://etherscan.io/chartsync/chaindefault): a 2TB drive

We hope to provide estimates for other blockchain environments as soon as we can test them: in the meantime you are welcome to make suggestions [here](https://github.com/rphair/frankenwallet).

{: .highlight }
**a second memory stick**: used _once_ in the installation.

Note this is not essential (since you can install from optical media, TFTP boot server, etc.) but most people will want to use one.  Only 8GB capacity is needed, and the slowest ones on the market will be fine for this purpose.

## 2. a Windows PC to attach it to {#hardware-2-pc}

{: .note }
If you have a made-for Windows PC — whether it runs Windows, Linux or both — you can skip to the next section. 😎

### What if I have a Mac?

Since the conception of the Frankenwallet in 2020 we haven't have enough Apple machines available locally to test whether the boot software on an Apple desktop or laptop will ever properly recognise a bootable Linux partition (either legacy / GRUB or UEFI) on any removable media without specially formatting it with a tool like [Etcher](https://www.balena.io/etcher/):

- Etcher may work very well for the installation media itself, but the Frankenwallet is not just *bootable*… it is [persistent](https://askubuntu.com/questions/295701/what-would-be-the-differences-between-a-persistent-usb-live-session-and-a-instal) — with a live, modifiable file system — as well as created dynamically.
- So **we know of _no way_** that a boot disk creation tool like Etcher, designed to work on fixed ISO images, could ever make the Frankenwallet bootable after its creation through the Ubuntu installation process.

Again, we hope Apple Mac users interested in the Frankenwallet will find some approaches to this problem and report on their learning experiences [in the repository](https://github.com/rphair/frankenwallet) somehow.  In the meantime we hope the following links will provide some good starting points:

- [How to Boot a Linux Live USB Drive on Your Mac](https://www.howtogeek.com/213396/how-to-boot-a-linux-live-usb-drive-on-your-mac/)
- [Create a bootable USB stick on macOS](https://ubuntu.com/tutorials/create-a-usb-stick-on-macos#1-overview)
- [How to Create and Boot From a Linux USB Drive on Mac](https://www.makeuseof.com/tag/how-to-boot-a-linux-live-usb-stick-on-your-mac/)
- [How to Install and Dual Boot Linux on Your Mac](https://www.makeuseof.com/tag/install-linux-macbook-pro/) - suggests how you might set up the encrypted Linux partition by hand.
- if Mac can't use GRUB it should be able to use [rEFind](https://sourceforge.net/projects/refind/)...?
- [Adding Encrypted Persistence to a Kali Linux Live USB Drive](https://www.kali.org/docs/usb/usb-persistence-encryption/)
- [mkusb](https://help.ubuntu.com/community/mkusb) - general tool to create boot drives
