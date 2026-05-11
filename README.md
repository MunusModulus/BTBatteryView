# BTBatteryView (BTBTV)

**Version:** 0.3.0

BTBatteryView (BTBTV) is a small Windows utility that displays Bluetooth device battery levels reported by Windows in a desktop-widget-style window and the system tray.

It is intended for quickly checking Bluetooth device battery levels without opening the Windows 11 Settings app.

## Features

- Displays Bluetooth device battery levels reported by Windows
- Desktop-widget-style window
- System tray icon
- Restores the widget from the tray icon
- Right-click menu with `Refresh`, `Rescan`, and `Exit`
- Low-battery notification when a device reaches 10% or below
- Prevents multiple instances
- Saves widget position
- Advanced appearance customization via `appearance.json`

## Requirements

- Windows 11
- Bluetooth devices whose battery levels can be retrieved by Windows

Battery level retrieval is not guaranteed for all Bluetooth devices.

## Download

Download the latest `BTBatteryView.zip` from the Releases page.

## How to use

1. Download `BTBatteryView.zip`.
2. Extract the ZIP file.
3. Run `BTBatteryView.exe`.
4. If a supported device's battery level can be retrieved, it will be shown in the widget.
5. Pressing the `X` button does not exit the application; it hides the widget to the system tray.
6. To fully exit the application, right-click either the tray icon or the widget itself and select `Exit`.
7. If you connect a new device or the display is not updated, run `Rescan` from the right-click menu.

## Notes

- Only devices whose battery level can be retrieved by Windows are supported.
- Some devices may report only rough battery levels, such as in 10% increments.
- Battery levels are scanned once per minute.
- Battery level retrieval is not guaranteed for all Bluetooth devices.
- There is no installer. If you no longer need the application, delete the folder containing `BTBatteryView.exe`.

## Settings location

BTBatteryView stores settings under:

```text
C:\Users\<UserName>\AppData\Local\BTBatteryView\
```

For Japanese Windows users, `<UserName>` corresponds to your Windows user name.

Main saved data:

- Widget position
- Detected device cache
- Notification threshold
- Appearance settings

## Advanced appearance settings

BTBatteryView creates an `appearance.json` file in the following folder:

```text
C:\Users\<UserName>\AppData\Local\BTBatteryView\
```

Actual file:

```text
C:\Users\<UserName>\AppData\Local\BTBatteryView\appearance.json
```

Advanced users can edit this file directly to customize part of the appearance.

After editing `appearance.json`, fully exit and restart BTBatteryView.

### Notes

- `appearance.json` is a standard JSON file. Comments are not supported.
- Colors must be specified in `#RRGGBB` or `#AARRGGBB` format.
- If an individual value is invalid, the default value is used for that item.
- If the entire JSON file is invalid, the default appearance is used.

### Available appearance items

| Item | Description |
|---|---|
| `Opacity` | Widget opacity. `1.0` is fully opaque, `0.9` is slightly transparent. |
| `BackgroundColor` | Widget background color. |
| `ForegroundColor` | Main text color. |
| `MutedTextColor` | Sub text color, such as `Updated` or `No data`. |
| `RowBackgroundColor` | Device row background color. |
| `RowBorderColor` | Device row border color. |
| `BatteryWarningColor` | Battery percentage color when the level is 20% or below. |
| `LowBatteryColor` | Battery percentage color when the level is at or below the low-battery notification threshold. |
| `TrayPopupBackgroundColor` | Background color of the tray popup. |
| `TrayPopupForegroundColor` | Text color of the tray popup. |
| `TrayPopupBorderColor` | Border color of the tray popup. |

Example:

```json
{
  "Opacity": 0.95,
  "BackgroundColor": "#F5F2EA",
  "ForegroundColor": "#222222",
  "MutedTextColor": "#666666",
  "RowBackgroundColor": "#FFFFFF",
  "RowBorderColor": "#E68A2E",
  "BatteryWarningColor": "#D99000",
  "LowBatteryColor": "#D83A2E",
  "TrayPopupBackgroundColor": "#F5F2EA",
  "TrayPopupForegroundColor": "#222222",
  "TrayPopupBorderColor": "#E68A2E"
}
```

## Startup

BTBatteryView does not register itself to start automatically by default.

If you want it to start with Windows, create a shortcut to `BTBatteryView.exe` in the Windows Startup folder manually.

## License

Copyright (c) 2026 Munus Modulus.  
All rights reserved.

This software may not be copied, modified, redistributed, sublicensed, or sold without prior written permission from the copyright holder.

This software is provided "as is", without warranty of any kind.
