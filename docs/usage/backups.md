---
layout: page
nav_order: 30
parent: Usage
title: Backups
---
# Backups from Frankenwallet to host machine (and beyond)
{: .no_toc }
- TOC
{:toc}

## How to back up, and verify backups of, your low-security and high-security key folders
{: .no_toc }

Whether you're a cryptocurrency business operator (e.g. an SPO [stake pool operator] for Cardano) or an asset holder (on any blockchain(s)), the cryptocurrency keys you keep will generally fall into two groups:

1. verification keys, which are intended for exposure to the public: these are [low-security keys](/prepare/password-low).
2. signing keys, which are used to prove your identity or ownership of your resources: these are [high- security keys](/prepare/password-high/).

If you keep these separated into two groups, and only extract the "verification" keys when you might need them (while leaving the "signing" keys untouched outside the Frankenwallet:
- your host computer files will not reveal anything about the nature of the information stored in them, _and_
- you won't risk the exposure of the private keys every time you access one or more of the public keys.

➤ Choose a file name for each of these these 2 archives that mean something to you, and which you will *never confuse* between the two security levels of low- and high- security keys.

The Frankenwallet is the best place to ensure you associate each password with each archive: because you *never* want to be entering that Frankenwallet password on your host environment by mistake!

{: .new-title }
> hint
>
> When naming your crypto key archives on your host computer (assumed compromised, likely to be backed up into the cloud, etc.): don't call them e.g. `crypto-keys.7z` or anything that looks like an attractive target to hackers or spooks.

## Backup creation

➤ If you haven't already, designate a working directory for your crypto operations in the Frankenwallet: e.g. a folder created on the desktop.  

For each set of keys (low and high security):

➤ Move the keys into a folder (e.g. `top` for high security, `bottom` for low security).

➤ In the File Manager: select all those keys, right-click on them, and select "Compress" from the menu.

➤ Select `7z` (for which you [installed the package](/install/packages/#libreoffice-7z) in Ubuntu setup), and tick the boxes for
- use a password
- hide the files unless the password is entered (otherwise malicious users might be able to tell these are cryptocurrency keys, even if they can't open the archive)

This will leave you with two files: e.g. `top.7z` and `bottom.7z`.

{: .important }
Make sure you keep each of these encrypted archives side-by-side with the directories they were made from: so you can keep them updated more easily (when keys are updated, added or removed) by comparing the `*.7z` file modification times with the modification times of the directories or contents.

➤ Finally, copy each of these encrypted archives from the working directory on your Frankenwallet to your Host Folder.

From there, these files should be able to face the outside world: on memory sticks, cloud backups, CD / DVDs, and perhaps even email.

{: .note }
The AES encryption algorithm used by `7zip` (also LibreOffice), until there are substantial advances in quantum computing, would still require a cosmic-scale computer to "break" — but only if the encryption password itself is never exposed through your operating environment.

{: .new-title }
> hint
>
> For very cautious users and operators — if worried about deleting a vital file like a payment address key — older copies of the encrypted archives can be kept in a subfolder so old versions of archives and keys can still be retrieved.  

## Backup verification & correcting mistakes 

Some tools & methods you can use, _besides_ simply comparing the modification times of the two `7z` files, to determine that the file in your Frankenwallet is the same as the one on your host computer (especially if the modification time on the host computer is lost, as often happens on Windows filesystems):

### `md5sum`

Run, in a terminal on both your Frankenwallet working folder an host folder:

```bash
`md5sum top.7z`
```

The slightest difference in a file will produce a completely different output (a 32 hex-character hash): so you can tell when the files are different... and you can examine both files to determine which is correct, complete, or current: and then update the other.

### `srm`

Recall the [installation of the `secure-delete` package](/install/packages/#secure-file-deletion) - so in case you accidentally move your unencrypted (or improperly encrypted) keys or key folder to the host machine, you can **remove every trace of the file**{: .text-red-300} before your host computer starts again.  
