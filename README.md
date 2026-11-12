<div align="center">

<img src="snap/gui/wealthfolio.png" alt="Wealthfolio logo" width="128" />

# Wealthfolio

**Track your investments, net worth and spending privately on your own computer.**

[![wealthfolio](https://snapcraft.io/wealthfolio/badge.svg)](https://snapcraft.io/wealthfolio)
[![Base: core26](https://img.shields.io/badge/Base-core26-2C8C3C?logo=canonical&logoColor=white)](https://snapcraft.io/core26)
![Confinement: strict](https://img.shields.io/badge/Confinement-strict-2C8C3C)
[![Maintainer: sidaliteir](https://img.shields.io/badge/Maintainer-sidaliteir-2C8C3C?logo=snapcraft&logoColor=white)](https://snapcraft.io/publisher/sidaliteir)
![Architectures: amd64 and arm64](https://img.shields.io/badge/Architectures-amd64%20%7C%20arm64-2C8C3C?logo=linux&logoColor=white)

[Getting Started](#getting-started) · [Configure](#configure) · [Limitations](#limitations) · [Build](#build) · [Support](#support) · [License](#license)

Unofficial snap packaging for [Wealthfolio](https://github.com/wealthfolio/wealthfolio), a private, local-first portfolio tracker for investments, net worth, spending and financial plans. It is built from the source of upstream's tagged releases and published with permission from Teymz Inc. It is not the official build; official downloads are at [wealthfolio.app](https://wealthfolio.app).

</div>

---

## Getting Started

<a href="https://snapcraft.io/wealthfolio"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install wealthfolio
sudo snap connect wealthfolio:password-manager-service
wealthfolio
```

You can also open Wealthfolio from the application menu. Create your profile, add an account, then record activities or import them from a CSV file.

Wealthfolio stores secrets in your desktop keyring through the Secret Service, for example GNOME Keyring. The snap reaches the keyring only through the `password-manager-service` interface, which is not connected automatically. Without it, Wealthfolio still starts and tracks your data locally, but these features fail: saving market data and AI provider API keys, signing in to Wealthfolio Connect, device sync, cloud backups, addon secrets, profile passwords and database encryption. Your keyring must be unlocked. You can connect the interface while Wealthfolio is running; the next action that uses the keyring picks it up.

## Configure

Use the application's settings. There are no `snap set` options.

| Data | Location |
| --- | --- |
| Profiles, databases, backups, addons, web view storage and logs | `~/snap/wealthfolio/current/.local/share/com.teymz.wealthfolio` |
| Window size and position | `~/snap/wealthfolio/current/.config/com.teymz.wealthfolio` |

Each snap revision keeps its own copy of this data, so `snap revert` also returns to the data as it was before the last refresh.

Optional connections:

```bash
sudo snap connect wealthfolio:login-session-observe   # lock protected profiles when the screen locks, and after sleep
sudo snap connect wealthfolio:removable-media         # CSV files and backups on /media or /mnt
```

## Limitations

- The in-app updater is turned off at build time with upstream's setting for distribution packages. Wealthfolio still announces new releases with their notes, then refers you to `sudo snap refresh wealthfolio`. Update checks can be turned off in the application's settings.
- If you protect a profile with a password or encrypt its database, the key is in your keyring. Keep `password-manager-service` connected; copying the data folder alone is not a complete backup. Use **Export backup** for a portable copy.
- Data from another Wealthfolio installation, in `~/.local/share/com.teymz.wealthfolio`, is not visible to the snap. Use **Export backup** there and **Restore backup** in the snap.
- A native installation uses the same keyring entries and the same single-instance name as the snap. Do not run both at the same time.
- Files for import, export and backups must be in your home directory or on connected removable storage. Hidden folders directly under your home directory are not accessible.

## Build

The recipe builds the tagged upstream source without patches, with upstream's build settings for distribution packages: the in-app updater off, and Wealthfolio Connect enabled with upstream's public settings for source builds.

```bash
git clone https://github.com/sidalit/wealthfolio-snap.git
cd wealthfolio-snap
sudo snap install snapcraft --classic
snapcraft pack
```

## Support

- **Installation or snap issues:** [open a packaging issue](https://github.com/sidalit/wealthfolio-snap/issues).
- **Application bugs:** [report them upstream](https://github.com/wealthfolio/wealthfolio/issues).

## License

Snap packaging: [MIT](https://github.com/sidalit/wealthfolio-snap/blob/main/LICENSE). Wealthfolio is licensed under the [AGPL-3.0](https://github.com/wealthfolio/wealthfolio/blob/main/LICENSE). Wealthfolio is a trademark of Teymz Inc.
