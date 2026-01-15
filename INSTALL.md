# Polonium Installation Guide

This guide will help you install Polonium on KDE Plasma 6.3.6+.

## Prerequisites

- **KDE Plasma 6.3.6 or newer**
- **Wayland session** (recommended, X11 has limited support)

## Installation Methods

### Method 1: KDE Store (Easiest) ⭐

This is the recommended method for most users.

1. Open **System Settings**
2. Navigate to **Window Management** → **KWin Scripts**
3. Click **Get New Scripts...**
4. Search for **"Polonium"**
5. Click **Install**
6. Check the box next to Polonium to enable it
7. Click **Apply**
8. **Log out and back in** to activate

### Method 2: Direct Download

Download and install the pre-built package:

```bash
# Download the latest release
wget https://github.com/zeroxoneafour/polonium/releases/latest/download/polonium.kwinscript

# Install the package
kpackagetool6 -t KWin/Script -i polonium.kwinscript

# If already installed, use -u to upgrade:
kpackagetool6 -t KWin/Script -u polonium.kwinscript
```

After installation:
1. Open **System Settings** → **Window Management** → **KWin Scripts**
2. Enable **Polonium**
3. Click **Apply**
4. **Log out and back in**

### Method 3: Build from Source

For developers or users who want the latest changes:

```bash
# Install prerequisites (if not already installed)
# On Arch/Manjaro:
sudo pacman -S npm kwin

# On Ubuntu/Debian:
sudo apt install npm kwin-dev

# On Fedora:
sudo dnf install npm kwin-devel

# Clone and build
git clone https://github.com/zeroxoneafour/polonium.git
cd polonium
make
```

This will automatically build and install Polonium. Then:
1. Open **System Settings** → **Window Management** → **KWin Scripts**
2. Enable **Polonium**
3. Click **Apply**
4. **Log out and back in**

## Post-Installation Setup

### Configure Recommended Settings

For the best experience (similar to Hyprland), configure these settings:

1. Open **System Settings** → **Window Management** → **Window Behavior**
2. Set these options:
   - **Window activation**: Focus follows mouse (mouse precedence)
   - **Delay focus**: 0ms
   - **Window actions modifier key**: Meta

### Learn the Keybindings

Default keybindings (you can customize these in System Settings → Shortcuts → KWin):

| Action | Keybinding |
|--------|------------|
| Toggle window tiling | `Meta+Shift+Space` |
| Switch focus (left/down/up/right) | `Meta+H/J/K/L` |
| Move window | `Meta+Shift+H/J/K/L` |
| Resize tiled window | `Meta+Ctrl+H/J/K/L` |
| Open tile editor | `Meta+T` |
| Cycle layouts | See System Settings → Shortcuts |

### Optional Enhancements

For an even better tiling experience:

1. **[dbus-saver](https://github.com/zeroxoneafour/dbus-saver)** - Saves your layouts across logout/login
2. **[Active Accent Borders](https://github.com/nclarius/Plasma-window-decorations)** - Bismuth-like borders for tiled windows
3. **[Geometry Change](https://github.com/peterfajdiga/kwin4_effect_geometry_change)** - Smooth tiling animations

## Verification

After logging back in, your windows should automatically tile. To verify:

1. Open a terminal window
2. Open another application
3. Windows should automatically arrange in a tiled layout

Press `Meta+Shift+Space` on a window to toggle tiling on/off.

## Troubleshooting

### Windows aren't tiling

- Ensure Polonium is enabled in **System Settings → KWin Scripts**
- Check if the application is filtered in Polonium settings
- Restart KWin: Log out and back in, or run `kwin_wayland --replace &`

### Keybindings don't work

- Open **System Settings → Shortcuts → KWin**
- Verify Polonium shortcuts are assigned
- Check for conflicting shortcuts
- Restart KWin after changing shortcuts

### Need help?

1. Enable debug mode in Polonium configuration
2. Restart KWin
3. Check logs: `journalctl --user --no-pager -e | grep -i "polonium"`
4. Report issues at: https://github.com/zeroxoneafour/polonium/issues

## Uninstallation

To remove Polonium:

1. Open **System Settings → Window Management → KWin Scripts**
2. Uncheck **Polonium**
3. Click **Apply**
4. Run: `kpackagetool6 -t KWin/Script -r polonium`

To remove old shortcuts:
```bash
# Edit and remove Polonium entries
nano ~/.config/kglobalshortcutsrc
```

---

**Enjoy your tiling window manager!** 🚀

For more information, see:
- [Usage Guide](docs/usage.md)
- [FAQ](docs/faq.md)
- [Project README](readme.md)
