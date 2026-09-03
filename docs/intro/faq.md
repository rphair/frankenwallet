---
layout: page
nav_order: 70
parent: Introduction
title: Other initial questions
---
# Miscellaneous FAQ's

## I have a second machine and I don't mind keeping it around: can I use these instructions to build it? {#second-machine}

Yes!  Nothing about the [default OS installation](/install/process) requires installing on a memory stick... but it does overwrite the *entire* primary boot disk (if not a memory stick, the disk of your "second machine").

That means you cannot install the Frankenwallet directly on a PC hard drive — even in the common dual-boot conformation with Linux and Windows each on their own partitions — without following some form of the [Advanced: internal disk partition](/install/internal) procedure.

## Don't I get enough security isolation from running VirtualBox on my usual host computer? {#no-virtualbox}

No!  You might be able to confirm that a VirtualBox, VMware, or any other virtual machine image has no access to the host environment, but *not the other way around*.  This means a virus infected or exploited host system can still potentially access your VM's files (including keys) as well as read passwords and seed phrases through logging keystrokes or reading the screen of the VM.

## Why are we installing full blown Ubuntu + heavyweight GNOME rather than lightweight [Xubuntu](https://xubuntu.org/) with XFCE? {#why-not-xubuntu}

XFCE probably would save about 1GB of RAM and a lot of disk bandwidth across the already strained USB interface.  Still, this might not be worth it because:

- Ubuntu has better support for the installer, especially with unusual disc configurations like putting the OS partition on a memory stick.
- For first time or new Linux users, there is more documentation based on the GNOME UI than for XFCE and its own default applications.
- Ubuntu, also common to VPS (cloud server) configurations, is explicitly supported in building `cardano-cli` on your (hopefully secure) VPS if you have one... so you wouldn't have to build it again on the Frankenwallet.

## What can an [Evil Maid](http://theinvisiblethings.blogspot.com/2009/01/why-do-i-miss-microsoft-bitlocker.html) do to compromise my Frankenwallet or its use on a host computer… i.e. if either equipment is covertly tampered with by a malicious and competent adversary? {#evil-maid}

Please consider whether the following risks are real enough to justify your choice of Frankenwallet vs. other platforms, noting that all these risks also apply to a "second air-gapped machine" as well:

1. Your Evil Maid temporarily steals your Frankenwallet and installs something in the unencrypted `/boot` partition that intercepts your [device decryption password](/prepare/password-high) as you type it... _and then_ steals it again once able to decrypt your main partition and read your files.
  - Note this is not a risk if your system boots with UEFI and therefore was able to encrypt the `/boot` partition as well as the OS partition when the Frankenwallet was created.
2.  Your Evil Maid sneaks onto the computer where you use the Frankenwallet and patches in a malicious BIOS that can log the key presses even as they are entered into programs that are loaded by GRUB (including the LUKS prompt where you enter your drive's decryption password).

Therefore you should make sure that no super-hacking Evil Maids are ever able to physically get to the Frankenwallet *or* the computer(s) that you use it on.  More seriously, and generally:

{: .warning }
If and when using the Frankenwallet on a physically insecure public computer, keep in mind the risk that computer might have a tampered or institutionally compromised BIOS.

{: .new-title }
> tip
>
> If you are fluent enough in Linux to use it in your daily workflow and build & rebuild systems, and the subject of more tamper-proof encryption interests you, please read and consider following at least some aspects of the alternative configuration at [Installing the Frankenwallet on an internal disk partition](/install/internal) — mainly addressing the challenges of encrypting the `/boot` partition.
