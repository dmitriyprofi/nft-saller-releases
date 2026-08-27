# NFT saller releases

Public release-only distribution channel for **NFT saller**.

This repository intentionally contains **no application source code, private keys, wallets, API credentials, databases, user data, or development secrets**.

## Channels

- `beta` — owner-first testing channel.
- `stable` — employee/user channel after owner verification.

A version promoted from `beta` to `stable` must use the **same exact installer bytes and cryptographic hash**. Do not rebuild between beta approval and stable promotion.

## Publication path

Local Codex uses only its already-proven ordinary Git workflow. It does not need GitHub CLI, a new PAT, or a second login.

- push staging branch `publish-beta` -> workflow publishes mutable release tag `beta`;
- push staging branch `publish-stable` -> workflow publishes mutable release tag `stable`;
- installer is staged as small chunks to avoid GitHub's per-file Git size limit;
- `.github/workflows/publish-release.yml` reassembles and cryptographically verifies the exact pinned installer before creating the release with the repository-scoped GitHub Actions token;
- successful workflow removes the temporary staging branch where possible.

## Release assets

Each update channel release contains the exact Electron/NSIS update trio produced by the private source repository build:

- `NFT saller Setup <version>.exe`
- matching `.blockmap`
- `latest.yml`

The application verifies installer size and SHA-512 from the HTTPS manifest before installation.

## Security

The private source repository remains private. Never publish source archives, credentials, wallet secrets, OpenSea API keys, GitHub tokens, local databases, logs containing secrets, or owner/employee personal data here.
