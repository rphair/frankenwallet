---
layout: page
nav_order: 10
parent: Installation
title: Set up encrypted Ubuntu
---
# Set up Ubuntu encrypted drive
{: .no_toc }
- TOC
{:toc}

## Wireless & network settings {#settings-network}

There is **no need to disconnect from the Internet** or your router at this time, especially since this is not the "air gapped" system itself.

{: .note }
This installation procedure, with its standardised software environment built from an immutable ISO from a security vetted software baseline, is the overall safest Internet context in which to get Ubuntu software package updates (though you may choose not to do this) and the Internet will be disconnected immediately afterwards.

➤ **Wireless network** - therefore it's OK to use the one you regularly use.

## Updates and other software {#settings-update}

Select **Minimal software installation**, since this is the least likely to leave you with security intrusive applications and services.

➤ **LibreOffice** may be an item that we’re excluding: which we will need for our AES encrypted documents.  If that is so, don't worry since we'll have a chance to install it later: during the first boot of the Frankenwallet.

{: .highlight-title }
> Why?
>
> Arguably, it is less of a security risk to have one single connection to the Internet (immediately after first boot) —where packages like LibreOffice and other security tools can be installed — than to install these few items from the installation media: without that first connection, but with the larger package set in a "Typical" installation which contains a full array of insecure and network hungry desktop apps waiting for the first accidental Internet connection.

{: .warning }
Do *not* tick (as you normally would) the option for **third party hardware for graphics and WiFi**!

Unfortunately closed source can be subverted with no visibility or accountability: exactly the kind of subversion that we need to avoid the most.

It is unlikely that you would need the correct WiFi drivers to be installed in your Frankenwallet anyway (since you might arrange a cable connection during one-time or occasional software updates), and the Frankenwallet operations won't need any more than rudimentary graphics capabilities.

## Create a new Ubuntu partition on a fully encrypted drive {#encrypted-partition}

First, specify a brand new installation and enable the volume encryption.

➤ Tick **Erase disk and install Ubuntu**… don't worry yet about it wiping out your host computer, since it will ask you later which disk to install the system on, and because the external & internal drives are easy to tell apart.

![erase disk and install](/assets/images/011-erase-disk-and-install_cam.jpg)

➤ Hit the button below that option: **Advanced Features** which will say *None selected*.

- Tick the feature **Use LVM with the new Ubuntu installation**.
- Tick the option below it: **Encrypt the new Ubuntu installation for security**.

![select LVM with encryption](/assets/images/012-select-LVM-with-encryption_cam.jpg)

Don’t hit the **Continue** button unless you can verify it now says ***LVM and encryption selected*** under Advanced options:

![shows LVM with encryption selected](/assets/images/013-LVM-with-enryption-selected_cam.jpg)

➤ Enter the [high-security **Frankenwallet password**](/prepare/password-high) you have prepared in advance: as a **volume decryption key.**

- At this point you might want to check the password a few times that you can type it properly: either with consistency from written notes, or from memory.
- To double check in this installation environment: move over to the left (the "dock") where you'll see a text editor icon, in which you can practice typing the Frankenwallet password a few times.
- And if you *do* do this, keep in mind this should be *the first and last time* that password ever appears on a computer screen!

![set frankenwallet password](/assets/images/014-choose-volume-key_cam.jpg)

➤ **Overwrite empty disk space: Yes** is generally a good idea, although this only makes a difference to the visibility of old data that might be on the Frankenwallet drive.

- The warning “For more security” refers to the security *of data that was *previously* stored on this drive*… *not* the security of the data or environment that we’re creating anew.
- However, you never really know how artefacts of old software, viruses from indiscriminate use, or even institutional spyware on a brand new USB drive might cause security issues on your new operating environment… so it's best to be safe from any such code executing somehow by zero-writing *everything*.
- On the other hand if you have a 1TB memory stick or are preparing a massive Frankenwallet for a full Ethereum node, you may choose to back out now and find some other way of zero-writing the drive which doesn't tie up your host computer for so long.

➤ Finally, **choose the** ***external*** **drive from the list of available disks**:

![choose drive for frankenwallet install](/assets/images/015-choose-drive_cam.jpg)

{: .warning }
It might allow you to choose your host computer's internal OS disk and/or the drive with all your files on it without trying very hard to stop you!

So this is when you should recall the information you assembled in the ([host computer & media](/prepare/computer)) step:

{: .new-title }
> double check
>
> Make sure you have a match for both the size *and* the manufacturer of the external drive (sometimes shows as the manufacturer of the USB cable or hub it’s connected through).

➤ Hit **Install now** and **Continue** to confirm the partition creation.

➤ **Last chance to double-check** the media that they appear here… and go Back if you think any of these partitions are on a drive on your host computer:

![asks before deleting partitions](/assets/images/016-confirm-delete-old-partitions_cam.jpg)

{: .note }
You can get strange errors if you hit Back at the very last stage (this happened to me because I wanted to get 1 or 2 more screenshots).

If you get a message something like “cannot create LVM group” or “volume group”, it means the installer has lost track of the volume decryption key you entered… so you'll have to restart the system, boot from the Ubuntu installer, and repeat the steps above.

## Enter user level information for the Frankenwallet OS {#user-info}

➤ **Select local time zone**.  If you want UTC (to match timestamps on your node software, for instance), and it's not available on the "map" method of selection, you'll be able to set that later when you boot the Frankenwallet (next section):

![select geographical location from map](/assets/images/017-select-country-and-time-zone_cam.jpg)

{: .new-title }
> tip
>
> Selecting the country that matches your *current* location will greatly improve the speed of installation & updates, since it chooses package repository servers based on your answer here.

**Enter user information** with your particular choices of username and "real life" name:

![choose username password and login method](/assets/images/018-set-user-and-login-details_cam.jpg)

➤ You should enter the high-security (Frankenwallet) password also for your user password.

- This means anyone using your device when it’s unattended will have to enter your password to escalate to root privileges.

➤ Tick the option “Log in automatically” — rather than the generally better default “Require my password to sign in”).

- Since this goes against typical desktop security recommendations, consider that nobody can get into the Frankenwallet environment without booting up with the same password (set as your volume decryption password).
- Therefore, by logging in automatically, you're avoiding having to enter your (hopefully) very long & complex password **twice** every time you use the Frankenwallet.

Upon confirming the user details, you will see this slide show (with progress indicator below) as it proceeds with the installation:

![image confirming installation has begun](/assets/images/019-installation-under-way_cam.jpg)

… and when it successfully finishes:

![ubuntu installation process finished](/assets/images/020-installation-complete_cam.jpg)

➤ Remove the boot media when prompted.

{: .warning-title }
> very important tip
>
> Don't remove the Frankenwallet by mistake!

![remove installation media](/assets/images/021-remove-install-media_cam.jpg)

...and get ready to boot the computer from the _still-connected_ Frankenwallet.  **Before you continue**:

➤ **Disconnect your network cable**, and if it's practical you can also turn off your router and/or its WiFi connection, since the network dependent part of the OS installation is over (pending one more connection after booting for software download).
