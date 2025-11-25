---
layout: page
nav_order: 20
parent: Cardano SPO Scripts
title: Usage
---
# Operator workflow for SPO Scripts in the Frankenwallet
{: .no_toc }
- TOC
{:toc}

## What to do when `cardano-node` isn't running on your host machine {#use-light-mode}

Cardano stake pool operators will always have access to a running `cardano-node` and Linux remote environment accessible by `ssh` on all the machines hosting the nodes of their stake pool.

Although some operators would feel comfortable installing the SPO Scripts in *Online-Mode* on one or more of these machines — to host their information-gathering and execution — for most operators it will be more convenient to run the scripts in *Light-Mode* on the host machine itself.

This has the advantage of being able to run the SPO Scripts on the host machine even when it's not running its own `cardano-node` — which means that data and actions can be written to & read from the host folder directly... without having to copy them over the network to or from a stake pool node.

{: .new-title }
> tip
>
> Unless you need flexibility and security that might be provided by running a `cardano-node` on the same Internet connected host where you'll be running the SPO scripts, generally that Internet host should be your host machine itself: with the SPO scripts set up with `workMode="light"` (*Light-Mode*) in `00_common.sh`.

## Illustrating & verifying SPO Scripts workflow {#verification}

Operators who have been using the SPO scripts will know there are scripts available for all kinds of pool management functions (see [Examples in Offline-Mode](https://github.com/gitmachtl/scripts/tree/master/cardano/mainnet#examples-in-offline-mode)): including the most complicated steps of generating all required initial key pairs and preparing the initial pool registration & deposit transaction.

Still, the most demanding requirement for the Frankenwallet is to authenticate that it can host the same workflow as the 2 separate "offline" and "online" machines in the workflow of the SPO Scripts.

Therefore we will use the simpler example of an elementary transaction: so operators will be able to verify the security and practicality of their arrangement before [migrating their stake pool](/cardano/scripts/install/#import) into it.

{: .note-title }
> recommendation
>
> Review the first part of [Examples in Offline-Mode](https://github.com/gitmachtl/scripts/tree/master/cardano/mainnet#examples-in-offline-mode) to *both* ensure that you have a good understanding of the "workflow in Offline-Mode" *and* to check that `00_common.sh` in your Frankenwallet's scripts directory is set to `workMode="offline"`.

### Example: Sending funds securely with `01_sendLovelaces.sh` {#example}

This follows the SPO Scripts documentation section [Sending some funds from one address to another address in Offline-Mode](https://github.com/gitmachtl/scripts/tree/master/cardano/mainnet#sending-some-funds-from-one-address-to-another-address-in-offline-mode): in this example, preparing a batch of 2 funds transfers between wallets that have been previously set up, with differences for the Frankenwallet shown here:

➤ **1. Obtain necessary information from online machine**

Running `01_sendLovelaces.sh` will build the file `offlineTransfer.json` in your "online" SPO Scripts directory as per the example: saving the balances from the wallets used in your transaction.

Once this is complete, copy `offlineTransfer.json` to the Frankenwallet [host folder.](/usage/host-folder)  (If your host machine and the machine with your online SPO scripts are different, you'll also have to transfer it between machines.)

➤ **2. Generate transaction in the Frankenwallet**

Reboot into the Frankenwallet and move `offlineTransfer.json` from the host folder into the Frankenallet's "offline" SPO scripts directory.

{: .important }
This should always involve moving a file from one directory to another... since the Frankenwallet's copy of the SPO scripts should not be installed *anywhere* on the host machine — *including* the host folder — to prevent tampering with the scripts.

When you're done using the `01_sendLovelaces.sh` script to update the `offlineTransfer.json` file, move it back from the SPO Scripts directory into the host folder again: for execution by the "online" scripts.

➤ **3. Submit transaction through online machine**

Reboot into your host environment and move/copy the `offlineTransfer.json` file to the "online" SPO Scripts directory.  (If your host machine and the machine with your online SPO scripts are different, you'll also have to transfer it between machines.)

Run `01_workOffline.sh execute` as many times as necessary to execute all your transactions that were assembled in the Frankenwallet.

## Backing up the SPO Scripts pool directory {#backups}

Operators interested in backing up this material outside the Frankenwallet will basically follow the procedure in [Backups from Frankenwallet to host machine](/usage/backups), but with one important difference:

{: .highlight }
The pool files won't be separated between [low security](/prepare/password-low) and [high security](/prepare/password-high) requirements (based on the consequences of a security breach): so when encrypting the whole directory for backup it should be with your **high**-security Frankenwallet password.

Recall (from [file encryption levels](/usage/security)) that the lower-security files were kept encrypted with a password that the user would feel comfortable entering on the host machine: while the higher-security password can never be entered on an Internet-connected system.  

- This is to allow users and operators access to less confidential files more freely on the host system... for example, stake and payment addresses which can be used and transmitted openly.

However, since [the directory that stores your pool keys](https://github.com/gitmachtl/scripts/tree/master/cardano/mainnet#import-your-existing-pool-from-cli-keys-or-tutorials) doesn't separate files by these characteristics, you'll have to do one of these things: either

1.  As suggested above, assume the highest security clearance for the whole directory and encrypt its entire contents with a single maximum-security password; or
2.  Make your backups more deliberately: perhaps by writing a script that prepares two or more archives according to different security criteria, and with different passwords.

In either case, encrypted backups can then be stored on the host folder or whatever folder on your host machine your automatic or off-site backups are regularly made from.
