<div align="center">

# Adapta KDE

**A Material-Design-inspired theme pack for KDE Plasma 6**

_Polished for **KDE Plasma 6.3.6** on **Debian 13.4 "Trixie"**_

[![Plasma](https://img.shields.io/badge/KDE%20Plasma-6.3.6-1d99f3?logo=kde&logoColor=white)](https://kde.org/plasma-desktop/)
[![Qt](https://img.shields.io/badge/Qt-6-41cd52?logo=qt&logoColor=white)](https://www.qt.io/)
[![Debian](https://img.shields.io/badge/Debian-13.4%20Trixie-a81d33?logo=debian&logoColor=white)](https://www.debian.org/)
[![License](https://img.shields.io/badge/License-GPL--3.0-blue.svg)](LICENSE)
[![Maintained](https://img.shields.io/badge/Maintained-yes-brightgreen.svg)](https://github.com/digitalxs/adapta-kde)

<img src="https://raw.githubusercontent.com/digitalxs/adapta-kde/master/preview.png" alt="Preview Adapta KDE" width="820"/>

<sup><sub>
Engine: <a href="https://github.com/tsujan/Kvantum/tree/master/Kvantum">Kvantum</a> ·
Kvantum theme: Adapta Nokto ·
Aurorae decoration: Adapta ·
Plasma theme: Adapta ·
Icons: <a href="https://github.com/PapirusDevelopmentTeam/papirus-icon-theme">Papirus-Adapta-Nokto</a> ·
File manager: Dolphin
</sub></sup>

</div>

---

## Overview

Adapta KDE is a cohesive Plasma theme pack inspired by Google's Material Design,
originally ported from the (now-frozen) [Adapta GTK theme](https://github.com/adapta-project/adapta-gtk-theme).
This fork keeps the KDE side actively maintained on the **Qt 6 / Plasma 6 / KDE Frameworks 6** stack.

The pack ships everything needed for a consistent desktop experience:

|                        |                                                                  |
| ---------------------- | ---------------------------------------------------------------- |
|  **Aurorae decoration**     | KDecoration2/3-compatible window borders                         |
|  **Color schemes**          | Adapta (light) & Adapta Nokto (dark), with Plasma 6 Header sets  |
|  **Konsole profiles**       | Matching terminal palettes                                       |
|  **Kvantum themes**         | Rich widget styling for Qt 6 apps via `qt6-style-kvantum`        |
|  **Plasma desktop theme**   | Panels, tray, widgets, tooltips                                  |
|  **Look-and-Feel package**  | Global theme with a Qt 6 splash screen                           |
|  **Wallpaper**              | Signature Adapta teal wallpaper                                  |
|  **Yakuake skins**          | Adapta and Adapta Nokto drop-down terminal skins                 |

---

## What's new in the 2026 release

The theme was audited end-to-end for Plasma 6 / KF6. Notable updates:

- **KPackage manifests** — every package now ships a `metadata.json` (KPluginMetaData
  schema) alongside the legacy `metadata.desktop` for back-compat with older tooling.
- **Qt 6 splash** — dropped the removed `QtGraphicalEffects 1.0` import, moved to
  unversioned `QtQuick` imports, fixed the splash `sourceSize` binding.
- **Plasma 6 color sets** — added `[Colors:Header]` and `[Colors:Header][Inactive]`
  sets plus an explicit `accentColor` so the scheme plays nicely with the new
  header-styled headerbars and the accent system.
- **Screen-locker seeding** — the Look-and-Feel `defaults` now also seeds
  `kscreenlockerrc` so the locker matches the desktop theme on first apply.
- **SPDX license tags** — metadata now uses `GPL-3.0-only` and `CC-BY-SA-4.0`.
- **Install tooling** — Plasma 6 cache paths are cleared on install; the Makefile
  prints a `kbuildsycoca6 --noincremental` hint after copy.

---

## Quick install

### Debian 13.4 "Trixie" (recommended)

```sh
# 1. Install runtime dependencies
sudo apt update
sudo apt install --no-install-recommends \
    qt6-style-kvantum kvantum \
    plasma-workspace plasma-desktop kwin-x11 \
    konsole yakuake \
    papirus-icon-theme breeze-cursor-theme

# 2. Install Adapta KDE
wget -qO- https://raw.githubusercontent.com/digitalxs/adapta-kde/master/install.sh | sh
```

### Build from source

```sh
git clone https://github.com/digitalxs/adapta-kde.git
cd adapta-kde

sudo make install               # system-wide, into /usr/share
# or
make install PREFIX=~/.local    # per-user, into ~/.local/share

kbuildsycoca6 --noincremental   # refresh the KF6 service cache
```

### Uninstall

```sh
wget -qO- https://raw.githubusercontent.com/digitalxs/adapta-kde/master/install.sh | uninstall=true sh
# or
sudo make uninstall
```

### Other distributions

| Distro             | Package                                                                                                                                                                    |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Ubuntu / Mint      | `sudo add-apt-repository ppa:papirus/papirus && sudo apt install adapta-kde`                                                                                               |
| Arch Linux         | `sudo pacman -S adapta-kde kvantum-theme-adapta`                                                                                                                           |
| Arch Linux (AUR)   | [`adapta-kde-git`](https://aur.archlinux.org/packages/adapta-kde-git)                                                                                                      |
| openSUSE           | [OBS: home:kill_it/adapta-kde](https://software.opensuse.org/download.html?project=home:kill_it&package=adapta-kde)                                                        |

> Third-party packages are maintained outside this repo. Please contact the
> respective maintainer for distro-specific issues.

---

## Applying the theme

Once installed, open **System Settings → Appearance → Global Theme** and pick
**Adapta**. This applies the Plasma theme, color scheme, Aurorae decoration,
splash screen and cursor in one go.

For the best result:

1. **Widget style** — run `kvantummanager`, select **Adapta** or **Adapta Nokto**,
   then in System Settings → Colors & Themes → **Application Style** pick
   **kvantum** (or **kvantum-dark**).
2. **Icons** — set [Papirus-Adapta / Papirus-Adapta-Nokto](https://github.com/PapirusDevelopmentTeam/papirus-icon-theme).
3. **Fonts** — System Settings → Fonts → **Noto Sans** for title, menu and toolbar.
4. **Toolbars** — icon size 16 px, no text.
5. **Terminal** — Konsole → Settings → Profiles → Color Scheme → **Adapta** /
   **Adapta Nokto**. Yakuake users: Settings → Skin → **adapta** / **adapta-nokto**.

---

## Tips for high-density / small-screen laptops

Disable window buttons and the titlebar to reclaim vertical space. Edit the
installed aurorae rc file:

```sh
$EDITOR /usr/share/aurorae/themes/Adapta/Adaptarc
```

and set:

```ini
[Layout]
ButtonHeight=0
ButtonWidth=0
TitleHeight=0
TitleEdgeTop=0
```

Combine with the [Window Title Applet](https://github.com/Zren/plasma-applet-window-title)
and [Application Menu applet](https://invent.kde.org/plasma/plasma-workspace) for a
single-row layout.

---

## Troubleshooting

<details>
<summary><b>The theme doesn't show up in System Settings</b></summary>

After the first install, KF6 needs to rebuild its service cache:

```sh
kbuildsycoca6 --noincremental
kquitapp6 plasmashell && kstart plasmashell
```

Log out and back in if System Settings still doesn't see the theme.
</details>

<details>
<summary><b>Aurorae borders render as a solid block (proprietary GPU drivers)</b></summary>

On some NVIDIA proprietary setups, Aurorae SVG compositing is broken. Workarounds:
disable window shadows in the Adaptarc file, or switch the compositor backend
from OpenGL to XRender in System Settings → Display → Compositor.

See [issue #21](https://github.com/digitalxs/adapta-kde/issues/21) for history.
</details>

<details>
<summary><b>Qt 5 apps ignore the theme</b></summary>

Plasma 6 runs on Qt 6. If you still launch Qt 5 apps (Latte Dock, older KDE
apps), install `qt5-style-kvantum` alongside `qt6-style-kvantum` and set
`QT_STYLE_OVERRIDE=kvantum` in your shell profile.
</details>

<details>
<summary><b>Splash screen doesn't appear / white flash on login</b></summary>

The 2026 release rewrote the splash for Qt 6. If you upgraded from a Plasma 5
theme install, clear the cached QML:

```sh
rm -rf ~/.cache/plasmashell/qmlcache/*
```

and log out / back in.
</details>

---

## Support the project

If Adapta KDE improves your desktop, consider supporting continued development:

<p align="center">
  <a href="https://www.buymeacoffee.com/digitalxs" title="Support this project on Buy Me a Coffee">
    <img src="https://img.buymeacoffee.com/button-api/?text=Buy%20me%20a%20coffee&emoji=&slug=digitalxs&button_colour=00bcd4&font_colour=ffffff&font_family=Inter&outline_colour=ffffff&coffee_colour=ffffff" alt="Buy Me a Coffee"/>
  </a>
</p>

---

## Authors & credits

Adapta KDE is the work of many contributors. The 2026 Plasma 6 / Debian 13.4
port is maintained by:

- **Luis Miguel P. Freitas** — maintainer of the 2026 edition, Plasma 6 port
- **DigitalXS** — sponsoring company of the ongoing Plasma 6 effort — <https://digitalxs.ca>

Original and upstream credits:

- **Alexey Varfolomeev** (`varlesh`) — original Adapta KDE port
- **Tsu Jan** — original `KvAdapta` Kvantum theme this pack builds upon
- **Papirus Development Team** — founding maintainers of the KDE port
- **The Adapta GTK project** — source of the visual language

See each subdirectory's `AUTHORS` file for per-component attributions.

---

## Contributing

Bug reports, fixes and distro packaging are welcome — open an issue or pull
request at <https://github.com/digitalxs/adapta-kde>.

If you package Adapta KDE for a distribution not listed above, please open a
PR adding it to the "Other distributions" table.

---

## License

Released under the **GNU GPL v3** (color schemes under **CC-BY-SA 4.0**).
See [`LICENSE`](LICENSE) for the full text.
