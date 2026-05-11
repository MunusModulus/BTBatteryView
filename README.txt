BTBatteryView (BTBTV)
Version: 0.3.0
　Japanese↓ / English↓↓

◆概要
BTBatteryView(BTBTV)は、Windowsが取得しているBluetoothデバイスのバッテリー残量を
デスクトップウィジェット風ウィンドウとタスクトレイで確認できるツールです。

◆主な機能
- Bluetoothデバイスのバッテリー残量表示
- デスクトップウィジェット風表示
- Xボタンでトレイ格納
- トレイアイコンから再表示
- 右クリックメニューから Refresh / Rescan / Exit
- 10%以下になった時に低残量通知

◆使い方
1. BTBatteryView.exe を実行します。
2. 対応デバイスの残量が取得できる場合、ウィジェットに表示されます。
3. 「X」ボタンを押しても終了せず、トレイに格納されます。
4. 完全に終了する場合は、トレイアイコンもしくは本体を右クリックして 「Exit」 を選んでください。
5. 新しいデバイスを接続した場合や表示が更新されない場合は、右クリックメニューから Rescan を実行してください。

◆注意
- Windows側でバッテリー残量を取得できているデバイスのみ対象になります。
- デバイスによっては 10%刻みなど、粗い残量しか報告されない場合があります。
- 残量のスキャンは１分毎に行われます。
- すべてのBluetooth機器で残量取得を保証するものではありません。

◆設定保存先
C:\Users\ユーザー名\AppData\Local\BTBatteryView\

◆保存される主な内容
- ウィジェット位置
- 検出済みデバイスのキャッシュ

◆自動起動について
標準では自動起動を登録しません。
必要な場合は、ユーザー自身でスタートアップフォルダにショートカットを配置してください。

◆アンインストールについて
アンインストーラーはありません。BTBatteryView.exe を含むフォルダごと削除してください。

◆上級者向け：外観設定
BTBatteryViewは、以下の”appearance.json”を直接編集することで、外観の一部を変更できます。

C:\Users\ユーザー名\AppData\Local\BTBatteryView\appearance.json
(※「ユーザー名」は、Windowsのユーザー名に置き換えてください。)

このファイルは初回起動時に自動作成されます。
編集後はBTBatteryViewを終了し、再起動してください。
(X印は最小化です。右クリで”Exit”を。)

注意:
- appearance.json は通常のJSONです。コメントは書けません。
- 色は #RRGGBB または #AARRGGBB 形式で指定してください。
- 値が壊れている場合、その項目は既定値で扱われます。
- JSON全体が壊れている場合、外観設定は既定値で扱われます。

■設定項目:

Opacity
  ウィジェット本体の不透明度です。
  1.0 = 不透明、0.9 = 少し透過。
  安全のため 0.30 ～ 1.00 の範囲に丸められます。

BackgroundColor
  ウィジェット本体の背景色です。

ForegroundColor
  ウィジェット本体の通常文字色です。

MutedTextColor
  Updated / No data などの補助文字色です。

RowBackgroundColor
  デバイス行の背景色です。

RowBorderColor
  デバイス行の枠線色です。

BatteryWarningColor
  バッテリー残量が20%以下のときの％表示色です。

LowBatteryColor
  低残量通知しきい値以下のときの％表示色です。

TrayPopupBackgroundColor
  タスクトレイ左クリック時に表示されるポップアップの背景色です。

TrayPopupForegroundColor
  タスクトレイ左クリック時に表示されるポップアップの通常文字色です。

TrayPopupBorderColor
  タスクトレイ左クリック時に表示されるポップアップの枠線色です。

例:
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


----------

English summary
BTBatteryView (BTBTV) is a Windows utility that displays Bluetooth device battery levels reported by Windows in a desktop-widget-style window and the system tray.

Main features
- Displays Bluetooth device battery levels
- Desktop-widget-style window
- Minimizes to the system tray with the X button
- Can be restored from the tray icon
- Right-click menu with Refresh / Rescan / Exit
- Low-battery notification when a device reaches 10% or below

How to use
1. Run BTBatteryView.exe.
2. If a supported device's battery level can be retrieved, it will be shown in the widget.
3. Pressing the X button does not exit the application; it minimizes the widget to the system tray.
4. To fully exit the application, right-click either the tray icon or the widget itself and select "Exit".
5. If you connect a new device or the display is not updated, run "Rescan" from the right-click menu.

Notes
- Only devices whose battery level can be retrieved by Windows are supported.
- Some devices may report only rough battery levels, such as in 10% increments.
- Battery levels are scanned once per minute.
- Battery level retrieval is not guaranteed for all Bluetooth devices.
- There is no installer. If you no longer need the application, delete the folder containing BTBatteryView.exe.

Settings location
%LOCALAPPDATA%\BTBatteryView\

Main saved data
- Widget position
- Detected device cache
- Notification threshold

Startup
BTBatteryView does not register itself to start automatically by default.
If you want it to start with Windows, create a shortcut in the Startup folder manually.

Advanced: appearance settings
BTBatteryView creates an appearance.json file in the following folder.
Advanced users can edit this file directly to customize part of the appearance.

C:\Users\<UserName>\AppData\Local\BTBatteryView\

Actual file:
C:\Users\<UserName>\AppData\Local\BTBatteryView\appearance.json

After editing appearance.json, fully exit and restart BTBatteryView.

Notes:
- appearance.json is a standard JSON file. Comments are not supported.
- Colors must be specified in #RRGGBB or #AARRGGBB format.
- If an individual value is invalid, the default value is used for that item.
- If the entire JSON file is invalid, the default appearance is used.

Available items:
- Opacity
- BackgroundColor
- ForegroundColor
- MutedTextColor
- RowBackgroundColor
- RowBorderColor
- BatteryWarningColor
- LowBatteryColor
- TrayPopupBackgroundColor
- TrayPopupForegroundColor
- TrayPopupBorderColor
