---
layout: page
nav_order: 40
parent: Preparation
title: Your high security password
---
# Choose password: High security

## Your "vital" encryption password, for all private keys and to unlock the Frankenwallet drive

This password will be **brand new** as well as matching the requirements of the "low security password" :
- length & complexity enough to hash to about `2^128` possible values (around 20 apparently random keyboard characters)
- it has *never been entered or stored* on your, or anyone's, host machine, *ever*.

The safest thing of course is to come up with a completely new password… but use something like the tips on the next page to make sure you will be able to recall the password later.

{: .new-title }
> Hint
>
> Composing & practicing the password in a text file on a "stateless" machine like an OS installer or the Tails environment won't breach the password.

This password will be used to encrypt:

➤ The entire Frankenwallet disk itself.

➤ Documents you prepare on the Frankenwallet to be saved on the host computer, but *are too confidential* to *ever* open there (i.e. anything containing private keys or seed words, e.g. a document with all your wallet data, or a "will" for your crypto assets with wallet seed phrases)

➤ Archives of these "high security files" (examples for the Cardano blockchain) stored on the host computer:

- stake pool ownership files:
  - your pool stake address signing key (`stake.skey`)
  - cold key pair signing key (`cold.skey`)
  - KES and VRF signing keys (`kes.skey`, `vrf.skey`)
  - your pool operational certificate (`node.cert`)
- signing keys for:
  - your pool pledge address (`payment.skey`)
- the private / signing component of *any* key pair, especially for addresses with funds (`*.skey`)

{: .important }
The list of "high security" keys here can be use to steal your funds and divert the rewards, or disrupt the operations, of a Cardano stake pool... as opposed to the [low security](/frankenwallet/prepare/password-low) keys which can only be used for verification and observation, and therefore are a lower risk of compromise.

Note also that the password encrypting the Frankenwallet doesn't have to be the same as the one encrypting high security key archives & files, **but**:

➤ Having the same password for both purposes (whole-drive and file encryption) ensures that meeting the strict password security requirements for one purpose will also apply to the other.

➤ Therefore it's generally better to have one single long, complicated, unique password — which you can commit to memory for both purposes — rather than keeping two separate passwords for virtually the same purpose... making it more likely to forget either of them.
