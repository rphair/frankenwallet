---
layout: page
nav_order: 50
parent: Usage
title: "Use case 2: Will & Testament"
---
# Use case 2: Preparing a cryptocurrency will & testament 
{: .no_toc }
- TOC
{:toc}

This is a special case of "resource sharing" for a single draft of confidential data: not intended for operational use, but requiring an equally strict approach to security (plus an additional need for privacy) and therefore following a very similar procedure.

{: .new-title }
> tip
>
> Even if you are not an operator or developer, browse the background & purpose of [use case \#1](/usage/sharing) first, since most of the theory & preparatory steps will also apply here.

The main differences will be in:

- **Frequency**: instead of transmitting an encrypted document regularly to the outside world, you will prepare and place it *once* (and then update it as needed; eradicating any old version).
- **Target audience**: instead of a technical counterpart, the person with the document may know little more than how to open a password-protected file.
- **Infallibility**: without the usual opportunities to clarify errors or correct omissions, you must be sure enough correct detail has been left in place for a likely naive recipient to reconstruct your portfolio: since there will be no way of answering questions after your incapacitation or demise.

## Target audience of your testament {#target} 

The cultural term [will and testament](https://en.wikipedia.org/wiki/Will_and_testament) is used very loosely here, since there will be nothing legal nor enforceable about the document, and the sole possessor of its unencrypted contents will generally be given complete access to everything described therein: regardless of any other beneficiaries you may designate.  

Unless you have implicit trust in a person to whom you might show the contents in advance — and unless you would trust them to cooperate with you in asset sharing *prior to* your incapacitation or demise — an encrypted LibreOffice document must be sufficient to reconstruct all your blockchain & custodial assets **as if you were deliberately giving them everything here and now**... even though they should only see this testament after your death or incapacitation is confirmed.  

{: .important-title }
> splitting the estate
>
> Use common sense in following these instructions: e.g. if you wish to strictly split your crypto estate into two or more parts, for multiple sets of inheritors, you would go through *all* instructions here twice: preparing multiple testaments, then situating each document and its own *unique* password with different pairs of custodians.  

However, most substantial cryptocurrency holders would consider themselves lucky even to find *one* trusted friend or family member with enough technical skill to be able to reconstruct all their blockchain assets — potentially across multiple chains, exchanges, liquidity pools, etc. — so the general recommendation would be to leave a single document in the hands of the single person most ethically *and* technically qualified to act as your *executor*.

## Components of a testament file {#components} 

### I. Identify helpers {#helpers} 

Here is a chance, if possible, to begin your document with a list of individuals or companies you currently think could be trusted if a non-technical or non-crypto-oriented executor finds themselves with the document in their hands.  Suggestions would include:

➤ Your own most trusted associates in the crypto community: any of whom should be likely to want to honour your legacy and ensure your loved ones are provided for.  

➤ Any associate of the executor known to be technically competent, crypto-aware, and capable of helping under supervision (though perhaps not suitable as executor themselves).

➤ Responsible I.T. companies who could designate a trustworthy agent to help your executor in accessing blockchain resources under contract; perhaps after signing a non-disclosure agreement or posting a bond against theft.

An "incentive" can also be recommended here: with an indication that these people should be paid for their time and confidence out of the total inherited funds before distribution to beneficiaries.  

### II. Identify software {#software} 

Here you should not assume that even the most technically competent helpers will determine on their own *any* completely safe way (in an Internet full of scams and fakes) to convert your crypto keys and passphrases into usably reconstructed accounts.  For instance, imagine someone unfamiliar with the Cardano blockchain searching online for "cardano wallet" and finding a well-promoted fake that would wipe out your estate immediately.

Therefore you must also designate software in a way that is completely unambiguous and leaves *nothing* to the imagination.  For instance, to reconstruct a series of wallet passphrases on the Cardano chain, you might write:

{: .highlight }
1.  Get a newly installed or otherwise secured computer and confirm an Internet connection.  
1.  Save this file to that computer's hard drive.
1.  Install Lace wallet from web site **lace.io** where you will find a button "Add to Desktop" which will set up the wallet software in your Internet browser.
1.  If that button is missing or not working, install the Lace extension directly from its official page ([on Firefox](https://addons.mozilla.org/en-GB/firefox/addon/lace-wallet/)) or ([on Chrome](https://chromewebstore.google.com/detail/lace/gafhhkghbfjjkeiendhlofajokpaflmk)).
1.  All the following "Cardano wallet" 24-word phrases can then be copied & pasted into the Lace screen where it says "Import wallet".  If you cannot paste the whole phrase, make sure all individually selected words are an exact match.  

Generally: list here the **exact URLs** (to avoid any possibility of fakes) of:
- sites from where your executor should download each type of wallet they will need;
- crypto exchanges where your executor should check for stored funds;
- any dApps necessary to reclaim funds from staking arrangements and liquidity pools.

Don't shy away from including abundant and *redundant* detail!  The fewer people that need to provide "help" to nontechnical, or less technical users, the lesser the chances that your funds will be lost or stolen in the process.  

### III. The resources themselves {#assets} 

Here you must imagine a person trying to reconstruct your entire fortune from a cold start.  There cannot be a complete checklist for all of these, but it should include each of these when applicable:  

➤ For each blockchain you have resources on:
- for each wallet you have there:  
  - list its recovery phrase.
  - if wallet is "staked", provide instructions to unstake it and claim any rewards.
    - (the results of this can be significant if the testament is received after a long period of wallet disuse, due to your incapacitation or delay in delivery)  
- for each non-wallet resource:
  - copy all key pairs necessary to reconstruct that resource:  
    - e.g. for payment keys: address, public (verification) key, and private (signing) key
    - (any process for claiming staking rewards for these addresses should also be detailed)  

➤ For each dApp or liquidity pool you maintain funds with:
- list its URL, recovery phrase, access key, or any other relevant details.
- provide complete instructions to dissolve the position and transfer into one of the restored wallets.  

➤ For each exchange you might have funds stored in:
- list its URL, username, and login password;
- list all registered details for authentication purposes (email, phone, any PINs, address as on KYC);
- list any other means of authenticating your login or identity:
  - e.g. [TOTP (authenticator app)](https://en.wikipedia.org/wiki/Time-based_one-time_password) setup code or other authentication tokens
  - e.g. any PINs required for certain activities like trading or transfer  
  - including **login details for the registered email address**: likely needed for ID challenges.

{: .new-title }
> suggestion
>
> If you can commit to keeping such balances updated, the restoration process would be more certain if you would leave **approximate balances and dates** for **each wallet and account** to help your executor confirm they've been restored properly.

{: .important-title }
> for complex resources
>
> Naive users will likely not understand too many text keys copied into a document format, so this approach could be error prone for multi-part resources like a Cardano stake pool.

In these cases, your instructions might direct them to an archive — to be decrypted per your instructions, and included on the same media as the testament file — [as set up for transfer to a co-operator](/usage/sharing) so a potential new opemight download all the stake pool resources and continue the pool as your legacy.  If that seems unjustifiable given the circumstances, just include the key details **for the [stake pool pledge](https://docs.cardano.org/about-cardano/learn/pledging-rewards)**.

{: .new-title }
> tip
>
> Some or all of this may be simplified if you share with them here your Frankenwallet password(s) *and* let them know where they can *physically* obtain your Frankenwallet(s).  

### IV. Advice on distribution {#distribution} 

This is a subjective, perhaps narrative document in your own words about how, when, and to whom the funds should be distributed, including (but not limited to):
- what percentage, or which types of resources, you would like to distributed to each inheritor
- whether you would like each of these resources distributed as cryptocurrency or fiat currency
- how cryptocurrency should be converted to fiat: in which jurisdiction, and with what services *including URLs*
- any message you would like to be distributed confidentially along with these funds

{: .note }
> For the sake of clarity — and to avoid distracting anyone providing technical help — any personal message that would be tempting to include here should likely be put in the [covering instructions](#placement-specific).

## Place the document in your family or social circle {#placement-general} 

For your own peace of mind, and for the preservation of your fortune while you are still in sound mind and body, the most essential part of this procedure will be this:

{: .warning-title }
> cardinal rule
>
> The encryption password of this document and the document itself must never be kept in possession of a single person.

Therefore, unless you can think of other restraining factors that will prevent a single person from taking everything that you have — including the possibility of your executor being robbed by an antagonist who might combine the testament with its password — you can proceed with the placement when you have found **two people or agencies** that meet all the following criteria:

- both of them are trustworthy and well-known to you;
- each of these knows of the other, but are outside regular contact *and live separately*;
- each of these has been assured of the other's integrity while you are in sound mind and body;
- both of them together will not be inclined to secretly conspire against you.

If you cannot find two such people, or have no such faith that such trustworthiness is possible or can ever really be relied upon, your best choice is to keep any prepared document for your own reference and skip to the final section on [alternatives](#alternatives).

### 1. Choose the decryption password {#password-choice} 

Unless you plan to distribute this document to your executor ***in*** the Frankenwallet — i.e. including them as a single item, to be delivered after incapacitation or death, perhaps walking through accessing your instructions ahead of time, at least by opening the file where you've prepared it inside the Frankenwallet — your own master copy of this document will reside on your host machine, encrypted with a separate password than any you've created for the Frankenwallet.

{: .highlight }
> These should different to avoid the possibility that an antagonist gaining access to the testament password will not also be able to raid your resources by obtaining & operating your Frankenwallet _or_ decrypting any of the key backups you've made with it.

Like [phase 1 of the document sharing instructions](/usage/sharing/#shared-password), the testament password is also a brand-new and [highest security password](/prepare/password-high).  The file you create above might never touch the Internet, but you must remain even more sure that potential antagonists will not somehow find previously used passwords (for either you or your executor) and apply them to a stolen or intercepted testament file.  

Also, in your chosen password, you should consider any limitations of both your executor (who will generally hold the file) and your key-keeper (who will deliver the decryption password).  Some people are bad with punctuation; some can't tell capital from lowercase letters; some of them won't recognise a 40-character random string as a password at all *or* be able to transcribe it correctly.  You might avoid a sad and frustrating situation (posthumously) by being gentle with them.  

### 2. Prepare the non-confidential covering instructions {#cover} 

Here is where you can introduce the procedure you expect them to follow — along with any affectionate or inspirational messages you were advised not to include in the encrypted testament document itself — to ensure they are most likely to understand what they should do next.

As anyone following the Frankenwallet instructions would agree, most people and their desktop computers will never maintain the security assurances necessary to work safely with cryptocurrency keys or passphrases.  You must assume general household computers will be infected with crypto-raiding malware and that your legacy would be lost the moment anyone opened your testament file on such a grossly insecure machine.

For that reason, you might advise them in the covering instructions as follows:

1.  First, find & use a temporary secure environment to apply the password and read the file, and then see the next steps to takes, since those would require making some additional arrangements;
2.  Then, be prepared to execute those instructions securely: e.g. advising to buy a new computer, or obtain an old one, and install a fresh copy of Linux on it... or whatever you consider adequate security precautions (perhaps with technical assistance from your [identified helpers](#helpers)).  

{: .new-title }
> tip
>
> So they can quickly get started & review your testament, you can advise your executor in your covering letter to first decrypt the file from LibreOffice within an easily set up [Tails environment](https://tails.net) that they should install first: though also advising them that this [stateless environment](https://tails.net/about/#amnesia) will be unsuitable for maintaining access to the assets themselves.  

### 3. Deliver the file and cover instructions to one person (generally your executor) {#placement-specific} 

Now, while in your prime, you have a chance to explain what you are giving them: as well as choosing a backup media recognisable as something distinctive and robust enough to stand the test of time or environmental duress:

➤ All it takes is a spark to wipe out a **memory stick**{: .text-red-300 }, and your legacy along with it.  The [failure modes of flash drives](https://en.wikipedia.org/wiki/USB_flash_drive#Failures){: .text-red-300 } statistically create too much opportunity for either a manufacturing defect or prior degradation from read/write cycles to cause a failure when your document is needed the most.

➤ The author's choice would be **optical media**{: .text-green-200 }, especially a **CD**{: .text-green-200 } which has a much better statistical failure immunity and life expectancy: with much greater *scratch resistance* than a **DVD**{: .text-red-300 }.  You can also easily make multiple copies of the CD and leave them in different places if concerned about loss: including with other people, to ensure at least one copy is available for your executor when the time comes.

➤ Don't use a **rewritable disc**{: .text-red-300 }: these are weaker in both physical and logical structure.

It is absolutely vital that any media you prepare be **marked with the date on the media itself** rather than its containing envelope (another shortcoming of memory sticks vs. optical discs).

{: .important-title }
> no need to encrypt optical discs
>
> Though possible to make encrypted optical discs, accessing these would be much more prone to operator error than than reading an unencrypted ISO CD containing your already strongly encrypted testament file plus any other encrypted archives needed for your assets.

### 4. Deliver the password to another trusted person {#password-custody}

When you've delivered these materials and notified your executor that the key- or password-bearer will contact them after your decease or incapacitation is confirmed, then you can make the corresponding delivery of the decryption password.  

Ideally the executor is "at home" while your key-bearer is "abroad" though in some place where you can physically meet them: and therefore give them a card or a note containing the password that your executor can recognise has indisputably come from you:

➤ This is a chance to show a personal touch — ensuring the executor & perhaps other inheritors will see its indisputable and final significance — and to include brief instructions for both the bearer and the executor: with completely reliable long-term contact information for the latter.

➤ Perhaps you could rely on both the bearer and the executor to both be present with you after suffering a mortal injury or illness... but in case of accident, you should ensure the bearer has the means to contact the executor after you are gone: perhaps for the first time.

### 5. Update as necessary {#update} 

Given how crypto portfolio assets shift around, you will want to update the testament file in your Frankenwallet each time you create or close a substantial wallet, account or substantial DeFi position: with no logistical difficulty, since you would be using the Frankenwallet for all these things anyway.

{: .new-title }
> tip
>
> You might format your own personal records of wallets & other resources so their key components can easily be copy & pasted from those files into the separate testament document.

After each update, a newly burned CD can be **marked with the date** and sent out to your executor to replace all older copies: updating the "cover" instructions whenever necessary.  The rest of the process is in the hands of a "higher power" as they say. 😇  

## Alternatives (potentially) {#alternatives}

At the time of this writing, and for the five years of the author's experience preceding it, there is no generally trusted means of simulating the process of batching funds and information for delivery upon the holder's confirmed death or incapacitation.  In fact, even proving that someone is living or dead (as for a [blockchain oracle](https://en.wikipedia.org/wiki/Blockchain_oracle) that a smart contract could use) is an infamously error-prone process.

### Use a commercial service (currently rare) {#outsourcing}

Now that you know what roles they would be fulfilling, you may feel confident evaluating whether any new company entering the crypto marketplace would be capable of doing this with enough technical and ethical reputation to reassure you whenever considering your own mortality.

In the last several years, the author has seen a very small number of companies offer such a service: including one on the Cardano blockchain.  None of them are still in operation today (and perhaps should not be referenced for professional reasons), which could be due to a daunting combination of liability risks and the uncertainty of "death confirmation" which is a mortal flaw for the usual certainty of a smart contract.

### Build the solution yourself {#diy}

In this case, you will inherit all the difficulties and uncertainties that have made businesses based on the "crypto will & testament" premise so rare in the market.  In the author's experience, [the most promising approach](https://forum.cardano.org/t/smart-contract-wallet-with-timer-for-protection-against-lost-seed-phrase-alternative-to-ledgers-private-key-sharing-scheme/118024) seems to be the "canary" (as per the expression *[canary in a coal mine](https://en.wikipedia.org/wiki/Sentinel_species#Canaries)*) or a *[dead man's switch](https://en.wikipedia.org/wiki/Dead_man's_switch)*:  

- First, verify a blockchain address that can be accessed by your beneficiary in the long term that includes your anticipated demise.
- Then, install a smart contract set up with a timer & the necessary signatures to transfer your funds after that timer (the "canary") runs out.
- Sending a message (e.g. transaction with certain metadata) to the resource the canary resets the timer.
- As long as you are of sound mind and body, you keep sending that message within that interval: if not, the "canary" assumes you are deceased or incapacitated and transfers the funds from your own accounts to the beneficiary.

Note that such a solution would not require the Frankenwallet because it would use the signing capabilities of blockchains themselves instead of manual decryption and application of keys for asset transfers.

### Share your fortune with inheritors using a multi-signature wallet {#multisig}

With sufficient trust in a technically competent beneficiary — arguably more difficult to achieve, and more rare to see, than a crypto fortune itself — the greatest peace of mind may be from installing a [multisig wallet](https://www.investopedia.com/multi-signature-wallets-definition-5271193) for you and your loved ones... so that a certain quorum of signatures, all agreeing upon your incapacitation, could then transfer funds out of the wallet to any designated inheritors.

This approach has the advantage of allowing you to see it in operation while still alive and healthy... and to make adjustments as long as you remain so, in cooperation with one or more of your beneficiaries.  If the goal is truly to retain peace of mind through the time of your own passing, perhaps the greatest assurance would be the confidence that your designated resources would practically already be in your inheritors' hands.
