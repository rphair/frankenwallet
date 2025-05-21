---
layout: page
nav_order: 10
parent: Cool environments
title: Cardano
---
# Cardano "cool" operations: Light wallets & dApps in the Frankenwallet
{: .no_toc }
- TOC
{:toc}

{: .note }
This page is intended for Cardano users and asset holders who only need a "cool" environment with the minimum of routine Internet usage and settings to support web-based crypto tools.  If you don't need these, and intend to manage your resources in an "air gap" environment, go back to this section (or continue here as well if you need _both_ a "cool" and "cold" Frankenwallet):

[Cardano secure workflow](/cardano){: .btn .btn-purple }

Cardano workflow, as "sandboxed" in the Frankenwallet — with judicious Internet usage, though separated from the owner's host software environment — follows the same pattern as it would for any blockchain: wallet packages maintaining funds, and crypto web sites to apply these funds to interactive use via the Internet.

Though the user should be able to improvise their own Cardano workflow from the principles on the parent page [Cool environments](/cool), here are some use cases to help users get started right away:

## Light wallet use case: Eternl

➤ First, in your host environment, and according to recommended [use of the "scratch" file](/cool/#record-common-data), validate and record the following details for the Eternl browser wallet:
* the Eternl web site [eternl.io](https://eternl.io): comparing it to sources of information you trust (well-populated Telegram groups, X channel(s) followed by people you're connected to, community blog articles & forum postings, etc.)
* the Eternl **Browser Extension** linked from the home page: confirming also with other searches, and other measure of validity (e.g. the number of installations you'd expect from an industry standard wallet)

➤ _(only when that's confirmed)_ Boot into the Frankenwallet, run Chrome, and open the installation link for the Browser extension.

{: .important }
This precaution is to avoid cases where an Internet or browser app search for `Eternl`, immediately before its installation with no corroboration from other sources, could immediately offer a malicious fake that would lead to loss of funds if installed & used.

➤ Record and/or confirm the Eternl wallet passphrase.

{: .warning }
The "scratch" file that keeps your casual records, links, procedures, addresses, and account balances **cannot** be used to store your passphrases, because it require access from the host machine and therefore is encrypted with the [low-security password](/usage/security/#use-cases-low-security).. only the [high-security password](/usage/security/#use-cases-high-security) is suitable to encrypt your passphrases (as per [File encryption levels](/usage/security)).

At this point, if not already, you must therefore designate a file on your host machine to store passphrases and any other Cardano account private key information.  You'll then use thie file for:
* recording (copy & paste, whenever allowed) the full wallet passphrase when it is created;
* keeping the spending password (or hint for that password) next to the passphrase;
* periodically verifying the passphrase via the Eternl UI or by importing into another wallet.

## dApp use case: Staking vault

This is a somewhat lower security requirement, since a security breach might affect the performance or privacy of a user's assets but not allowing funds to be stolen.  An example would be the [World Mobile Vault](https://faq.worldmobiletoken.com/docs/faq-and-support/vault-support) which stores metadata about a user's funds without storing funds themselves.

These resources are meant to be managed similarly to wallets: so users should follow the above Light wallet use case procedure to record the generated login password and seed phrase in the high security password encrypted document.

## dApp use case: Cardano DEX

Since these web sites will automatically locate a user's funds based on the wallet active in the same browser (e.g. for Eternl, see [Setting up your DApp Browser account or DApp connection](https://wiki.eternl.io/en/2_user-guide/dapps)), the only essential step to prepare in your host environment before executing swaps in the Frankenwallet is:

➤ In your host environment, and according to recommended [use of the "scratch" file](/cool/#record-common-data), validate and record the URLs for all swap sites, DEX aggregators, or exchanges you might use.

You will then be able to launch these in the "cool" Frankenwallet without a spurious Internet search leading to a fake malicious DEX or phishing site.  

{: .new-title }
> hint
>
> The URLs for all your dApps can be generously bookmarked, even on the browser toolbar, of the Frankenwallet browser without giving away any of your crypto activity as it might if you did this on your host machine.

Keeping these browser bookmarks for all commonly used staking, trading, and other dApp activity will keep your Frankenwallet off of explicit Internet search... and using all these sites _**only** in the Frankenwallet_ will avoid associating any of your crypto account activity with the "real world" identying activities on your host machine.


