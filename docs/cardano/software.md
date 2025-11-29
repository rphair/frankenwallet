---
layout: page
nav_order: 10
parent: Cardano secure workflow
title: Install Cardano CLI
---
# Set up Cardano CLI in the Frankenwallet
{: .no_toc }
- TOC
{:toc}

## Confirm you're OK using an official, pre-built package {#github-binaries-ok}

Many operators will be accustomed to building their own software, but there are security challenges in maintaining a suitable build environment without routine Internet access, for both:
- getting & updating the software to build
- getting & installing dependencies (for both building & running the software)

Therefore our recommendation is to download the official, pre-built [`cardano-node` Releases](https://github.com/IntersectMBO/cardano-node/releases) as they become available, according to the guidelines on this page.

{: .note }
If there is sufficient demand & justification, these instructions will be extended with a procedure (based on [Cardano Developer Portal > Getting `cardano-node`](https://developers.cardano.org/docs/get-started/cardano-node/installing-cardano-node)) to build the Cardano CLI (and Node) in the Frankenwallet itself... the original Frankenwallet instructions included this, before the official release packages for Linux became prompt & reliable.

## Preparation on host computer {#cli-prep}

➤ Make a subfolder of your [host folder]() called e.g. `pool-bin`.

➤ Go to the page for the most recent of the [`cardano-node` Releases](https://github.com/IntersectMBO/cardano-node/releases) tagged [**Latest**](https://github.com/IntersectMBO/cardano-node/releases/latest).

➤ Go to its **Assets** section and download the package ending `linux.tar.gz` (if it's not there yet, wait a day or so and/or post to the Cardano Forum or developer Discord and ask why).

➤ Extract the `cardano-cli` file from that archive (generally in the `bin` subdirectory).

➤ Rename it to the current version; e.g. for version `10.3.1`:
```bash
mv cardano-cli cardano-cli-10.3.1
```
... and move it into the subfolder (e.g. `pool-bin`) that you created earlier.  (You can delete the rest of the downloaded files.)

➤ Link the latest Cardano CLI binary to `cardano-cli`:

Since you will likely be doing this again when future versions come out, keeping `cardano-cli` as a symbolic link to the latest version will allow you to easily backtrack (without Internet access!) if something goes wrong with a newer version in the Frankenwallet.

In your `pool-bin` subdirectory, e.g.: for version `10.3.1`:

```bash
rm cardano-cli     # if that link exists
ln -s cardano-cli-10.3.1 cardano-cli
```

## Move CLI binary to the Frankenwallet {#cli-install}

Upon your next boot into the Frankenwallet, you'll be able to move the current version into a place where it will be called with every executed `cardano-cli` command and from any [operator scripts](/cardano/scripts) that you install:

➤ Make a subfolder of your Frankenwallet _home directory_ called `/bin`.

➤ Copy everything from the subdirectory you created your host folder there (including the symbolic link for `cardano-cli`... or recreate it).

Since `~/bin` is included in the default Ubuntu path, the next time you start a Terminal you can verify that `cardano-cli` is available:

```bash
cardano-cli --version
```

{: .note }
This version is currently likely to be greater than — in fact, in a different sequence of numbers from — the version number of the `cardano-node` package you downloaded & named the file with.  This is a consequence of the maintainers' release process.

{: .new-title }
> tip
>
> Therefore, if you want to ensure you're running the version you just installed, you can compare the **first 7 hex digits** of the `git` revision to ensure they match.

e.g. for the current release page at the time of this writing, [version 10.3.1](https://github.com/IntersectMBO/cardano-node/releases/tag/10.3.1) shows `b3f237b` in the web page header, which will match in the Frankenwallet:

```bash
$ ./cardano-cli-10.3.1 --version
cardano-cli 10.7.0.0 - linux-x86_64 - ghc-9.6
git rev b3f237b75e64f4d8142af95b053e2828221d707f
```
