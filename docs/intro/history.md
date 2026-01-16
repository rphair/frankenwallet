---
layout: page
nav_order: 30
parent: Introduction
title: Why was it developed?
---
# Why was the Frankenwallet developed?
(in words of original author)

## Literally, [COSD](https://cosd.com/pool) could not secure its stake pool [pledge](https://docs.cardano.org/about-cardano/learn/pledging-rewards) without the Frankenwallet.

I began documenting this standard in the first 4 epochs of the [Cardano Shelley era](https://roadmap.cardano.org/shelley), while creating the stake pool amidst very real fears about placing my entire life savings into a bare Cardano address without being able to know if the system I was working on was compromised.

We'd been "locked down" in a country without commonly available spare computers, so I came up with the idea of generating the stake pool keys on a persistent instance of Ubuntu Linux on a USB connected drive.  I realised a modified Linux installation procedure would allow any stake pool operator (SPO) or demanding user to create a "cold environment" without needing the hardware of a second machine.  
  
In that same period there was a [sadly famous case](https://forum.cardano.org/t/spos-do-not-repeat-my-mistakes-keep-your-core-node-safe/37766) of an SPO who was brave & noble enough to admit losing a million ada via an injection of crypto key harvesting malware by a compromised Docker script.  So I also chose to avoid shared images and scripts (though adding the [SPO Scripts](/cardano/scripts) much later) which operators would be expected to use without being able to identify hackers with similar looking tools.  

In other words: the evolving Frankenwallet instructions, by contrast, are *procedural* or *educational* — outlining a flexible method for everyone to build their own image — rather than downloading a USB-compatible Ubuntu image which would eventually be subverted somehow.

Even if a user's computer is known to be infected with malicious software, and even if the hardware has to be shared with others (like an inner-city library with public computers, or a shared computer in a African village schoolhouse), a safe booting environment for Cardano & other cryptocurrencies can be created with only the cost of a (hopefully fast) USB drive *and* a time commitment to follow these instructions.

Generally the Frankenwallet is offered here as a *security sandbox*… whether you are using it for simple transaction signing, configuring Cardano operations, or just an an extra partition to isolate your crypto wallet (or any software) from a system with a lower security standard.
