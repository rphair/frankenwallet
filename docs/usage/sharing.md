---
layout: page
nav_order: 40
parent: Usage
title: "Use case 1: Sharing resources"
---
# Use case 1: Sharing keys and resources with associates and co-workers
{: .no_toc }
- TOC
{:toc}

The Frankenwallet design will help physically separated co-workers, as well as personal associates, to share highly sensitive information like cryptocurrency account keys and passphrases with a minimum of exposure.

## Security assumptions 

Computer scientists and operators will recall the general principle that [key exchange](https://en.wikipedia.org/wiki/Key_exchange) is most vulnerable when a communication channel is first established.  At this point, a potential "man in the middle" has their main, and generally their only, opportunity to compromise the key on which the rest of a otherwise perfectly encrypted communication channel is based.

On conventional systems — and for [your backups](/usage/backups) or deliberately shared resources that we'll look at in this use case — that opportunity comes whenever these files are encrypted.  The Frankenwallet's [zero trust](https://en.wikipedia.org/wiki/Zero_trust_architecture) model assumes that the user's host system also hosts an attacker with the ability to observe or record passwords that are entered there: so resources encrypted there might be identified and decrypted on either the host system or any place to which they are transferred.

So the **good news** is that the same protection we believe protects our Frankenwallet backups also applies to other files and archives encrypted in the Frankenwallet for use by others.  Once our counterpart possesses our own designated encryption password — never entered outside *their own* Frankenwallet, as it would also be confined to our ours — the same security guarantees for those resources in our own Frankenwallet will also apply to theirs.

{: .note }
> This assumes acceptance of the "unbreakability" of [software AES encryption](/intro/encryption) as recommended throughout this project.

This argument, if accepted, means that your attacker's only chance to decrypt your shared data has been lost if they cannot use your Frankenwallet nor read its own files — and likewise your data will be equally safe at the other end as long as your associates follow the same protocol.

## Shared resource workflow {#sharing-workflow}

### 1. Set a shared encryption password {#shared-password}

This should be a password that satisfies all the requirements of a [high security password](/prepare/password-high).  To repeat, at the risk of being pedantic: any password you have *ever* entered over the Internet might be used to decrypt the file at some point as your are sharing it.

Beyond the choice of a non-trivial password with [enough entropy](/prepare/password-strategy/#aes-hashed-passwords) (and assuring your counterparts can spell, type & perhaps remember it), nothing is more important than using a _previously unused_ password.

{: .highlight }
To visualise why: for example, if using Gmail to send your hard-encrypted data, you're not just trusting Google but _all of its present and future employees_ not to have indexed a password list from every compromised server or system you've ever used before.

### 2. Ensure all the partners have their own Frankenwallet {#all-endpoints}

They should also agree to the same security standards: which will generally mean they should have the same type of Frankenwallet:

➤ If all partners are working with keys within an "air gap" — for instance, operators of the same Cardano stake pool, or co-owners of the same set of private payment or application keys on any blockchain — then all partners should configure and agree to use a "cold" Frankenwallet as per the default installation instructions: and for each to maintain ongoing isolation from the Internet on that device.

➤ If all partners will require Internet access to administer their shared resources — for instance, co-administrators of institutional wallets (needing to share sets of passphrases), or dApp developers configuring blockchain interaction with the Internet — then you would all arrange a ["cool" environment](/cool) so that no partner's "cold" environment have to be diminished by not maintaining a strict "air gap" around their protected keys.

You may also choose to agree on a [file encryption level](/usage/security): but this is less important because generally such a guarded confidential exchange would only be justifiable for [high security](/usage/security/#use-cases-high-security) data.  

### 3. Share the encryption password {#share-key}

{: .important }
> It's beyond the scope of this article to identify a means of *online* exchange of the encryption password for the exchange of shared files.  Keeping a secret key *truly* secret is the oldest problem in cryptography: long predating the computer age.

This does not mean you have to meet your associates in person to give them a sheet of paper with the password on it: though it's often an ideal solution, it's hard to arrange in the global work environment.  

A "layered" approach is often used in the industry, e.g. opening first a dialogue about how to share the password using [OpenPGP](https://www.openpgp.org): requiring that all parties initially communicate by keys that are verifiable through a mutually trusted third party, and then transmitting an encrypted file containing the password once the confidentiality of that channel is assured somehow.  

{: .new-title }
> get started
>
> See [OpenPGP > Email Encryption software](https://www.openpgp.org/software).

### 4. Share the commonly encrypted files {#share-files}

Now you and your associates can follow this regular procedure to share encrypted resources:

1. In your Frankenwallet, create or update a `7z` archive or LibreOffice file — depending on whether you need to share whole files or just text (passphrases or copies of keys / key files) — encrypting it with your shared encryption password.
1. Save this file to your [host folder](/usage/host-folder) or host directory for that project.
1. On your normally booted host system, send / email / attach / store / save / ship this file to your counterpart(s): along with whatever insecure covering message it may need.
1. Your counterpart saves this file in their own computer's host folder or project directory.
1. In their own Frankenwallet, they decrypt the file or archive and use the data.

The encrypted files saved on both your & your counterpart's host folder — in addition to being transferred with hard encryption, [assumed safe](/intro/encryption) even for unencrypted email exchange — are also assumed safe to back up on insecure media, including storage with your own host computer files outside of the Host Folder.  Just get them to agree they will **never decrypt it on their machine outside of their Frankenwallet**{: .text-red-300 }!

{: .new-title }
> tip: leave your shared files as backups  
>
> This procedure also leaves a natural trail of dated secure records: so you may choose to keep a history of the files prepared in this way to form a history of your project: especially useful if something goes wrong on either side of the exchange that other partners need to verify.

## Example application: multiple operators of a Cardano stake pool {#sharing-spo-example}

The two usual sets of stake pool operation files:
* verification keys and resources visible on-chain already ([low-security files](/prepare/password-low))
* signing keys and "cold" keys proving stake pool ownership ([high-security files](/prepare/password-high))

... should already have been prepared as backups, as described in [backup creation](/usage/backups/#backup-creation): effectively packaging them to be shared between all co-operators of a stake pool by the method above.

{: .highlight }
This has the further advantage of only requiring a single "cold" Frankenwallet for _both_ sharing of these files with co-operators _and_ using them in operational practice.

Sharing both "high" and "low" security `7z` file archives constructed as stake pool backups — each time either archive is updated — would be practical to run a stake pool between two or more remote operators, and would provide a further advantage of maintaining a running backup of the sets of keys.

{: .warning }
Ensure your own personal [pledge](https://docs.cardano.org/about-cardano/learn/pledging-rewards) keys aren't inadvertently shared with others this way: unless doing so deliberately!

➤ Be very careful about the "high" security files: since many stake pool configuration instructions include a pledge address signing key (generally called `payment.skey`) with the list of "stake pool" files.

➤ Stake pools with multiple owners who have separated the pledge between them will — unless deliberately agreed otherwise — want to keep the ownership of these funds completely separate... so ensure you each look through these archives to **remove any confidential payment keys**{: .text-red-300 } before sending this archive to any of the other parties.

{: .important }
> Separate any such "private" resource files into *a third archive* — and only share the other two sets (low and high security) _of the pool configuration files themselves_.

Generally, it would be up to that pool's operators which of these keys would be considered "private" from the other operators.  Some pools might have asymmetric levels of privilege — an "owner" plus a less privileged "operator" — with the partitioning between shared and unshared keys being arranged accordingly.



