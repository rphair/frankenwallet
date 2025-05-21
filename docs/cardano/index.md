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

{: .new-title }
> coming soon: Stake pool operator scripts
>
> Many operators will likely be interested in a secure environment for the stake pool operator scripts, which is scheduled for integration testing & documentation after the current material passes its first stage of Project Catalyst audit: currently on track for **May 2025**, so the SPO scripts will appear in this section shortly afterward.

## Third party software not required

Just as stake pool operation does not require any particular set of third party scripts or tools to build or run a pool, the "cold" Frankenwallet workflow described in this section never needs to include anything more the basic commands of the Cardano CLI.

Once users can verify that the basic CLI (and perhaps Cardano Node) features are running, other tools will be included and documented which operators and users can incorporate into their "cold" environment.
