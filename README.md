# BTBatteryView (BTBTV)

**Version:** 0.3.4

---

# 日本語

BTBatteryView（BTBTV）は、Windowsが取得しているBluetoothデバイスのバッテリー残量を、デスクトップウィジェット風のウィンドウとシステムトレイで確認できるWindows用ユーティリティです。

Windows 11の設定画面を開かずに、Bluetoothデバイスの残量をすばやく確認することを目的としています。

ウィジェットを常に最前面に表示したり、`appearance.json` を編集して外観の一部を変更することもできます。

## 主な機能

- Windowsが取得しているBluetoothデバイスのバッテリー残量を表示
- デスクトップウィジェット風ウィンドウ
- システムトレイ常駐
- トレイアイコンからウィジェットを再表示
- 右クリックメニュー
  - `Hide widget`
  - `Refresh`
  - `Rescan`
  - `Always on top`
  - `Test notification`
  - `Exit`
- システムトレイアイコンを左クリックしてバッテリー残量をポップアップ表示
- バッテリー残量が10%以下になった場合の低残量通知
- Windows App Notificationによる低残量通知
- 低残量状態が続く場合の再通知
- バッテリー残量がさらに低下した場合の再通知
- 通知動作を確認する `Test notification`
- 複数起動防止
- ウィジェット位置の保存
- `appearance.json` による簡易外観カスタマイズ

## 動作環境

- Windows 11
- Windows側でバッテリー残量を取得できるBluetoothデバイス

すべてのBluetoothデバイスでバッテリー残量を取得できることを保証するものではありません。

## ダウンロード

Releasesページの **Assets** から `BTBatteryView.zip` をダウンロードしてください。

`Source code (zip)` および `Source code (tar.gz)` はGitHubが自動生成するファイルで、配布用の実行ファイルは含まれていません。

## 使い方

1. `BTBatteryView.zip` をダウンロードします。
2. ZIPファイルを任意のフォルダへ展開します。
3. `BTBatteryView.exe` を起動します。
4. 対応デバイスのバッテリー残量をWindowsから取得できる場合、ウィジェットに表示されます。
5. `X` ボタンを押してもアプリケーションは終了せず、システムトレイへ格納されます。
6. 完全に終了する場合は、トレイアイコンまたはウィジェットを右クリックし、`Exit` を選択してください。
7. 新しいデバイスを接続した場合や表示が更新されない場合は、右クリックメニューから `Rescan` を実行してください。
8. 通知機能を確認する場合は、右クリックメニューから `Test notification` を実行してください。

## 注意

- Windowsがバッテリー残量を取得できるデバイスのみ対応します。
- デバイスによっては、10%刻みなど大まかな残量のみ報告される場合があります。
- バッテリー残量は約1分ごとに確認されます。
- すべてのBluetoothデバイスでバッテリー残量を取得できることを保証するものではありません。
- Windows App Notificationを使用するため、BTBatteryViewは通常権限で起動してください。
- 管理者権限で起動した場合、Windows App Notificationは利用できません。

## 設定保存先

BTBatteryViewの設定は以下に保存されます。

```text
C:\Users\<ユーザー名>\AppData\Local\BTBatteryView\
```

`<ユーザー名>` はWindowsのユーザー名に置き換えてください。

主な保存内容・関連設定：

- ウィジェット位置
- 検出済みデバイスのキャッシュ
- 低残量通知しきい値
- トレイポップアップ関連設定
- `appearance.json` による簡易外観カスタマイズ

通知関連のログは以下に保存されます。

```text
C:\Users\<ユーザー名>\AppData\Local\BTBatteryView\logs\
```

## 自動起動について

BTBatteryViewは標準ではWindows起動時の自動起動を登録しません。

Windows起動時に自動実行したい場合は、`BTBatteryView.exe` のショートカットをWindowsのスタートアップフォルダへ手動で登録してください。

## アンインストール

インストーラーはありません。

不要になった場合は、`BTBatteryView.exe` を含むフォルダを削除してください。

必要に応じて、以下の設定フォルダも削除できます。

```text
C:\Users\<ユーザー名>\AppData\Local\BTBatteryView\
```

## 上級者向け：外観設定

BTBatteryViewでは、以下のファイルを直接編集することで外観の一部を変更できます。

```text
C:\Users\<ユーザー名>\AppData\Local\BTBatteryView\appearance.json
```

このファイルは初回起動時に自動作成されます。

`appearance.json` を編集した後は、BTBatteryViewを完全終了してから再起動してください。

