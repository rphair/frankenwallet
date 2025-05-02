---
layout: page
nav_order: 30
parent: Preparation
title: Your low security password
---
# Choose password: Low security

## Your "regular" encryption password, also for routine encryption on the host computer

You probably already have a password like this: one you would use to encrypt your most sensitive files before saving to shared media, sending over the Internet, or storing on a cloud-based backup.  Therefore this password has two requirements:

- it has *never* been transmitted over, or stored in, cleartext on the Internet
- length & complexity enough to hash to about `2^128` possible values (around 20 apparently random keyboard characters)

This password will be used to encrypt:

➤ Documents you save on the host computer to be opened in the Frankenwallet (e.g. data to use in command scripts, with your private transaction details)

➤ Documents you save on the Frankenwallet which you will need easy access to, and will back up from, the host computer (i.e. of relatively low security: without private keys or seed words)

➤ Archives of these "low security files" (examples for the Cardano blockchain) stored on the host computer:

- stake pool maintenance files:
  - delegation certificate (`delegation.cert`)
  - pool certificate (`pool.cert`)
  - your pool stake address, key, and certificate (`stake.addr`, `stake.vkey`, `stake.cert`)
  - KES and VRF verification keys (`kes.vkey`, `vrf.vkey`)
  - cold counter and cold key pair verification key (`cold.counter`, `cold.vkey`)
    - (this term "cold" has a slightly different meaning than the general one [*here*](/frankenwallet/prepare))
- addresses with verification keys for:
  - your pool pledge (`payment.addr`, `payment.vkey`)
- any other Cardano address (`*.addr`)
- the public / verification component of *any* key pair (`*.vkey`)
