# Seven

A Dynamic Island for Windows. A small black notch grows out of the top edge of your screen, shows what's going on (music, timers, notifications, charging), and opens into a panel when you hover it.

Free to use. Made by one independent developer. Website and live preview: https://sevennxtdoor.github.io/Seven/

## Features

- **Live activities in the notch**: now playing with equalizer, live synced lyrics, timer and stopwatch, volume indicator, notification banners, charging status. When nothing is happening, it shows a small face that blinks (and falls asleep when you're away), or a clock if you prefer.
- **Pages in the panel** (swipe left/right with two fingers on the touchpad, or use the arrows):
  - Music: cover, visualizer, progress, shuffle, skip and synced lyrics, on frosted glass tinted by the cover
  - Notifications: recent Windows notifications
  - Controls: volume and screen brightness
  - Timer and stopwatch
  - Weather and calendar
  - To-do list
  - Water intake tracker
  - Shelf: drop files on the notch to keep them handy, drag them back out later
  - Clipboard history (off by default, text only, kept in memory)
  - Settings
- **Swipe to skip or seek**: swipe sideways over the cover to change song, or to jump 10 seconds.
- **Music card when away**: with music playing, a glass card with the controls appears in the middle of the screen after a minute without input.
- **Stays out of the way**: during a fullscreen video or game it leaves only a thin colored line at the top. Behind a maximized window it hides, and drops down briefly for volume changes, notifications and timers. Hold the cursor at the top edge of the screen to peek.
- Smooth spring animations, rendered through the Windows compositor (DWM).

## Install

1. Download `SevenSetup.exe` from the [latest release](https://github.com/sevennxtdoor/Seven/releases/latest).
2. Run it. It installs for your user only (no administrator rights needed) into `%LocalAppData%\Programs\Seven`.
3. Optionally tick "Start Seven when Windows starts".

The installer bundles the .NET runtime, so you don't need to install anything else.

Updating keeps your data: just run the new installer over the old version.

Settings live in the panel: right-click the notch and choose **Settings**. To quit Seven, right-click the notch and choose **Quit Seven**. To remove it, use **Settings → Apps → Installed apps → Seven → Uninstall**.

Requires Windows 10 version 2004 (build 19041) or newer, or Windows 11.

## You'll probably see a warning. That's expected.

Seven is new, and Windows hasn't seen it downloaded many times yet, so it shows a caution message. Here's how to get past it.

**In your browser: "SevenSetup.exe isn't commonly downloaded"**

1. In your downloads, click **See more** (or **…**) next to the file.
2. Choose **Keep**.
3. Click **Show more**, then **Keep anyway**.

**When you open it: "Windows protected your PC"**

1. Click **More info**, then **Run anyway**.
2. Follow the installer. Seven appears at the top of your screen.

The warning will fade as more people install Seven and Windows gets to know it.

## Why you can trust it

- **No admin rights** and nothing hidden: it installs for your user only and uninstalls cleanly from Settings.
- **Your data stays on your PC.** No account, no telemetry, no analytics, no server of its own. Your to-do list, water count, shelf items and settings are saved only in `%AppData%\Seven\data.json`.
- **Clipboard history is opt-in.** It's off until you turn it on in Settings. It keeps text only, in memory, never on disk, skips anything password managers mark as private, and is erased when you turn it off or close Seven.
- **No keyboard logging.** Seven never reads what you type. Volume and brightness come from the Windows audio and WMI interfaces, not from your keys.
- **Startup is your choice.** Only if you tick it in the installer, a value named `Seven` is added to `HKCU\Software\Microsoft\Windows\CurrentVersion\Run`. The uninstaller removes it.
- **Notifications** are read through the official Windows notification permission, which Windows asks you to allow. They are only shown in the notch and never sent anywhere.

### The only network connections

All over HTTPS, directly to free public services:

| Service | Why | What is sent |
|---|---|---|
| [lrclib.net](https://lrclib.net) | Synced lyrics | Title, artist and length of the song that's playing |
| [ipwho.is](https://ipwho.is) | Find your approximate city for the weather | Nothing besides the request itself, so the service sees your IP address |
| [open-meteo.com](https://open-meteo.com) | Weather forecast | The approximate latitude/longitude from the step above |

### Verify your download

Only download Seven from this page. Each release lists the SHA-256 hash of `SevenSetup.exe`. Check yours in PowerShell:

```powershell
Get-FileHash .\SevenSetup.exe -Algorithm SHA256
```

The hash must match the one on the release page. If it doesn't, don't run the file.

## Feedback

Found a bug or have an idea? [Open an issue](https://github.com/sevennxtdoor/Seven/issues).

## License

Freeware, see [LICENSE](LICENSE). Free to use; please don't redistribute, sell or modify it. © Seven (sevennxtdoor)
