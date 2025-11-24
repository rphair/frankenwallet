---
layout: page
nav_order: 30
parent: Cardano secure workflow
title: Cardano SPO Scripts
---
# Cardano Stake Pool Operator Scripts in the Frankenwallet
{: .no_toc }

The Cardano [StakePool Operator Scripts (SPOS)](https://github.com/gitmachtl/scripts) are a popular choice for operators running stake pools: providing a few dozen utilities for setup, administration, and accounting of pools and related blockchain resources.  These scripts must run in an air-gapped environment in many important cases: especially to secure the operator's pledge account(s) and the pool's operational certificates.

{: .important-title }
> FYI
>
> The term `stake pool` is two words (see [Cardano Developer Portal > Editorial Style Guide](https://developers.cardano.org/docs/contribute/portal-style-guide/#editorial-style-guide)) and the term `SPO` [is synonymous](https://github.com/cardano-foundation/developer-portal/pull/1674) with other blockchains' use of the term `validator`.

As you can verify in the [SPO Scripts Mainnet documentation](https://github.com/gitmachtl/scripts/tree/master/cardano/mainnet#readme) (please read this if you haven't already) the scripts can be installed anywhere... but their most logical use with the Frankenwallet will be in its [cold environment](/usage) configuration, set up to run in [offline mode](https://github.com/gitmachtl/scripts/tree/master/cardano/mainnet#online-mode-vs-light-mode-vs-offline-mode): just as they would be installed on a dedicated air-gapped machine.

Assuming you are satisfied with the integrity of the scripts themselves, this will provide the same security of key handling and transaction building as when you are using the raw commands of `cardano-cli` directly, and following the same pattern of [secure transaction workflow](/cardano/model):

1.  first, collecting raw information from an Internet-connected machine;
2.  then, building operations & transactions in a separate, offline environment;
3.  finally, executing these operations & transactions back in the Internet-connected environment.

## Prerequisites

➤ You should already have followed the Frankenwallet installation instructions to create a "cold" Frankenwallet: the default configuration, with the encrypted Linux instance set up & patched without ever having re-enabled Internet access (i.e. don't use a ["cool" Frankenwallet](/cool)).

{: .note }
The only package required by the SPO scripts not installed by default in the Debian-based operating systems recommended here is `jq` which [should already have been installed manually](/install/packages#jq) when the Frankenwallet was created (before disconnecting from the Internet permanently).

➤ The previous [Cardano Secure Workflow](/cardano) step to [Install Cardano CLI](/cardano/software) should also be complete.

{: .new-title }
> tip
>
> `~/bin` — the recommended location to install `cardano-cli` for general ease of use — is also the location expected by the SPO Scripts when they are *also* installed, as recommended, in `~/bin`.

➤ As suggested in the SPO Scripts repository, you should be familiar with the range of [commands used for Mainnet operations](https://github.com/gitmachtl/scripts/tree/master/cardano/mainnet#configuration-scriptfiles-syntax--filenames) and already feel comfortable using some of them: since the particulars of how to use the SPO scripts themselves are beyond the scope of this documentation (you can refer back to that repository with questions or difficulties).

{: .note }
Though another script archive is available for *testnet* operations, this usage is less significant for the Frankenwallet because of the reduced need for security precautions & secure workflow.

➤ Ensure you have an Internet-enabled host for the SPO scripts to collect the required information and execute the results by [installing the scripts in Online- or Light-Mode](https://github.com/gitmachtl/scripts/tree/master/cardano/mainnet#online-mode-vs-light-mode-vs-offline-mode) somewhere that you have access to... and are able to run tasks like those listed in [Examples in Online-Mode](https://github.com/gitmachtl/scripts/tree/master/cardano/mainnet#examples-in-online-mode).

{: .new-title }
> tip
>
> If you don't want the overhead of maintaining a `cardano-node` on your Internet connected machine, you can set up that machine [in Light-Mode](https://github.com/gitmachtl/scripts/tree/master/cardano/mainnet#examples-in-light-mode) instead... specifically, you can install the scripts in Light-Mode directly on your host machine.
