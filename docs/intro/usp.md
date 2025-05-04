---
layout: page
nav_order: 10
parent: Introduction
title: What's unique about it?
---

# What's unique about it?

## Your removable drive is used to provide rich features and security isolation, rather than simple file transfer.

To quote [a popular stake pool creation guide](https://forum.cardano.org/t/moving-and-installing-cardano-cli-to-cold-environment/64631/8?u=cosdpool) in 2021:

> “*In order to remain a true air-gapped environment, you must move files physically between your cold and hot environments with USB keys or other removable media.*”

The Frankenwallet demonstrates this is **not true**, because:

{: .highlight }
When booting this "cold" air-gapped environment created on "USB key or other removable media" you are able to read and write files natively on the usual hard drive of that "hot environment" — so those files are never moved physically at all.

This creates an opportunity to save those high-security files on the hard drive encrypted with a [maximum-security password](/prepare/password-high), used as the basis for AES encryption (via LibreOffice or the 7z archive utility): a password which has never been entered via that hard drive's operating system (or anywhere else outside the Frankenwallet!).

File encrypted as such can be even backed up with impunity — to regular backup media from the host computer, over the Internet, with cloud services, even emailed — which safeguards the financial and operational components of a user's cryptocurrency portfolio and/or staking enterprise from theft, fire, or other unpredictable loss, damage or destruction.

{: .note }
This makes the choice of the highest-security password — both for the encryption of the Frankenwallet partition and the high-security files it saves on the host machine — paramount, along with the restriction *never* to enter that password outside the Frankenwallet… this restriction is discussed further below ([Preparation \> High Security Password](/prepare/password-high)).

In short: Your memory stick becomes more than just a way of saving and transferring files… to be used as an interactive component of your security architecture while completely replacing a "cold" computer with a very small form factor.
