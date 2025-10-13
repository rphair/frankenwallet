---
layout: page
nav_order: 50
parent: Preparation
title: Password strategy
---
# More about passwords & encryption

(based on the original author's operational experience as a UNIX & security administrator)

## How and why to "practice" a password

You will need to know you can type both the low & high security passwords repeatedly from memory, and I have found this strategy works well:

➤ For the [low security password](/prepare/password-low), open up a Text Editor on your host computer — one that doesn't save a "buffer" as you are typing unsaved changes (as an unencrypted LibreOffice or MS Word document would) — to come up with a string of 20+ characters that you can type dozens of times in a row: observing that you've typed them exactly the same.  *Don't save this file by mistake*!

➤ For the [Frankenwallet / high security password](/prepare/password-high), you cannot do this — since any password typed on the host computer should be considered "blown" — so your options to explore a good password, and commit it to memory, are more restrictive… e.g.:

- Boot your host computer in the [Tails environment](https://tails.net) and practice it in a text editor there.
- Postpone this step until you're setting up your encrypted partition in the Ubuntu installer... and then open up a text editor in that temporary Linux environment to practice it there.
- Write down in advance **very clearly** what you plan to use as a Frankenwallet password, and throw it away (or lock it in your safe) when you have typed the password from memory enough times.

{: .warning-title }
> watch out
>
> Composing on paper can work poorly for long & complicated passwords: since not all passwords that look good on paper can be easily typed or memorised!

## About passwords used for AES and assurances AES is "unbreakable" {#aes-hashed-passwords}

AES, beyond the consideration of its implementations in [encryption software](/intro/encryption), lacks a comprehensive attack surface as conceded by cryptographers for nearly 3 decades, and is therefore still considered unbreakable in itself (best source: [Bruce Schneier: tag AES](https://www.schneier.com/tag/aes/)).  Any mitigations of brute-forcing 256-bit encryption only reduce the difficulty to roughtly that of trying 2^128 keys: still a job for a cosmic scale computer.  Therefore your goal is to have a password, which will be "hashed" to this key, with the same unpredictability as a randomly generated 128-bit number.

Assuming that there are 80 possible characters you can type on the computer keyboard (26 uppercase + 26 lowercase + 10 digits + 18 punctuation marks), this is how we derive the 20 minimum number of characters for your password (assuming it's apparently of random & unrelated characters, with any meaning or relationship existing in your mind alone):

```bash
$ bc -l
128 * l(2) / l(80)
20.24698764029213039466
```

With a 20-character password providing enough key variation that the key can't be brute-forced, all remaining attacks have to be on the password itself.  This confirms the absolutely strict requirement that **the Frankenwallet password can never, never be entered outside the Frankenwallet** (where all data is absolutely encrypted and unobservable to the host computer) or in some other system that is *completely stateless* and also unobservable.

So please stay most aware of the operational issues that to passwords themselves, rather than assuming vulnerabilities in the encryption algorithms: since, as we reviewed in our [introduction to software encryption](/intro/encryption), the only practical attack points will be where keys are set, verified, or exchanged: rather than breaking the cipher itself.