`X` ボタンはウィジェットを隠すだけです。完全終了する場合は、ウィジェットまたはトレイアイコンを右クリックして `Exit` を選択してください。

### appearance.jsonについて

- `appearance.json` は通常のJSONファイルです。コメントは使用できません。
- 色は `#RRGGBB` または `#AARRGGBB` 形式で指定します。
- 個別の値が不正な場合、その項目には既定値が使用されます。
- JSONファイル全体が不正な場合、既定の外観が使用されます。

### 外観設定項目

| 項目 | 説明 |
|---|---|
| `Opacity` | ウィジェットの透明度。`1.0` で完全不透明、`0.9` で少し透明になります。`0.30` ～ `1.00` の範囲に制限されます。 |
| `BackgroundColor` | ウィジェット背景色。 |
| `ForegroundColor` | メイン文字色。 |
| `MutedTextColor` | `Updated` や `No data` などの補助文字色。 |
| `RowBackgroundColor` | デバイス行の背景色。 |
| `RowBorderColor` | デバイス行の枠線色。 |
| `BatteryWarningColor` | バッテリー残量が20%以下の場合の残量表示色。 |
| `LowBatteryColor` | バッテリー残量が低残量通知しきい値以下の場合の残量表示色。 |
| `TrayPopupBackgroundColor` | トレイアイコン左クリック時に表示されるポップアップの背景色。 |
| `TrayPopupForegroundColor` | トレイポップアップの文字色。 |
| `TrayPopupBorderColor` | トレイポップアップの枠線色。 |
| `FontFamily` | ウィジェットおよびトレイポップアップで使用するフォント。例：`Yu Gothic UI`、`Segoe UI`、`Meiryo` |
| `FontSize` | ウィジェットの主な文字サイズ。`6.0` ～ `18.0` の範囲に制限されます。 |
| `StatusFontSize` | `Updated` や `No data` などの補助文字サイズ。`6.0` ～ `16.0` の範囲に制限されます。 |
| `AlwaysOnTop` | ウィジェットを常に最前面に表示するかどうか。右クリックメニューの `Always on top` からも切り替えられます。 |

### appearance.json の例

```json
{
  "Opacity": 0.9,
  "BackgroundColor": "#1F2026",
  "ForegroundColor": "#F2F2F5",
  "MutedTextColor": "#A8A8B3",
  "RowBackgroundColor": "#2A2C36",
  "RowBorderColor": "#5E6AD2",
  "BatteryWarningColor": "#D9A441",
  "LowBatteryColor": "#E35D6A",
  "TrayPopupBackgroundColor": "#1F2026",
  "TrayPopupForegroundColor": "#F2F2F5",
  "TrayPopupBorderColor": "#5E6AD2",
  "FontFamily": "Yu Gothic UI",
  "FontSize": 9,
  "StatusFontSize": 8,
  "AlwaysOnTop": false
}
```

---

# English

BTBatteryView (BTBTV) is a small Windows utility that displays Bluetooth device battery levels reported by Windows in a desktop-widget-style window and the system tray.

It is intended for quickly checking Bluetooth device battery levels without opening the Windows 11 Settings app.

The widget can also be kept always on top, and part of its appearance can be customized by editing `appearance.json`.

## Features

- Displays Bluetooth device battery levels reported by Windows
- Desktop-widget-style window
- System tray icon
- Restores the widget from the tray icon
- Right-click menu with:
  - `Hide widget`
  - `Refresh`
  - `Rescan`
  - `Always on top`
  - `Test notification`
  - `Exit`
- Tray popup display by left-clicking the system tray icon
- Low-battery notification when a device reaches 10% or below
- Modern Windows App Notifications for low-battery alerts
- Repeat notifications while a device remains at low battery
- Additional notification when the battery level drops further
- `Test notification` command for notification diagnostics
- Prevents multiple instances
- Saves widget position
- Simple appearance customization via `appearance.json`

## Requirements

- Windows 11
- Bluetooth devices whose battery levels can be retrieved by Windows

Battery level retrieval is not guaranteed for all Bluetooth devices.

## Download

Download `BTBatteryView.zip` from the **Assets** section on the Releases page.

`Source code (zip)` and `Source code (tar.gz)` are automatically generated by GitHub and do not contain the packaged executable.

## How to use

1. Download `BTBatteryView.zip`.
2. Extract the ZIP file.
3. Run `BTBatteryView.exe`.
4. If a supported device's battery level can be retrieved, it will be shown in the widget.
5. Pressing the `X` button does not exit the application; it hides the widget to the system tray.
6. To fully exit the application, right-click either the tray icon or the widget itself and select `Exit`.
7. If you connect a new device or the display is not updated, run `Rescan` from the right-click menu.
8. To verify notification functionality, select `Test notification` from the right-click menu.

