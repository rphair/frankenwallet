---
layout: page
nav_order: 20
parent: Cardano secure workflow
title: Transaction flow
---
# Model for transaction workflow using the Frankenwallet
{: .no_toc }
- TOC
{:toc}

## Stick to the general "air gap" transaction workflow {#model}

First, familiarise yourself (if not already familiar) with the page [Cardano Developer Portal > **Secure Transaction Workflow**](https://developers.cardano.org/docs/get-started/security/secure-workflow) which outlines [this general model](https://developers.cardano.org/docs/get-started/security/secure-workflow#a-model-for-a-secure-transaction) for the use of an air gapped machine:
1. (**insecure**) [**Assemble**](https://developers.cardano.org/docs/get-started/security/secure-workflow#1-assemble-all-transaction-details) blockchain data for your transaction from the Internet and live Cardano node
1. (**secure**) [**Build**](https://developers.cardano.org/docs/get-started/security/secure-workflow#2-build-tx-details-into-a-signed-transaction) the transaction and sign it with private keys kept only in secure environment
1. (**insecure**) [**Upload**](https://developers.cardano.org/docs/get-started/security/secure-workflow#3-upload-and-submit-the-tx-file) and execute the signed transaction

The Frankenwallet model will be exactly the same *except* that it won't require a "transfer memory stick" to move files between the insecure and secure environments (as introduced on the ["What's unique..."](/intro/usp) page) because those 2 environments already share a drive: your host computer's disk itself.

{: .highlight }
> The rest of material below suggests steps you might want to do differently on the Frankenwallet than you would on a traditional "air gap" system with a memory stick transferring your files.

This general model is also used whenever utilities like the Stake Pool Operator Scripts are incorporated into the secure workflow ([see example](/cardano/scripts/usage/#example)).

## 1. Assembling the transaction details on the host machine {#assemble}

### Keep a current `protocol.json` file in your [host folder](/prepare/#host-folder) {#protocol-file}

{: .new-title }
> tip
>
> This habit will ensure you always have an up-to-date `protocol.json` file — to avoid transaction building errors, or inaccurately costed transaction, in the "cold" Frankenwallet where you won't be able to download an updated copy.

Whenever you're ready to work in the Frankenwallet, get a fresh copy of the protocol file and compare it with the old one to see if it needs to be copied... if so, note it in the file where you're keeping your transaction details and notes.

This process can be simplified by keeping the previous version of `protocol.json` and comparing them: if the old & new file differ, copy the new file from your host folder into the Frankenwallet directory where you're preparing your transactions.

## 2. Building & signing the transaction in the Frankenwallet {#build}

### Use your "scratch file" to pass messages between your Frankenwallet & host machine {#scratch-file}

{: .new-title }
> tip
>
> The "scratch" file doesn't have to be disposable, only storing data for the current round of transactions... it can have a page or section for each Frankenwallet session, to keep an ongoing record of your account activities, stake pool operations, etc.

Whether you prefer to run `cardano-cli` commands raw (as recommended in the original Frankenwallet documentation, by keeping "templates" of commonly used commands rather than relying on third party scripts) or use a CLI package of operator tools, you will likely do both these things:
1. **repeat certain activities**: therefore it helps to copy & modify commonly used commands or groups of commands from your own previous work.
2. **prepare commands before running them** in the Frankenwallet: especially when this might be easier with the full software & Internet access of your host machine.

Over time this "scratch" file can become both a log and a workbook for your operations & cryptocurrency records... and since this file will be repeatedly opened on the host machine as well as the Frankenwallet, this extension to the usual "air gap" instructions is especially important:

{: .warning }
Unless you are certain your "scratch file" will **not** contain any compromising data, it should be encrypted from the beginning with your [low security password](/prepare/password-low).

## 3. Upload & submit signed Tx, and update records & backups {#upload}

### (optional) Use the Frankenwallet disk to store files used to build transactions and operations {#archives}

{: .new-title }
> tip
>
> Each session on the Frankenwallet may generate temporary files: rather than deleting these, you can use the encrypted disk to keep these files without having to encrypt them individually.

While your low security (verification) keys and high security (signing) keys [should be kept in separate, dedicated directories](/usage/backups/#backup-creation), intermediate files can also be kept in different folders on your Frankenwallet disk, including:
1. subfolders for particular projects (token mints, smart contract development & testing)
1. subfolders for each date of operations (especially for stake pools: e.g. with folders named by ISO date + the activity performed)

... according to whatever scheme suits your operations & crypto resources.  The only requirement of course is to keep all of this sensitive but unencrypted data **on the Frankenwallet disk** and far away from your host folder!
