# Adapta KDE — Plasma 6 / KDE 6.3.6 (Debian 13.4 "Trixie") edition

> Originally a port of the [GTK theme Adapta](https://github.com/adapta-project/adapta-gtk-theme).
> Upstream Adapta GTK is frozen ([more info](https://github.com/adapta-project/adapta-gtk-theme/commit/4e74e0f569ed527b715ca3840f5d7701baebaf3c));
> this fork keeps the KDE side alive on **Plasma 6 / KDE Frameworks 6 / Qt 6**.

<p align="center">
  <img src="https://raw.githubusercontent.com/PapirusDevelopmentTeam/adapta-kde/master/preview.png" alt="Preview Adapta KDE"/>
  <sup><sub>Screenshot: Engine: <a href="https://github.com/tsujan/Kvantum/tree/master/Kvantum">Kvantum</a> | Kvantum Theme: Adapta Nokto | Aurorae decoration: Adapta | Plasma Theme: Adapta | Icons: <a href="https://github.com/PapirusDevelopmentTeam/papirus-icon-theme">Papirus-Adapta-Nokto</a> | File Manager: Dolphin | Calendar: <a href="https://invent.kde.org/plasma/plasma-workspace">Event Calendar</a></sub></sup>
</p>

In this repository you'll find:

- Aurorae Theme (KDecoration2/3 — works in KWin 6)
- Konsole Color Schemes
- Kvantum Themes (Qt 6 via `qt6-style-kvantum`)
- Plasma Color Schemes (with Plasma 6 `Header` color set)
- Plasma Desktop Theme
- Plasma Look-and-Feel package (with Qt 6 splash QML)
- Wallpaper
- Yakuake Skins

## Plasma 6 / KDE 6.3.6 compatibility

The theme has been updated for **KDE Plasma 6.3.6** as shipped in **Debian 13.4 "Trixie"**.
Notable changes since the Plasma 5 version:

- All KPackage manifests now ship a `metadata.json` (KPlugin schema) alongside the
  legacy `metadata.desktop` for backward compatibility.
- The look-and-feel splash QML no longer imports the removed `QtGraphicalEffects 1.0`
  module and uses unversioned Qt 6 `QtQuick` imports.
- Color schemes now include the `[Colors:Header]` and `[Colors:Header][Inactive]`
  sections introduced in KColorScheme 6, plus an explicit `accentColor`.
- The look-and-feel `defaults` file now also seeds the screen-locker (`kscreenlockerrc`).
- License identifiers updated to SPDX (`GPL-3.0-only`, `CC-BY-SA-4.0`).

## Installation

### Debian 13.4 (Trixie) and derivatives

Install the required runtime dependencies first:

```sh
sudo apt update
sudo apt install --no-install-recommends \
    qt6-style-kvantum kvantum \
    plasma-workspace plasma-desktop kwin-x11 \
    konsole yakuake \
    papirus-icon-theme breeze-cursor-theme
```

Then install Adapta KDE itself with the script below, or by cloning the repo and
running `sudo make install`.

### Adapta KDE Installer

Use the script to install the latest version directly from this repo (independently of your distro):

#### Install

```sh
wget -qO- https://raw.githubusercontent.com/PapirusDevelopmentTeam/adapta-kde/master/install.sh | sh
```

#### Uninstall

```sh
wget -qO- https://raw.githubusercontent.com/PapirusDevelopmentTeam/adapta-kde/master/install.sh | uninstall=true sh
```

### Build from source

```sh
git clone https://github.com/PapirusDevelopmentTeam/adapta-kde.git
cd adapta-kde
sudo make install            # system-wide, into /usr/share
# or
make install PREFIX=~/.local # per-user, into ~/.local/share
```

### Ubuntu

```sh
sudo add-apt-repository ppa:papirus/papirus
sudo apt-get update
sudo apt-get install --install-recommends adapta-kde
```

### Third-party packages

Packages in this section are not part of the official repositories. If you have a trouble or a question please contact the package maintainer.

| **Distro** | **Maintainer** | **Package** |
|:-----------|:---------------|:------------|
| Arch Linux | Bruno Pagani | `sudo pacman -S adapta-kde kvantum-theme-adapta` <sup>[[link](https://www.archlinux.org/packages/community/any/adapta-kde/)]</sup> |
| Arch Linux | Jan Neumann | [adapta-kde-git](https://aur.archlinux.org/packages/adapta-kde-git) <sup>AUR</sup> |
| openSUSE | Konstantin Voinov | [adapta-kde](https://software.opensuse.org/download.html?project=home:kill_it&package=adapta-kde) <sup>OBS [[link](https://build.opensuse.org/package/show/home:kill_it/adapta-kde)]</sub> |

**NOTE:** If you are a maintainer and want to be in the list please open an issue or send a pull request.

## Recommendations

- For a more polished look, use this pack with the [Kvantum engine](https://github.com/tsujan/Kvantum/tree/master/Kvantum)
  built against Qt 6 (`qt6-style-kvantum` on Debian).

  Run `kvantummanager` to choose and apply the **Adapta** or **Adapta Nokto** theme.

- Install the [Papirus-Adapta icon theme](https://github.com/PapirusDevelopmentTeam/papirus-icon-theme) for a more consistent and beautiful experience.

- Set tree-menu view in System Settings.

- In System Settings set **Noto Sans** as the font for title, menu and toolbar.

- Use 16 px toolbar icons without text (works best with the Papirus icon set).

- Apply everything in one go from System Settings → Appearance → Global Theme → **Adapta**.

## Hacks for small screen resolutions

- Install widgets such as [Window Title Applet](https://github.com/Zren/plasma-applet-window-title)
  and [Application Menu](https://invent.kde.org/plasma/plasma-workspace) and move them to the panel.
- Disable window buttons & titlebar on the decoration:

  Open the `Adaptarc` file inside the aurorae theme and set:
  ```
  ButtonHeight=0
  ButtonWidth=0
  TitleHeight=0
  TitleEdgeTop=0
  ```

## Known issues

- On some proprietary video drivers Aurorae has wrong rendering by default with the Adapta theme. See more info [here](https://github.com/PapirusDevelopmentTeam/adapta-kde/issues/21).
- After installing on top of an existing Plasma 6 session, log out and back in (or run `kbuildsycoca6 --noincremental`) so KPackage picks up the new `metadata.json` files.

## Donate

If you like this project, you can donate at:

<span class="paypal"><a href="https://www.paypal.me/varlesh" title="Donate to this project using Paypal"><img src="https://www.paypalobjects.com/webstatic/mktg/Logo/pp-logo-100px.png" alt="PayPal donate button" /></a></span>

## License

GNU GPL v3
