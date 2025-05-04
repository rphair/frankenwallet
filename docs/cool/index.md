---
layout: page
nav_order: 70
title: Cool environments
---
# Cool environments (Internet restricted)

If you have decided to go on with your Frankenwallet having restricted Internet access, rather than no Internet access at all, you will able able to use the applications in this section which depend somehow on Internet connectivity.  Therefore we're calling this the **cool**{: .text-blue-100 } environment (since it's not quite cold).

➤ Internet **browsing** should be prohibited on "cool" environments, just as you would not expect to browse on a "cold" environment.

However (and in case you have skipped to this section), you should still follow the instructions on this page ([securing the browser](/install/browser)) to curtail any automatic or institutionalised ("spyware") activity from Firefox (the default and only browser which comes with Ubuntu).

It is against these recommendations to mix the security levels of both the "cool" and the "cold" environments… for instance:

➤ Do not keep unencrypted private key files on any machine that also runs any Internet dependent software like a UI node wallet (e.g. Daedalus on Cardano).  The chances of losing the assets secured by those key(s) are too great.

{: .warning-title }
> that means...
>
> Don't assume your private key files are safe to keep & work with on the "cool" Frankenwallet... since these key files are "in the open" (as opposed to encrypted storage of LibreOffice or secure application space in a browser-based wallet), they pose a security risk anywhere outside of an air-gapped machine or "cold" Frankenwallet.

➤ Conversely, do not permit routine Internet access from any machine which stores those keys, or on which you enter the high security password for your most sensitive files (e.g. any that stores your wallet passphrases), at the risk of compromising either those keys or that password.

## What if I need *both* private key secure workflow *and* light wallets? {#both-cool-and-cold}

Then you are an ideal candiate to create & use **two** Frankenwallets... just as the [COSD pool](https://cosd.com) has from the beginning, since this material was first proven from 2020 to 2021.  Isolation between your extremely vulnerable cleartext private keys and your less vulnerable encrypted application data is ***exactly*** the purpose of this security model.

{: .new-title }
> tip: if creating two Frankenwallets
>
> You should still follow the cardinal rule of *never* entering your "cold" Frankenwallet password into any Internet connected machine... which includes the "cool" Frankenwallet.  **That means** your "high security" Frankenwallet password should ideally be _different between the 2 Frankenwallets_.
