---
layout: page
nav_order: 60
parent: Introduction
title: Is software encryption OK?
---
# Software encryption methods & their guarantees of security
{: .no_toc }
- TOC
{:toc}

{: .highlight }
_"Is software encryption enough to secure my life savings or livelihood?"_

... which must include a more detailed question, even for those having absolute confidence in the Frankenwallet's security itself:  

{: .highlight }
_"What prevents the files and data that I encrypt there from being broken into as soon as they're stored and transmitted through the outside world?"_

## Why AES encryption is common to Frankenwallet chosen tools {#why-aes}

AES (the [Advanced Encryption Standard](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard)) is the cipher common to these crucial Frankenwallet components:

1. [LibreOffice](https://www.libreoffice.org) (for encrypted documents: confidential text like passphrases)
1. [7-Zip](https://www.7-zip.org) which maintains the [`7z` format](https://www.7-zip.org/7z.html) archives (e.g. for key files)
1. [LUKS](https://en.wikipedia.org/wiki/Linux_Unified_Key_Setup) (for the encrypted disk partition itself)

The reassurance posted by the foremost expert in this field at the time — also a major influencer of realistic perceptions of cryptography through the decades ever since — is that the number of bit rearrangements necessary to even count through all the possible decryption keys for AES would still be beyond native human conception; as it still is nearly 30 years after this statement was published:  

> These numbers have nothing to do with the technology of the devices; they are the maximums that thermodynamics will allow. And they strongly imply that brute-force attacks against 256-bit keys will be infeasible until computers are built from something other than matter and occupy something other than space.  
> — [*Applied Cryptography*](http://www.schneier.com/book-applied.html), Bruce Schneier 1996, p. 158  
> — quoted & placed in context by himself in [Schneier on Security: The Doghouse, September 2009](https://www.schneier.com/blog/archives/2009/09/the_doghouse_cr.html)  

In other words, the numbers in the preceding paragraphs — indicating stellar if not galactic energy requirements for all these bit rearrangements — prove that the cracking problem of brute-forcing even a single AES key is one of either cosmic or geological scale: depending on whether you consider space or time.

At the time of this writing (late 2025) there is a [history of mitigation](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard#Known_attacks) — in which Dr. Schneier has been intimately involved, presenting what many believe is the best possible effort — demonstrating some reductions of this cosmic problem: which still fail to apply in any practical circumstance that would allow full 256-bit AES to be broken.  

We are now entering an era where quantum approaches to breaking ciphers will advance along with more mundane applications: but the same laws of physics that apply thermodynamic limitations to information density will also apply at some level to limit the density of optical frequency wave superpositions... and so Schneier's inventory of information density requirements would still apply.

Still we can assume we are headed, at some point, for an age in which quantum computing will require the redesign of encryption strategies at all levels.  Yet socially we will have years of advance notice before such technology creates a general vulnerability of full 256-bit AES: meaning that any insecurities from the Frankenwallet's perspective are determined *only* by assurances of the integrity of keys themselves: i.e. how workflow software handles your **passwords**.  

## Survey of potential vulnerabilities {#vulnerabilities}

These are some hypothetical questions to consider — for the above reason, all about the handling of your encryption password — for your own considerations of safety, so you can keep an eye on these key software packages and develop your own notions of security assurance or risk:

### Is the chain of software delivery by Linux media & update reliable? {#repositories}

Linux itself is just as susceptible to naive malware downloads as any OS like Windows would be, but our instructions (with any exceptions justified by their own security references) will only include packages that come from official Linux software repositories — notably LibreOffice, `7z`, and `srm`.

All packages in these repositories go through a rigid and manually cross-checked process for security auditors to confirm any changes and to ensure the distributed binaries match their open-source repositories (see [The Debian Free Software Guidelines (DFSG)](https://www.debian.org/social_contract.html#guidelines)).  

### Is document data not really encrypted, but only "locked" with a password like PDFs? {#true-encryption}

The commonly known ability to [unlock PDF documents without knowing the password](https://www.adobe.com/in/acrobat/how-to/unlock-pdf.html) should not lead users to believe *all* document encryption is equally "cosmetic" and therefore simply removable from the file.

LibreOffice, <a id="release-note"></a>[ever since version 3.5](https://wiki.documentfoundation.org/ReleaseNotes/3.5#Different_Encryption_Algorithm) (in [year 2012](https://www.libreoffice.org/about-us/libreoffice-timeline)), has encrypted all document data with 256-bit AES for all ODF files: i.e. when saving in its native Writer (Document), Calc (Spreadsheet), and related formats.

As this announcement indicates and source code view would confirm, all document data is encrypted *inside the document structure itself* according to a key that's only created from whatever password you enter when you [**Save with password**](https://help.libreoffice.org/25.8/en-GB/text/shared/guide/protection.html).

### Could a reclaimable version of the password somehow be stored in the unencrypted part of the file or archive: i.e. its metadata? {#back-door-metadata}

This would be a "back door" for the file itself, avoiding the much greater challenge of putting a [back door into the encryption algorithm](#back-door-in-cipher)... more like "leaving a key under the doormat" for the password or decryption key to be accessible somehow from the file metadata.

The reassurance on this point is the same as for the [chain of software delivery](#repositories): any code to do this would have to be entirely new and therefore reviewed by other code contributors, release managers, and repository maintainers before distributing it even to initial audiences.

But an even greater reassurance would be what it would do *to the affected files themselves*.  It is not only human beings that read encrypted LibreOffice documents and 7z archives... they are also routinely read and catalogued into document systems that parse these files, beginning with metadata.  Anyone working on such a system would see a historically unprecedented appearance of extraneous metadata in all newly created files, and would naturally and urgently question and report it: making even such an unlikely tampering very short-lived before that part of the code would be cut out.

### Can the password I enter be "grabbed" from a program by something else on the system? {#system-leaks}

Any uncertainty around this question points to why we are using the Frankenwallet in the first place.  Decades of evolution of the Unix and then the Linux security model have established practical isolation between all running programs: and the assurance of this is much greater if the operating environment has never been tampered with due to casual use.

Short of "bugs" in the program that would leak a password into the operating environment somehow, the remaining opportunity would be deliberate "hacking" by reading or poking at the system or running program's private memory space to see if these tiny opportunities could be exploited.

In practice, these types of attacks are extremely difficult even under the ideal circumstance where a malicious intruder has already "hacked" a desktop or server and therefore has the opportunity for iterative methods that might eventually find a region of system memory where a password could be kept in cleartext.

If you think this seems practically almost impossible, you are absolutely right.  This is made statistically even more improbable by the Frankenwallet's installation being "private" and there not known to be a target for such a difficult and long-term attack which could only be perpetrated by a specialised expert: who has somehow compromised your device during the limited amount of time you use it, through its limited (or no) Internet usage.  

### Could bugs appear that leave passwords exposed to due incompetence of the developers? {#inadvertent-bugs} 

We have to assume this is theoretically possible: but then the open source ecosystem provides more assurances.  As seen in the LibreOffice [release note](#release-note) above, the code for full 256-bit AES encryption from a user-entered password has been in place since 2012 (thirteen years, at the time of this writing) with no reason to modify it... *and* all kinds of alarms would go off in software repositories if it were.

The reassurance of `7z` — which has [similar longevity](https://www.7-zip.org/history.txt) for the essential components of its source code & encryption mechanisms — would be greater, since passwords are conveyed through either system-protected terminal input (when using the CLI) or the native Linux password & keychain libraries to handle passwords safely (when creating `7z` encrypted archives from the file manager).

Nevertheless, we might assume there could be "operator error" on the part of the software or repository maintainers, following either error or malice in the submission of an update that would "leak" a password in any of these programs as it was being typed.

That, again, is why our workflow model requires creating such encrypted documents and archives in the Frankenwallet.  Even if a program were so blatantly compromised that encrypting a file left an *actual cleartext copy* of its password in a directory known the the attacker, that artefact couldn't be accessed outside the Frankenwallet.

### Could any "back doors" be added to the AES algorithm used in these software packages? {#back-door-in-cipher}

No, because the algorithm would still have to behave [symmetrically](https://en.wikipedia.org/wiki/Symmetric-key_algorithm):

1. Any program implementing something purporting to be the AES algorithm would have to create an encrypted data stream only decryptable by the same code: therefore any program writing data with anything other than *bona fide* AES wouldn't be able to read it with AES.
2. Consequently: any "back door" for our essential programs would be *even more noticeable* in source code because it would have to *completely replace AES* somehow without anybody noticing.  

## Subjective reviews of essential software {#subjective}

### LibreOffice

In this 2020 question ([Is LibreOffice safe to use for creating very important documents?](https://ask.libreoffice.org/t/is-libreoffice-safe-to-use-for-creating-very-important-documents/59952)), with many thousands of undisputed views at this point, the conclusions are the same as those above & assumed for the foundation of Frankenwallet workflow:

1.  The best way to avoid ensuring the unbreakable encryption of a document with absolutely priceless contents is to handle the file only on a "Linux distro on a USB stick" — almost as conceived for the Frankenwallet (minus our added feature of persistent storage, but including the ability to encrypt and save files).
2.  The encryption of AES itself — plus the assurances that there are no artefacts in the file to provide any clue at all in its decryption — have long meant that **any LibreOffice file itself, without the password used to save it, is "lost" even to its creator**{: .text-green-200 }.

### 7-Zip

The security of 7-Zip has never been [challenged](https://en.wikipedia.org/wiki/7-Zip#Security) except when linked with other OS components such as the infamous DLLs: notorious for producing security problems through mainstream use on Windows.  Frankenwallet advocates and critics alike are welcome to identify any past security issue or data / password leak affecting the Linux platform: so the context can be elaborated here.  

Beyond this, Linux resources from many quarters identify `7z` as a robust and universal choice for simple archive creation (while others present "more convenient" alternatives), as in this 2021 review of its security features: [Encrypting and decrypting archives with 7-Zip](https://www.redhat.com/en/blog/encrypting-decrypting-7zip)  

## Security conclusions and operational guidelines {#summary}

{: .warning }
The guarantees here — both of AES's computational impregnability and lack of any back doors into the algorithm — don't apply to any of the encryptable [Microsoft- native document formats](https://en.wikipedia.org/wiki/Office_Open_XML) (DOCX, XLSX, etc., as per [this back-door PoC](https://www.slideshare.net/slideshow/backdoors-with-the-ms-office-file-encryption-master-key-and-a-proposal-for-a-reliable-file-format-by-mitsunari-shigeo-yoshinari-takesako/59669433)), nor to documents [sent with OpenPGP encryption](https://help.libreoffice.org/latest/he/text/shared/guide/openpgp.html) (an algorithm intended for transfer, _not_ encryption at rest).

Therefore: make sure in LibreOffice you always save confidential files with **File - Save As** and selecting **Save with password** in [OpenDocument file format](https://help.libreoffice.org/25.8/en-GB/text/shared/00/00000021.html) as indicated here: [Protecting Documents With Passwords When Saving](https://help.libreoffice.org/25.8/en-GB/text/shared/guide/protection.html)  

{: .new-title }
> tip
>
> This recommendation applies to *all* Linux operations (not necessarily Windows, which is designed to constantly leak personal data of all kinds) **even outside the Frankenwallet**: to provide privacy and security advantages in normal host system operation as well.

In fact this is the basis for keeping LibreOffice files encrypted whenever possible with the Frankenwallet [lower security password](/prepare/password-low) — so resources copied and created in the Frankenwallet can still be relatively secure even when accessing & modifying them on the host system.

This also works well in the other direction: documents on your usual desktop with elevated security beyond what you would normally encrypt (with a less unique password) can be encrypted with the "lower security" Frankenwallet password — where they can remain a part of the ongoing data used in your insecure workflow — while also being updatable in greater security when opened in the Frankenwallet.  

This leaves only your most confidential documents — those storing wallet passphrases and cryptocurrency keys — encrypted with the Frankenwallet [higher security password](/prepare/password-high) (never to be entered outside the Frankenwallet), and never touching the host system except for filing with your other documents and preparing backups as necessary.
