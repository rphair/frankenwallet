---
layout: page
nav_order: 30
parent: Installation
title: Secure system settings
---
# Secure your encrypted partition against any Internet usage
{: .no_toc }
- TOC
{:toc}

## Refuse *everything* from **Welcome to Ubuntu** {#refuse-welcome}

This one should be obvious!  New desktop installations (even with Minimal software setup) have a program called **Welcome to Ubuntu**. which will try to set up all kinds of Internet relationships.

As per the GNOME application default, its menus appear as a tab all the way on the left on the top bar… but selecting *Quit* here currently has no effect. So you must answer these questions manually, hitting *Next* each time:

➤ **Do not** link with any **online accounts** (obviously).

➤ **Do not** set up **Canonical Livepatch** which would be almost as bad (you will satisfy its purpose — kernel upgrades — in one single update & perhaps others).

➤ **No** don’t any send **system information**.

➤ **Location Services** are **disabled** by default… of course leave them that way.

Finally. click *Done*.

## Disable automatic Internet connections {#disable-auto-internet}

Look for any WiFi button in the right corner.  If you see one (meaning you have one, and Ubuntu has found the driver for it), right-click and disable it:

- Menu selection will be to **Turn WiFi Off**.
- If you have **Bluetooth** you should also see a menu selection nearby to **turn it off** as well.

If your Ethernet port is live (most Ethernet cards have Ubuntu drivers) you won't see an icon here if your cable has been disconnected.  If it's connected (i.e., watch for this like a warning sign) you'll see an icon that looks like this:

![GNOME toolbar network icon](/assets/images/network-icon-54sq.png)

