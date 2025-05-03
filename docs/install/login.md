---
layout: page
nav_order: 20
parent: Installation
title: First boot & login
---
# Booting the Frankenwallet
{: .no_toc }
- TOC
{:toc}

##  What you see when Frankenwallet is booted for the first time {#first-boot}

The Linux boot utility GRUB will have been configured to boot all the operating system that it finds when the Ubuntu OS of the Frankenwallet has installed.  This means:

- The boot selections will be valid on the host computer where you installed the Frankenwallet, but generally will not be valid for any other machines...
- If a second Ubuntu appears on the GRUB menu (as in the screenshot below), it means Ubuntu was also installed on the host machine where the Frankenwallet was created.
- The **Advanced options for Ubuntu** will only be valid if you upgrade the kernel on the Frankenwallet.  This may happen only once (in a one-time software upgrade) and is only useful if an upgrade installs a kernel which leaves your Ubuntu unable to boot (which itself would be very rare).

{: .warning }
> Generally you should never select anything but the first item on the List (just **Ubuntu** by itself). 

You can ignore the other selections… there is no security reason to boot a host partition from the Frankenwallet boot menu _and_ there could be undefined security risks by doing this.

![grub boot menu from frankenwallet](/assets/images/022-grub-menu-on-frankenwallet_cam.jpg)

## "Logging in" to Frankenwallet {#login}

{: .note }
This also decrypts your drive with the LUKS password.

Then, after the system fully boots, the recommended settings on the previous page will log you in automatically without a password: since you have already entered the highest security password.

{: .new-title }
> hint
>
> The **unlock disk** prompt is a good point to remember (in the future) to **disconnect the network cable** if this is a part of your security posture (but don't do this now).

... Soon you'll have a chance to disable both these connections in software (via _Airplane mode_) so they are off by default in the Frankenwallet.

➤ Enter the High Security password you entered in the Ubuntu set up as the **volume decryption password**:

![prompt for frankenwallet luks decryption password](/assets/images/023-decryption-password-prompt_cam.jpg)

How it will look if you enter an incorrect disk decryption password:

![response from entering luks password wrong](/assets/images/024-decryption-password-wrong_cam.jpg)

How it looks after you enter the disk decryption password successfully:

![response from entering luks password correctly](/assets/images/025-decryption-password-correct_cam.jpg)

## FYI: File system checking (`fsck`), with delays on older and slower drives {#fsck}

You won't see this the first time (because the root filesystem hasn't been booted yet)… and you may never see it if you have a fast USB connection with good write bandwidth… but perhaps on future logins if you've built the Frankenwallet on a slow USB drive:

![message displayed during disk check](/assets/images/026-fsck-decrypted-volume_cam.jpg)

If your equipment is as impoverished as ours in the [first version of the Frankenwallet](/intro/name)… i.e. with a rotational drive over USB 2.0… then you can expect it will need to do this every time.  Even in this *extreme* case the disk checking command (fsck) would complete in no longer than 90 seconds.

➤ However we have every reason to believe that SSD-based drives including memory sticks will be fast enough to `sync` the disk buffer cache every time the wallet is shut down... so you shouldn't see this message unless the power was shut off before normally shutting down the Frankenwallet.

- Therefore in either case, you have no choice but to allow this process to finish and succeed every time.
- **If you do press Ctrl+C** as offered, it's likely you'll get a read-only filesystem and will have to reboot the Frankenwallet anyway.
