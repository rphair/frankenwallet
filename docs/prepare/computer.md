---
layout: page
nav_order: 60
parent: Preparation
title: Host computer & media
---
# Prepare your host computer & media

## Download the installation media

This goes best with a second memory stick.  Prepare this according the current instructions here:

➤ Create a bootable USB stick [on Ubuntu](https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu) or [on Microsoft Windows](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows)

Note there are instructions to do this [on macOS](https://ubuntu.com/tutorials/create-a-usb-stick-on-macos#1-overview) but, according to the constraints already described [here](https://cosd.com/frankenwallet/prepare/hardware), an persistent Ubuntu installation (e.g. the Frankenwallet) may not be bootable from a Mac without substantial and expert modification (we are still trying to find a procedure that will work for this).

## Recommendations for the host computer

Check how to boot off other media if you don't already know.

If you've never done this before, it certainly helps to have Internet access while you are looking this up.  You'll have to boot off other media twice — once into the Ubuntu installer, then again into the Frankenwallet — so learn as much about this process as you can.

{: .important-title }
> idea
>
> If not sure you can check the [BIOS settings](/prepare/bios) again to make sure the boot devices you need (especially USB) are enabled *and* in a convenient order of which to boot first.

➤ **Do a full backup** of every partition… or at least all your personal data stored in all those partitions.

The Linux installation procedure allows any partition to be overwritten.  There are some checks to be sure that doesn't happen accidentally but they can be confusingly worded.

Obviously you'll be pointing the OS installer at the Frankenwallet memory stick… but if that device is selected incorrectly, or if you force through any warnings about overwriting an active partition (and you cannot depend on those warnings), you might end up overwriting your active host operating system or other essential partition with a new version of Linux!

➤ **Check and note the sizes of all partitions** on the host computer, as well as the memory stick you're installing the Frankenwallet *and* the second memory stick you're installing Ubuntu from.

This will make it less likely to confuse these partitions during the installation procedure.  Most disks will also show the vendor / manufacturer, which can also be used to tell the disks apart during installation.

➤ Create a [**host directory / folder**](/prepare/#host-folder) (if you haven't already) which will have the bulk of your files read & written from the Frankenwallet.

You can begin using that folder by saving key web pages from the the next section ([**Installation**](/install) in that folder, to make it easier to continue the Frankenwallet configuration — from the booted Frankenwallet itself — without connecting to the Internet.

{: .new-title }
> tip
>
> In the future, *any* Internet based instructions can be saved in the host folder, so they can be followed in the air-gapped environment without having to reconnect to the Internet.