{: .note }
GNOME currently shows an Airplane symbol when both WiFi & Bluetooth have live connections but are turned off, which automatically engages "Airplane Mode" (don't ask me to explain why).

{: .new-title }
> hint
>
> It therefore can be a good security workflow habit to **confirm you see an airplane icon** whenever you use Frankenwallet on a WiFi capable system (unless using the "cool" Frankenwallet)

## Disable Settings for networking, indexing and power management {#disable-nanny-settings}

Open **Settings**, also from the upper right corner of the screen:

![system settings gear button upper left screen](/assets/images/gnome-system-settings-button.png)

under **Search**:

➤ Turn this **off with the top level switch** …note this list includes *Passwords and Keys*.

under **Privacy** you have to **turn everything off individually**:

- Screen Lock \> Automatic Screen Lock **off**, because:
  - Ubuntu is notorious for (and changes behaviour frequently of) power management plugins… impossible to change at the user level… putting the computer to "sleep" after a period of screen lock.  This can cause problems with your root drive syncing over the slower USB interface.
- Connectivity \> Connectivity checking **off**
- Location services: verify it is **off** as per the Welcome screen
- File History & Trash **off**
  - no need (yet) to hit *Clear History* button: just note that it's there.
- Diagnostics \> Problem reporting \>
  - Automatic Problem reporting: **off**
  - Send error reports to Canonical: **never**

under **Removable media** \> **Never** prompt to start programs on media insertion!

- (consequence: you leave an infected memory stick also in the computer when booting Frankenwallet, and aren't paying attention when it finds the other device)

under **Date & Time** \> Automatic Date & Time **off**

- Therefore you might want to check the time & set manually every once in a while... or, if you're doing software updates every now and then, sync the clock at that time.
- ****exception**** if you're running the "cool" Frankenwallet, to enable a blockchain node e.g. the one inside the Cardano Daedalus wallet: leave automatic Date & Time ON to provide a reliable time reference!

➤ FYI If your host computer normally runs Windows, but hasn't dual-booted with Linux yet:

- Windows sets the hardware clock in the local time zone, while Linux installs with the time on the **hardware clock in UTC** and assumes it remains that way.
- Therefore, to avoid time discrepancies in the Frankenwallet, the next time you're booted into Windows, follow the instructions here ([ArchLinux \> UTC in Microsoft Windows](https://wiki.archlinux.org/title/System_time#UTC_in_Microsoft_Windows)).

under **Power**:

- Set **Blank Screen** to **Never** (see reason ablve regarding Screen Lock).
- Set Automatic Suspend to off.

{: .warning }
If you ever see a **Hibernation** option _anywhere_, **turn it off**.

Unless you configured a swap partition in the Ubuntu installer you will never see this, since it needs contiguous swap space for the hibernation data (via a process which is notorious for being unreliable on Linux).

- So, if you've deliberately enabled swap and hibernation… keep in mind that swap space can't be encrypted, and therefore what's saved in hibernation might contain the cleartext of any data you're hoping to protect with the Frankenwallet.
- In general, the goal of hibernation works against the goal of encrypting your root drive.

## Disable automatic software updates {#disable-updates}

Run the **Software & Updates** app… you can find this by clicking on Activities in the upper left corner & typing part of the name:

![icon for software & updates app](/assets/images/software-updates-icon.png)

on the **Ubuntu Software** tab:

- The current Frankenwallet recommendation is to leave ticked or **tick the box for Community-maintained software**.
  - We'll only be installing packages from this repository by hand (e.g. `7z` encrypted file archiver).
- Make sure **Proprietary drivers for devices** is **unticked.**

{: .important }
Just because you didn't select Proprietary Drivers, as recommended in the [OS configuration step](/install/process/#settings-update), doesn't mean it'll be unselected here!

As explained in that step, the possibility these drivers may be subversive is more significant than any improvement to your display or enabling a WiFi you will generally never use.

➤ If your **Download from**: is not **set to the country** where you'll first be using the Frankenwallet (i.e. for the rest of this page), select it to improve your connectivity for package upgrades.

➤ If the **Installable from** media is still ticked here, untick it since we’ll never be connecting that installation media again.

on the **Other Software** tab:

- make sure both boxes are **un-ticked** for **Canonical Partners** (i.e. companies like Google, Microsoft, Adobe, Dropbox, etc… all having well known goals of compromising user privacy)

on the **Updates** tab:

- For **Install updates from** (explanation: [Ubuntu \> Repositories \> Updates tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Updates_Tab)):
  - **yes** tick **Important security updates** (to cover any bugs in the Ubuntu OS release you just installed)
  - **yes** tick **Recommended updates** (to cover severe operational problems as well)
  - **no** don't tick **Unsupported updates** (ports from future Ubuntu versions by individuals without the same security or operational testing)
- **Automatically check for updates: Never**

on the **Livepatch** tab:

- This is likely to be unavailable if you followed the recommendation of turning it off in the installation process… since it won't have been installed.
- If you see it available or enabled here, make sure it's turned **off**.

**Close** the window.

- If and when it pops up a message saying information about available software is out-of-date then **Close** that as well.
- Do not hit the Reload button here (especially since your Internet connection should still be off).

### What if it asks me to download packages when I know I'm not on the Internet? {#packages-stuck-in-apt-cache}
{: note }
If you ever see the _Software & Updates_ "app" appearing again automatically, with a pop-up about installing downloaded packages, *check everything again carefully* because this means at some point the computer was booted with a live network connection ***and*** settings to check for downloaded packages regularly.

If that is the case, it is a topic of current investigation how to clear these pending Ubuntu updates from the cache used by the `apt` package manager:

{: .new-title }
> help wanted
>
> Until that question is answered there is **no known way** of suppressing that dialogue — even if you never connect the Frankenwallet to the Internet again and flush the `apt` cache — so if you ever see that dialogue and manage to suppress it please post your solution to the repository.

## Confirm: is your /boot partition encrypted? {#is-boot-encrypted}

We offered this question for "expert" discussion here ([boot methods & encryption](/prepare/bios/#bios-2-experts)) and here now is your chance to find out for sure:

➤ **Run the** ***Disks*** **application** to see if the partition where the `/boot` filesystem was created — which should be the smallest one on your Frankenwallet memory stick — shows up as an LUKS partition.

- LUKS confirms it's encrypted: if you don't see that, then /boot is unencrypted & you should avoid putting this Frankenwallet ever into any booted system *or* leave your Frankenwallet in a system that's being booted some other way.

## Get ready for work at the command line {#settings-done}

That's it for the application level system settings (part 1 of 2).  The second part of this installation will be some finer work with packages (installations & upgrades)… including ***one*** judicious connection to the Internet.
