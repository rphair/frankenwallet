---
layout: page
nav_order: 60
parent: Introduction
title: Is software encryption OK?
---
# Is software encryption enough to secure my life savings or livelihood?

> *"some style to illustrate a dramatic quote: in skeptical user's own words"*


## ... NEW WRITING GOES HERE ...


## About AES implementations in the programs you will be using {#aes-implementations}

[LibreOffice](https://www.libreoffice.org) (for text documents & spreadsheets) and [7z](https://www.7-zip.org) (for archives) have sufficient longevity in the open source community that any real threat — revealing the password entered when data is encrypted or decrypted — would have quite a bit of exposure.  So the attack surface into your crypto data can be considered zero as long as nobody has "blown the whistle" on either of these programs having insecure password management… something I have been watching for for 12 years and never found.

Beyond that, the parameters for AES seem only to make a difference mathematically: practically, the cracking problem of brute-forcing the keys is either geological or cosmic (depending on whether you consider time or space).  So please stay most aware of the security issues as they relate to *passwords themselves*: as with all cryptographic systems, the most common attack points are where keys are set, verified, or exchanged… rather than breaking the cipher itself.

➤ This is why the high security requirement has been set so the password to encrypt private key archives, and documents with the seed phrases for user funds, is never entered outside the Frankenwallet and therefore cannot be observed… so any opportunity to intercept the password from a program failure or even a "zero-day bug" never takes place.

➤ Since these files and archives are never encrypted or decrypted outside the Frankenwallet or other stateless device, they cannot be exposed to password entry vulnerabilities… since all an attacker would ever see, when that data emerges in the host environment, is the fully AES-encrypted file.
