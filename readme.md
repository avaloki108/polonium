<div align="center">

# polonium

An autotile manager for Plasma 6.

An (unofficial) spiritual successor to [Bismuth](https://github.com/Bismuth-Forge/bismuth) built on KWin 6.

The descendant of [autotile](https://github.com/zeroxoneafour/kwin-autotile).

![hot icon](https://raw.githubusercontent.com/zeroxoneafour/polonium/master/docs/logo.svg)

[![KDE Store](https://img.shields.io/badge/KDE%20Store-Install-blue?style=for-the-badge&logo=KDE&logoColor=white&labelColor=blue)](https://store.kde.org/p/2140417)
[![GitHub](https://img.shields.io/badge/GitHub-Source%20Code-grey?style=for-the-badge&logo=GitHub&logoColor=white&labelColor=grey)](https://github.com/zeroxoneafour/polonium)

[![wayland: supported](https://img.shields.io/badge/Wayland-Ready-blue?logo=kde)](https://community.kde.org/KWin/Wayland)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://makeapullrequest.com)

</div>

## features

-   **Plasma 6.3.6+ Compatible** - Fully updated for the latest KDE Plasma releases
-   **Zero Configuration** - Works out of the box with sensible defaults
-   **Wayland Native** - Built for modern Wayland Plasma 6.3.6 and up
-   **Multiple Tiling Layouts** - BTree, Half, Three Column, Monocle, and KWin floating
-   **Visual Tile Editor** - Edit tile sizes with the integrated KWin GUI (Meta+T)
-   **Keyboard & Mouse Control** - Move and tile windows with Vim-style keybindings or mouse
-   **Per-Desktop Settings** - Configure layouts independently for each desktop, activity, and screen
-   **Persistent Configuration** - [DBus integration](https://github.com/zeroxoneafour/dbus-saver) to save layouts and configurations after logging out

## quick start

### Installation (Easy Method)

> **📖 For detailed installation instructions, see [INSTALL.md](INSTALL.md)**

**Option 1: KDE Store (Recommended)**
1. Open System Settings → Window Management → KWin Scripts
2. Click "Get New Scripts..."
3. Search for "Polonium"
4. Click "Install"
5. Enable the script and click "Apply"

**Option 2: Direct Download**
```bash
# Download the latest release
wget https://github.com/zeroxoneafour/polonium/releases/latest/download/polonium.kwinscript

# Install using kpackagetool6
kpackagetool6 -t KWin/Script -i polonium.kwinscript

# Or if already installed, upgrade:
kpackagetool6 -t KWin/Script -u polonium.kwinscript
```

**Option 3: Build from Source**
```bash
# Clone the repository
git clone https://github.com/zeroxoneafour/polonium.git
cd polonium

# Build and install (requires npm and kpackagetool6)
make
```

### First Use

After installation, **restart KWin** (log out and back in, or run `kwin_wayland --replace &` on Wayland).

**Default Keybindings:**
- `Meta+Shift+Space` - Toggle window tiling
- `Meta+H/J/K/L` - Switch focus between windows (Vim-style)
- `Meta+Shift+H/J/K/L` - Move window in direction
- `Meta+Ctrl+H/J/K/L` - Resize tiled windows
- `Meta+T` - Open tile editor
- Cycle layouts - Open System Settings → Shortcuts → KWin → Polonium

**Recommended Settings** (System Settings → Window Management):
- Window activation: Focus follows mouse (mouse precedence)
- Delay focus: 0ms
- Window actions modifier key: Meta

That's it! Your windows will now automatically tile. See [docs/usage.md](docs/usage.md) for advanced configuration.

## X11

X11 has been briefly tested but is not supported. If you encounter an issue running the script on X11, make sure it is reproducible in Wayland before submitting a bug report.

## building from source

### Prerequisites
- `npm` (Node Package Manager)
- `kpackagetool6` (KDE Package Management Tool)

### Build Commands

```bash
# Clone the repository
git clone https://github.com/zeroxoneafour/polonium.git
cd polonium

# One-step build and install
make

# Or run individual steps:
make build      # Build the package
make install    # Install/reinstall to KWin
make clean      # Clean build artifacts
make cleanall   # Clean build and package file
```

### Development Commands

```bash
make start      # Load the script in KWin (for development)
make stop       # Unload the script from KWin
make lint       # Run linters
```

## troubleshooting

**Shortcuts not working?**
- Check System Settings → Shortcuts → KWin and ensure Polonium shortcuts are set
- Restart KWin after setting shortcuts (log out/in)

**Windows not tiling?**
- Ensure the script is enabled in System Settings → KWin Scripts
- Check if the window is in the filter list (Settings → KWin Scripts → Polonium → Configure)
- Try manually toggling tiling with `Meta+Shift+Space`

**Need logs?**
1. Enable debug mode in Polonium settings
2. Restart KWin (log out and back in)
3. Run: `journalctl --user --no-pager -e | grep -i "polonium"`

See [docs/faq.md](docs/faq.md) for more help.

## license

Majority of this project is [MIT licensed](https://github.com/zeroxoneafour/polonium/blob/master/license.txt), please bum my code if you can use to make something better. Make sure to give credit though!

## name

Came from a comment on my old script, you can find the script and comment [here](https://store.kde.org/p/2003956)
