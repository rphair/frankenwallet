---
layout: page
nav_order: 30
title: Preparation
---

# Prepare to create the Frankenwallet

## Frankenwallet security & operational terms

Some definitions before we begin:

### cold environment
An operating system installation in which the Internet is never connected, which has all necessary operational tools available without requiring Internet use.

### cool environment
(a term coined for this documentation) A security restricted environment intended for barely enough Internet use to support a node wallet (e.g. Daedalus in Cardano), light wallets (e.g. Eternl in Cardano), and/or blockchain tools requiring an Internet connected node.

### hot environment / host computer {#hot-environment}
Your machine for daily, unguarded Internet use: assumed (since it can never be proven otherwise) to be compromised with software that can automatically steal any unencrypted cryptocurrency private key files… and perhaps intercept encryption passwords as you enter them.

This is the computer from which you will boot the Frankenwallet.

### host folder / host directory {#host-folder}
A folder / directory on the host computer where you keep the bulk of the files read by, and written from, the Frankenwallet, for use in your cryptocurrency operations… including:

- unencrypted files, notes, and web pages saved for offline use (like these installation instructions, or the CLI command templates)
- **low security files** - encrypted with *any* complex password you might encrypt files with on the host computer — therefore, these may be decrypted directly on the host machine (but should not be stored unencrypted there).
- **high security files**, or **cold keys** - encrypted *with the Frankenwallet password*, which should be of unassailable length & complexity and must **never** be entered on the host computer — therefore, the files are only put on the host machine with the intention of backing them up.
- Such an organisation of the host folder will allow the entire profile of your secure cryptocurrency operations to be backed up along with the rest of your host computer's data.