## Notes

- Only devices whose battery level can be retrieved by Windows are supported.
- Some devices may report only rough battery levels, such as in 10% increments.
- Battery levels are scanned approximately once per minute.
- Battery level retrieval is not guaranteed for all Bluetooth devices.
- BTBatteryView should normally be run without administrator privileges.
- Windows App Notifications are unavailable when BTBatteryView is running elevated as administrator.

## Settings location

BTBatteryView stores settings under:

```text
C:\Users\<UserName>\AppData\Local\BTBatteryView\
```

Replace `<UserName>` with your Windows user name.

Main saved data and related settings:

- Widget position
- Detected device cache
- Low-battery notification threshold
- Tray popup display settings
- Simple appearance customization via `appearance.json`

Notification logs are stored under:

```text
C:\Users\<UserName>\AppData\Local\BTBatteryView\logs\
```

## Startup

BTBatteryView does not register itself to start automatically by default.

If you want it to start with Windows, create a shortcut to `BTBatteryView.exe` in the Windows Startup folder manually.

## Uninstall

There is no installer.

If you no longer need the application, delete the folder containing `BTBatteryView.exe`.

If desired, you can also delete the settings folder:

```text
C:\Users\<UserName>\AppData\Local\BTBatteryView\
```

## Advanced appearance settings

BTBatteryView allows part of its appearance to be customized by directly editing the following file:

```text
C:\Users\<UserName>\AppData\Local\BTBatteryView\appearance.json
```

This file is created automatically on first launch.

After editing `appearance.json`, fully exit BTBatteryView and restart it.

The `X` button only hides the widget. To fully exit, right-click the widget or tray icon and select `Exit`.

### Appearance file notes

- `appearance.json` is a standard JSON file. Comments are not supported.
- Colors must be specified in `#RRGGBB` or `#AARRGGBB` format.
- If an individual value is invalid, the default value is used for that item.
- If the entire JSON file is invalid, the default appearance is used.

### Appearance settings

| Item | Description |
|---|---|
| `Opacity` | Widget opacity. `1.0` is fully opaque, `0.9` is slightly transparent. The value is clamped to `0.30` - `1.00`. |
| `BackgroundColor` | Widget background color. |
| `ForegroundColor` | Main widget text color. |
| `MutedTextColor` | Sub text color, such as `Updated` or `No data`. |
| `RowBackgroundColor` | Device row background color. |
| `RowBorderColor` | Device row border color. |
| `BatteryWarningColor` | Battery percentage color when the battery level is 20% or below. |
| `LowBatteryColor` | Battery percentage color when the battery level is at or below the low-battery notification threshold. |
| `TrayPopupBackgroundColor` | Background color of the popup shown by left-clicking the system tray icon. |
| `TrayPopupForegroundColor` | Text color of the popup shown by left-clicking the system tray icon. |
| `TrayPopupBorderColor` | Border color of the popup shown by left-clicking the system tray icon. |
| `FontFamily` | Font family used by the widget and the system tray popup. Examples: `Yu Gothic UI`, `Segoe UI`, `Meiryo`. |
| `FontSize` | Main font size used by the widget. The value is clamped to `6.0` - `18.0`. |
| `StatusFontSize` | Font size for sub text such as `Updated` or `No data`. The value is clamped to `6.0` - `16.0`. |
| `AlwaysOnTop` | Whether to keep the widget always on top. This can also be toggled from `Always on top` in the right-click menu. |

### Example appearance.json

```json
{
  "Opacity": 0.9,
  "BackgroundColor": "#1F2026",
  "ForegroundColor": "#F2F2F5",
  "MutedTextColor": "#A8A8B3",
  "RowBackgroundColor": "#2A2C36",
  "RowBorderColor": "#5E6AD2",
  "BatteryWarningColor": "#D9A441",
  "LowBatteryColor": "#E35D6A",
  "TrayPopupBackgroundColor": "#1F2026",
  "TrayPopupForegroundColor": "#F2F2F5",
  "TrayPopupBorderColor": "#5E6AD2",
  "FontFamily": "Yu Gothic UI",
  "FontSize": 9,
  "StatusFontSize": 8,
  "AlwaysOnTop": false
}
```

---

## License

Copyright (c) 2026 Munus Modulus.  
All rights reserved.

This software may not be copied, modified, redistributed, sublicensed, or sold without prior written permission from the copyright holder.

This software is provided "as is", without warranty of any kind.
