---
description: An air-gappable transaction building & key backup and secured browser wallets for Cardano & other cryptos.
layout: page
nav_order: 10
title: The Frankenwallet
---
# An encrypted, air-gapped Linux bootable USB drive for Cardano & other cryptocurrency secure operations
{: .no_toc }
- TOC
{:toc}

## Who needs it?

- [x] Anyone working directly with **cryptocurrency private keys** or seed phrases (e.g. for Cardano, Bitcoin or Ethereum or other cryptocurrency addresses) or other high value resources targeted by hackers (e.g., Ada stake pool keys).

- [x] Anyone wishing to work in high security with these resources **without** either of these usual requirements:
  - a **second computer**, often called a *cold* or *air gapped* machine, for the sole purpose of storing keys, signing transactions, and other secure operations.
  - a **hardware wallet** with a fixed environment supporting these operations (these devices often have well supported feature sets, although with high price tags and proprietary design).

- [x] Anyone wanting or needing **direct access to all their own files** on their main computer, in an air-gapped and securely prepared environment, while working with high security data.

- [x] Anyone who **cannot afford — either financially or logistically** (e.g. frequent travellers) — **a second machine or hardware wallet**.

- [x] Anyone who finds the **small form factor** of a hardware wallet appealing, and has wondered how you might get the same (or better) features on a **cheap, ordinary memory stick**.

- [x] Anyone who has wished they could have a **full featured operating system** — with general purpose software, including the ability to edit & save encrypted key files, archives and other records — on their premium hardware wallet.

- [x] Anyone using memory sticks to **store or back up private keys** — for bare addresses or assets like stake pool pledges & smart contract accounts — who has worried about an unencrypted memory stick being lost or stolen.

- [x] Anyone wishing for an option for an **off-site backup** of their keys, wallet seed phrases, and other cryptocurrency asset records… given that AES based encryption is considered unbreakable when properly used.

## How to use this guide

Most readers interested in this subject will already know how to:

- [install Linux](https://ubuntu.com/tutorials/install-ubuntu-desktop) (our reference is Ubuntu 24.04, chosen based on popularity and especially to match the majority of Cardano stake pool & other servers)
- [install the Cardano node](https://developers.cardano.org/docs/get-started/cardano-node/installing-cardano-node) and CLI software **and/or** the CLI for their preferred blockchain
- use the [Linux command line](https://github.com/jlevy/the-art-of-command-line#readme)

Therefore, please be familiar with the external references above, so we can focus on:

- particular installation procedures & parameters to ensure an **encrypted OS partition** (and, where possible, an encrypted boot partition);
- a model for **secure workflow**: to allow common tasks to be done repeatedly in the Frankenwallet, while allowing the data & procedures for these tasks to be recorded, stored, and backed up on the host machine;
- OS and application **security tuning**: in case some applications or software upgrades require periodic or specialised Internet access (not a general requirement).

### Disclaimer

{: .warning-title }
> use at your own risk
>
> Nobody can anticipate the wide range of adversaries, attack methods, and operator errors which might lead to the loss of your privacy and/or funds even if you follow this security model.  This material is a "best guess" tradeoff between security and convenience.

The fact that the original author, and any contributors thereafter, have taken responsibility for maintaining and improving this material does not imply any responsibility for losses that may happen to you: as you use this material (as you would use anything else) entirely at your own risk.

Details: [CC BY-SA 4.0 Legal Code](https://creativecommons.org/licenses/by-nc-sa/4.0/legalcode.en) > [Section 5 – Disclaimer of Warranties and Limitation of Liability](https://creativecommons.org/licenses/by-nc-sa/4.0/legalcode.en#s5)

### Found an error, or want to make a suggestion?

Head over the the Frankenwallet repository (linked in the upper right hand corner) and submit:
- an Issue (to discuss a matter of form or content):
- a Pull Request (to submit a particular change: generally after submitting an Issue first)

{: .note }
Keep in mind this material is **under construction** until further notice, with calls for community comments planned for **late May 2025**: so to avoid duplication of effort, please save issues & change requests until then.

The goal will be to keep refining not only the instructions but the guides themselves: most importantly, the security standards.  If you have a well defined suggestion or correction, please post it on the repository when the community feedback period is announced (in mid-2025).

## Where to begin?

[History & motivation for the Frankenwallet](/intro){: .btn .btn-purple }

[Begin creating your device](/prepare){: .btn .btn-green }

{: .highlight }
**Site last built: {{ site.time | date: "%d %B %Y at %R %Z" }}**
