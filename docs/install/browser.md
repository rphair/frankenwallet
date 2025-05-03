---
layout: page
nav_order: 50
parent: Installation
title: Securing the browser
---


# Securing the Firefox browser (to the extent this may be possible) {#reasons-to-secure-firefox}
{: .no_toc }
- TOC
{:toc}

{: .new-title }
> hint
>
> Even if you will keep this environment "cold" and never connect it to the Internet again — neither for software nor any kind of upgrades — you are still safer with more secure Firefox settings.

This is in case:
- the host is accidentally connected to the Internet when booted from Frankenwallet
- some system compromise becomes pending when an HTML file is opened, which by default happens in the browser… with the default browser being Firefox.

## Reasons to harden these settings categorically (rather than wait for any Internet use) {#more-reasons}

This also creates some flexibility in case you end up keeping your Frankenwallet for a while and decide to judiciously connect your Frankenwallet to the Internet under controlled circumstances:

- It’s likely you’ll need to reconnect the Internet every once in a while and *with great* prejudice may need a browser to get software.
- Therefore we must remove institutionalised security breaches from Firefox, whose source code is pretty secure but whose default settings are far too open.
- Remember Firefox changes and moves these options constantly so there’s no way off assuring this list is complete from one month to the next.
  - i.e. when you see out in your "hot" environment that Firefox has had a substantial upgrade, ou’ll have to go over every setting in Preferences to make sure you’re not divulging your Internet presence in some new way.
- NOTE following the advice in this section is **precautionary only** and *does not* make it “safe” to browse the Internet.

{: .important-title }
> suggestion
>
> Whenever possible, whether your environment is cold or only "cool", don't use *any* browser when you can download files & packages with the [`wget`](https://linux.die.net/man/1/wget) command on the Frankenwallet.

This approach may not work so well for web pages (e.g. even this simple one, which reviews other assets like style sheets & embeded images to view it properly) but is an excellent habit for downloading archives & software: for which no browser environment or interpretation is needed.
- Even when software installations are automated, or interactive through a web site, you can often determine the direct download URL from sites like GitHub, GitLab, Ubuntu Launchpad, or the vendor's own web site.

{: .new-title }
> better yet...
>
> Download those pages, files & packages from your "hot" environment into the host folder, where you can access them in your Frankenwallet without compromising your security at all... [as originally recomended](/prepare/computer/#recommendations-for-the-host-computer) for these installation pages.

## Firefox settings for security & privacy in an intermittent air-gap {#firefox-settings-outline}
(from latest ESR release at publication time)

{: .note }
For brevity and convenience — and also because these settings are subject to so much change (and already be different) — these have been kept in outline rather than narrative form, so users can click through them as quickly as possible.  The presentation of this material, and the content, are open to suggestion [via the repository](https://github.com/rphair/frankenwallet).

General \> Browsing \> untick these two options:

- Recommend extensions as you browse
- Recommend features as you browse

Home \>

- New Windows and Tabs \> New Windows and Tabs: set both to “Blank page”
- Firefox Home Content: untick EVERYTHING

Search \>

- Search Bar: select “Add search bar in toolbar”
  - to avoid inadvertently searching for something if you type a badly formatted URL
- Default search engine: DuckDuckGo (doesn’t really matter, since we stop it from searching, so upon general principles)
- Search Suggestions: untick everything
- Search Engines: remove everything except DuckDuckGo (Firefox *requires* you to leave one behind :zany:)
  - We don’t want some commercially provided plugin to ever run in response to something being searched from the browser.
  - FYI Firefox updates may bring these back (if you ever find out how to stop that from happning please let us know.)

Privacy and Security \>

- Enhanced Tracking Protection \>
  - select Strict
  - DO NOT send DO NOT TRACK requests (and you will not be going anywhere that tracks you)
- Cookies: make a point to check which ones are stored every once in a while.
  - if you have more cookies than you would need for a Github or Gitlab login, you are getting yourself into trouble :angry:
- Logins and Passwords \> UNTICK EVERYTHING
  - otherwise it will use the “Firefox Lockwise” service to determine if you’re trying to save a password on a “breached website” (see [link](https://support.mozilla.org/1/firefox/79.0/Linux/en-GB/lockwise-alerts))
- Forms and Autofill \> UNTICK EVERYTHING
- Permissions \> nothing to change here, but DO NOT ALLOW Firefox to grant any web site access to ANY of these.
  - Keep in mind that passwords and wallet key phrases can be gleaned from the camera and/or the noise you make when you type on the keyboard.
- Firefox Data Collection and Use \> UNTICK EVERYTHING
- Deceptive content \> UNTICK EVERYTHING
  - Since you're not visiting any deceptive or malicious sites, it's better that you don't telegraph *all* your Internet visits to analytics services.
- Certificates \> UNTICK box for Query responder servers

Sync \> disabled by default.  Don't ever use this!

## For Google Chrome users

If you are incapacitated on the Internet without Google Chrome, FYI you can [install the Brave package](https://brave.com/linux) which provides similar UI conventions and conveniences without the famous Google intrusions upon user privacy:

... before closing your air gap in the final installation step (on next page).

{: .warning }

If you **do** choose to use Brave, keep in mind you must be willing to reconnect to the Internet periodically for updates through its own software repository: after a given time without updates (estimated 3 to 6 months), the software will display an "out of date" message until reconnecting to the Internet and manually upgrading (run `apt install brave-browser`).

This is a decided advantage of Firefox, and hence its preference for the Frankenwallet (though not well supported by Cardano light wallets as of 2025): the fact that it remains a good HTML and web page previewer indefinitely without any software updates beyond the originally installed Linux distribution.

{: .new-title }
> help wanted
>
> As requested above with Firefox, and in general perhaps with multiple browser choices someday, user and operator suggestions about the list of security settings to tighten & tweak is open to [suggestion via the repository](https://github.com/rphair/frankenwallet).
