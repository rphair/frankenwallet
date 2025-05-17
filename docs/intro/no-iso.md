---
layout: page
nav_order: 40
parent: Introduction
title: Why no ISO image?
---
# Why is there no ISO image for the Frankenwallet?
The question you might have, put into more detail:

> *“Here we have a several hour build procedure that potentially thousands of users will all have to do on their own.  Wouldn't it be a great benefit to the community to make a downloadable USB image, which has all these things included, that people could begin using immediately... saving us thousands of collective man-hours of work?”*

Due to the security and operational concerns below, this might not actually save the operator any time.  Additionally, with an ISO users would miss the invaluable experience of becoming intimately familiar with the security basis for their cryptocurrency livelihood by creating it from scratch: as well as being able to recreate that scenario across different hardware configurations (e.g. an internal hard drive partition [documentation forthcoming]).

{: .highlight }
**Reason 1**: An exploit of any prefabricated environment generally affects many users at once.

Standardising the process, rather than the result, keeps the target (the completed Frankenwallet) constantly subject to independent security audit.  The potential for even build scripts to include lethal exploits has been illustrated [here](https://blog.aquasec.com/malicious-container-image-docker-container-host) (the basis for the hack already referred to [here](/intro/history)).

It also ensures that **not all Frankenwallets will be the same**.  Keeping this procedure as flexible as possible will leave hackers without a common surface to look for besides the impenetrable exterior of an LUKS encrypted partition.

- Since the interaction between the Frankenwallet and files on the host computer is also left to user discretion, according to their own encryption standards and file naming conventions, hackers will also will be without a standardised set of files to look for as targets containing cryptocurrency assets.

{: .highlight }
**Reason 2**: Even with a pre-fabbed initial image, the user would still not be spared the requirement to maintain the software.

For Cardano CLI ([`cardano-cli`](https://developers.cardano.org/docs/get-started/cardano-cli/get-started/)) for example, its capabilities are constantly expanding and even the basic transaction syntax may change even if you're not using more modern features on the cutting edge of native tokens and smart contracts.  Users would still have to copy and install `cardano-cli` binaries and libraries from a compatible, relatively secure server *or* build these directly on the Frankenwallet.
