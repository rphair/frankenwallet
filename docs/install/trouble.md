---
layout: page
nav_order: 60
parent: Installation
title: Troubleshooting
---
# Errors and difficulties you may see

(so far just based on the author's own experiences when this project began in 2020)

{: .new-title }
> contributions welcome
>
> This can only ever be a partial list of difficulties with the above procedures, not intended to be complete since this isn't a manual on Ubuntu configuration or dual-booting.  Quick solutions to common problems in this section that would help other Frankenwallet installers are welcome for [submission through the repository](https://github.com/rphair/frankenwallet).

`wspanish` (or other unnecessary) package can’t be added during installation time... this is harmless & can be ignored.

- errors seen during installation (inconsequential) in 20.04.1 release
- in this case, the `wspanish` package had a dependency problem.
- Generally: if the Ubuntu installation stops to complain about such a package, just ignore the problem and click Continue.
- Any dependency problems found in the installation are almost guaranteed to be cleaned up the first time doing an `apt update` in the booted system.

`snap` won’t go quietly

- Some Linux distributions install LVM as a snap, and for these we may have a dependency problem.
- I managed to scuttle one system by removing one of the snaps, even though it wasn’t LVM.

asked to "run fsck manually on root” to start after a disk check failure

- likewise if writes fail, and you try to save a file in the shell and it says "read only file system”
- we've had no positive results from actually running `fsck` on root as it suggests.
- therefore best to *reboot* when you see this message
- If you see this message repeatedly, you probably have to reinstall... another argument for saving all Frankenwallet files in either high- or low-security encrypted backups on the host machine.

if you can't Restart or Shut Down after you get in that "read only" state, it's no problem powering off.

- No point doing a "sync" since any further writes to the disk are impossible: therefore you're not losing anything further by powering off the machine (without being able to shut down, in fact it's the only thing you can do).
