---
layout: page
nav_order: 60
title: Cardano secure workflow
---
# Cardano secure workflow

{: .note }
This section is intended for operators and developers who need a "cold" (= "air gapped") environment for low-level Cardano commands or stake pool operations.  If you intend to run a "light" (browser plugin) wallet in the Frankenwallet, skip forward to the section on the "cool" Frankenwallet which allows restricted use on the Internet:

[Cool environments](/cool){: .btn .btn-purple }

... and then continue to the page afterward with recommendations for Cardano "light wallet", DeFi, and dApp users.

## Stake pool operator scripts {#spo-scripts}

Many operators have come to depend on Cardano's [StakePool Operator Scripts (SPOS)](https://github.com/gitmachtl/scripts) and so — although these scripts may not be necessary for operators who are fluent with `cardano-cli` commands and comfortable managing blockchain resources manually — these scripts should be considered compatible with the Frankenwallet.

These operators should please continue through this section, in order, to the [SPO Scripts](/cardano/scripts) subsection: which will help them get started quickly and safely installing & using these scripts in the Frankenwallet.

## Third party software not required {#self-sufficient}

Just as stake pool operation does not require any particular set of third party scripts or tools to build or run a pool, the "cold" Frankenwallet workflow described in this section never needs to include anything more the basic commands of the Cardano CLI.

Once users can verify that the basic CLI (and perhaps Cardano Node) features are running, other tools will be included and documented which operators and users can incorporate into their "cold" environment.
