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

Unofficial snap packaging for [Wealthfolio](https://github.com/wealthfolio/wealthfolio), a private, local-first portfolio tracker for investments, net worth, spending and financial plans.

</div>

---

## Getting Started

<a href="https://snapcraft.io/wealthfolio"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install wealthfolio
sudo snap connect wealthfolio:password-manager-service
```

## Configure

There are no `snap set` options; everything is set in the app.
Your profiles, databases, backups and add-ons live in `~/snap/wealthfolio/current/.local/share/com.teymz.wealthfolio`, and each snap revision keeps its own copy, so `snap revert` returns to the data as it was before the last refresh.

Optional connections:

```bash
sudo snap connect wealthfolio:login-session-observe   # lock protected profiles when the screen locks
sudo snap connect wealthfolio:removable-media         # files on /media or /mnt
```

## Limitations

- Updates come through `snap refresh`; the in-app updater only announces new releases.
- Copying the data folder is not a full backup when profiles are protected or encrypted, because the keys are in your keyring. Use **Export backup** instead.
- Data from a native installation is not visible to the snap. Move it with **Export backup** and **Restore backup**.

## Build

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
