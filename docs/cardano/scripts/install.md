---
layout: page
nav_order: 10
parent: Cardano SPO Scripts
title: Installation
---
# Installing the SPO Scripts in your Frankenwallet
{: .no_toc }
- TOC
{:toc}

## Install & configure the software {#software}

{: .warning }
Since your Frankenwallet and host machine are sharing drives, you _must_ install the SPO Scripts on the Frankenwallet disk and ***not* the host machine** disk.

Why?  Since scripts can be changed so easily — and have many lines of code that operators couldn't comb all the time for intrusions (though you can [verify their checksums](https://github.com/gitmachtl/scripts/tree/master/cardano/mainnet#how-to-installcopy-the-scripts)) — we have to avoid the possibility that a compromised host system could add back doors, key extraction, and other malicious code into the SPO Script files.

This point isn't stressed in the SPO Scripts repository, since there it's understood you'd only be installing the offline scripts on a physically separated, dedicated machine that doesn't share disks with any other machine having Internet access: and therefore there would be no opportunities for tampering.

{: .highlight-title }
> be careful
>
> In general (applying to _all_ Frankenwallet usage, not just the SPO Scripts), you should ensure host directories are **not** included in the execution `$PATH` inside the Frankenwallet: since this could carry such tampering into an otherwise protected environment.

However, operators should be completely assured that offline SPO Scripts that operate on private keys in the Frankenwallet will be tamper-proof *as long as they're **only** installed there*.  And according to their [security model](https://github.com/gitmachtl/scripts/tree/master/cardano/mainnet#online-mode-vs-light-mode-vs-offline-mode) the consequences of tampering with the *online* SPO scripts wouldn't be as serious.

### Install script package from your host folder {#install-package}

(This adapts the SPO Scripts doc section [How to Install/Copy the Scripts](https://github.com/gitmachtl/scripts/tree/master/cardano/mainnet#how-to-installcopy-the-scripts) for the Frankenwallet.)

➤ With your host machine booted normally, download the [ZIP Archive](https://github.com/gitmachtl/scripts/archive/master.zip) into your [host folder](/usage/host-folder).

{: .new-title }
> tip
>
> It's marginally better to keep it as a compressed file in the host environment, rather than uncompressing it there: to avoid presenting the scripts, which can be more easily tampered with than a compressed archive, to the insecure system.

➤ Reboot into the Frankenwallet.

➤ Identify or create a `bin` directory that isn't on your host machine's disk (as explained above).

The home subdirectory `~/bin` is a good choice since it's already in the default `$PATH`: if using a different location, ensure you add it to `$PATH` by editing `~/.profile` accordingly.

Remember you can run `df .` (to show the filesystem where you currently are) any time you need to confirm you're on a Frankenwallet disk instead of your host computer's disk.

➤ Extract the contents and copy all the files in `scripts-master/cardano/mainnet` into that `bin` directory; for example:

```  
cp scripts-master/cardano/mainnet/* ~/bin  
```

### Put SPO scripts in [offline mode](https://github.com/gitmachtl/scripts/tree/master/cardano/mainnet#online-mode-vs-light-mode-vs-offline-mode) and finish configuration {#offline}

Continuing the [configuration instructions](https://github.com/gitmachtl/scripts/tree/master/cardano/mainnet#configuration-scriptfiles-syntax--filenames), edit the main configuration file `00_common.sh` in the scripts directory:

➤ Early in the file, set `workMode="offline"` (vs. the other two choices `"online"` and `"light"`): to match your air-gap configuration and the Frankenwallet's secure place in your workflow.

➤ In the section after that, ensure the variable `cardano-cli` (plus any others, if necessary) points to the place where it's actually installed (if not in the same `~/bin` directory as suggested).

## Import pool data from any existing pool {#import}

Your installation is finished here if you intend only to use the Frankenwallet + scripts to create a *new* stake pool.

Otherwise: to administer your existing pool, follow the SPO Scripts doc section [Import your existing data in Offline-Mode](https://github.com/gitmachtl/scripts/tree/master/cardano/mainnet#import-your-existing-data-in-offline-mode) — to create a subdirectory containing all of your pool data — with these added precautions to avoid installing sensitive data where it won't be shielded from the host machine:

### Before the import process {#import-before}

This documentation section (you may have to click **▸ Show Example** if it's not displayed) requires that you *choose a directory* to consolidate all your pool files.

{: .warning }
Do NOT put this directory in your host folder, or anywhere on your host machine!

As we had to check with the SPO Scripts themselves, it's even more important that we ensure your *keys* are kept on the Frankenwallet's own encrypted drive.

Generally this will happen automatically, since your Frankenwallet home directory and system are all encrypted... and so all files created there will be safe unless you've changed to a directory or file manager window on one of the host computer's disks.

If there's any doubt, any time you need to ensure you're not in the host folder nor _any_ part of the filesystems on your host machine:

1.  run `df .` from your shell, or in a Terminal opened in that file manager window;
2.  check the Filesystem shows as the virtual device for your encrypted Frankenwallet partition (beginning with `/dev/mapper`) rather than a raw disk device on your host computer (e.g. `/dev/sd*` or `/dev/nvme*`).

### After the import process {#import-after}

Once all your pool data is arranged in a single place, you can follow the procedure to [Back up the SPO Scripts pool directory](/cardano/scripts/usage/#backups) to generate a securely encrypted backup that can be shared with external backup devices & networks.
