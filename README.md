
# Drag Clicking on Linux

A simple community discovered workaround to enable drag click registration on Linux using a custom `libinput` quirk.

## Requirements

- A Linux distribution that uses a compatible version of `libinput`.
- A mouse capable of drag clicking.
- Administrator privileges through `sudo`.

## Installation

### 1. Create the Configuration File

Open a terminal and execute:

```bash
sudo mkdir -p /etc/libinput
sudo nano /etc/libinput/local-overrides.quirks
```

### 2. Add the Configuration

Paste the following configuration into the file:

```ini
[disable-debounce]
MatchName=*
ModelBouncingKeys=1
```

### 3. Save the File

If you are using Nano:

1. Press `Ctrl + O` to save.
2. Press `Enter` to confirm.
3. Press `Ctrl + X` to exit.

### 4. Restart Your Computer

```bash
sudo reboot
```

**You should be able to drag click now.**

## How It Works

- `[disable-debounce]` is the section identifier.
- `MatchName=*` matches any device name.
- `ModelBouncingKeys=1` enables the corresponding `libinput` quirk for matching devices.

## Optional

### Apply the Quirk Only to Mice

If you want to restrict the configuration to devices classified as mice, replace `MatchName=*` with `MatchUdevType=mouse`.

```ini
[disable-debounce]
MatchUdevType=mouse
ModelBouncingKeys=1
```

## Removing the Configuration

Open the file:

```bash
sudo nano /etc/libinput/local-overrides.quirks
```

Remove the section you added, save the file, and reboot.

## Community Compatibility List

If this workaround works for you, consider sharing your Linux distribution and mouse model by opening a pull request to help other users.

## References

- [libinput Device Quirks Documentation](https://wayland.freedesktop.org/libinput/doc/latest/device-quirks.html)
- [Reddit: Disable double-click prevention / lower debounce time](https://www.reddit.com/r/linux_gaming/comments/ku6gth/disable_double_click_preventionlower_debounce_time/)
- [Reddit: Linux drag-clicking discussion](https://www.reddit.com/r/linux_gaming/comments/1amqxyy/linux_not_registering_drag_clicks/)
