---
layout: page
nav_order: 50
parent: Introduction
title: What does the name mean?
---
# Why "Frankenwallet"?
(in words of project founder)

When our local Cardano users group began to form, during the 2020 intense "lockdowns" in the expatriate community on a dark continent, a few of us expressed reservations that our travel worn computers were not secure enough to host the crypto wallets which would be storing much of our life savings.

To reassure myself & others I outlined a plan to partition a Linux computer's disk — or create the usual dual-booting partition on a typical Windows PC — so the Linux partition would be encrypted and therefore unread- or -writable by the potentially compromised user environment.  For practical reasons [fully determined much later](/install/internal/#goal), it turned out the Linux boot mechanism wouldn't work that way every easily… so we resolved to install such an environment on a bootable _external_ drive instead.

Unfortunately, during the time our [COSD pool](https://cosd.com/pool) was being developed, we could hardly walk down the street for our grocery shopping let alone find a contemporary memory stick with at least USB 3.0 and a high read/write bandwidth… local computer stores were closed indefinitely and cross-country deliveries weren't running.  The best I could come up with was an old spare HD drive plus a SATA-to-USB cable which I hooked together and static-wrapped like this:

![Frankenwallet 1.0 from cable + hard drive](/assets/images/frankenwallet-HD-400x300.jpg)

At this point my working title of "Frankenwallet" looked particularly apt, since the hardware was a patchwork entity built of parts from different computers.  As the [Shelley era](https://roadmap.cardano.org/en/shelley/) was getting under way, we also recalled (later than you would think) that the eponymous Mary Shelley was the author of the eponymous *Frankenstein*.  So with a stirring of ancient hardware and electrical discharge, the ***Frankenwallet*** came to life.

Certainly a slow, rotational SATA drive rigged into a USB port would not have been able to support the bandwidth for the Cardano node wallet Daedalus, as we had hoped, but the bandwidth turned out to be fine for installing Ubuntu Linux and compiling both the Cardano node and the Cardano CLI... so we could safely configure our stake pool and work with our [pledged assets](https://docs.cardano.org/about-cardano/learn/pledging-rewards) without even buying a memory stick, let alone procuring a whole dedicated "air gapped" second machine.

Also in hindsight I realised the term [Franking](https://en.wikipedia.org/wiki/Franking) applied to this key signing environment, since that centuries-old term for *printing stamp impressions* relates perfectly to the task of signing Cardano and other blockchain transactions.  And even when the device is built without either a full-node or browser-based wallet (i.e. the "cold" configuration), the term "wallet" also still applies since it provides an alternative to hardware wallet based toolkits for Cardano stake pool management and other blockchain & cryptographic functions (as a *[zero data wallet](https://github.com/cardano-foundation/CIPs/pull/620#discussion_r1418060841)*).
