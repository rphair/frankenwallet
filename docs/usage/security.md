---
layout: page
nav_order: 20
parent: Usage
title: File encryption levels
---
# Ensure your documents and archives store cryptocurrency data with the correct level of security
{: .no_toc }
- TOC
{:toc}

These two scenarios are offered to illustrate when you would use the [high] or [low] security password in encrypting a LibreOffice document or `7z` archive of otherwise unencrypted files.

{: .important-title }
> TL;DR
>
> Any "low" security file or archive should be something you feel comfortable decrypting & reading on the host machine: knowing both the data & password could be exposed to hackers if you do... so if this would cause a catastrophic loss, use the "high" security password.

{: .new-title }
> help wanted
>
> There should be several more detailed user stories here — to fill out this page into a section on different types of secure workflow — so user and operators are welcome to share scenarios [through the repository](https://github.com/rphair/frankenwallet) if helpful for other users to achieve any security or privacy goal.

## Your highest security file: the one(s) containing wallet passphrases {#use-cases-high-security}

Encrypt any such file with the "high security" password for the Frankenwallet itself, as suggested earlier [here](/prepare/password-high).

This implies that you are in a cool environment in which a wallet has been initialised & can sync on the blockchain.  So you have a bit of Internet access — without full exposure — but you know that if you set that same wallet up on your Internet-exposed desktop that the copy/pasted wallet passphrase could be easily read.

Therefore as per the Frankenwallet standard, when setting up that wallet you use this encrypted LibreOffice file to store the wallet passphrases.

The passphrases remain secure because no part of that LibreOffice file will provide any clue about the password used to encrypt it... and you've never entered that password on the host computer: so even if your computer has been hacked, anyone attempting to read that file, on your comptuer or from anywhere you've backed up that file, will face brute-force AES decryption and therefore your passphrases remain secure.

{: .new-title }
> idea
>
> Besides your personal data for wallet storage, you might therefore also consider using the Frankenwallet for other high security data.

This includes (definitely not an exhaustive list, and open to suggestion or contribution as above):
- details and access information for discreetly held cryptocurrency and/or conventional assets... anything you would be "in trouble" if somebody found
- a encrypted file containing a living "will" with your cryptocurrency assets, possibly including instructions for their distribution... encrypted _with a different password_ kept separately and delivered to the executor upon your incapacitation

## Low security data: transaction records {#use-cases-low-security}

Use the password you normally use to encrypt files on the main computer, as suggested earlier [here](/frankenwallet/prepare/password-low).

{: .highlight }
This is called the "low security" password for the Frankenwallet environment, even though it's likely to be the _most confidential_ encryption password that you ever ever use in your daily computing environment.

Consider your transaction records, or (if you're a developer) copies of scripts used for any sensitive or confidential operations... e.g. token minting or smart contract creation that may have confidential _public_ keys & addresses in them.

In the simplest case you might have a file or spreadsheet with cryptocurrency transfers and holdings which you wish to keep confidential, because you would feel "in trouble" if it fell into the wrong hands... although not suffering any catastrophic or asset loss from such a breach.

Therefore this data is at a lower security level, since it might be used to establish ownership but cannot be used to steal your funds.

## High vs. Low: Tradeoff between security & convenience {#security-vs-convenience}

Some users might prefer to keep wallet passphrases in files encrypted only with the low-security password, for the sake of convenience & verification: to regularly verify the correctness of the wallet passphrase in the host environment and the accessibility of that backup file.

Many users will consider that ability to be a security feature in itself: so if you choose to do this, please always keep this security risk in mind (at the risk of sounding pedantic from repeating this idea):

{: .warning }
There is always a chance that _any_ encryption password ever entered on your "daily driver" machine, even if most carefully kept (i.e. never entered on the Internet itself), has been compromised.  If that happens, either on your computer or on any computer or cloud service where that file is stored, that program or malicious user identifying your wallet passphrase might have an opportunity to steal all of your funds.
