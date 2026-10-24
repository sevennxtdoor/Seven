# Seven

A Dynamic Island for Windows. A small black pill sits at the top of your screen, shows what's going on (music, timers, notifications, charging), and opens into a panel when you hover it.

Free to use. Made by one independent developer.

## Features

- **Live activities in the pill**: now playing with equalizer, live synced lyrics, timer and stopwatch, volume indicator, notification banners, charging status. When nothing is happening, the pill shows a small face that blinks (and falls asleep when you're away).
- **Pages in the panel** (swipe left/right with two fingers on the touchpad, or click the dots):
  - Music: cover, controls, progress, synced lyrics
  - Notifications: recent Windows notifications
  - Controls: volume and screen brightness
  - Timer and stopwatch
  - Weather and calendar
  - To-do list
  - Water intake tracker
  - Shelf: drop files on the pill to keep them handy, drag them back out later
- **Stays out of the way**: when a fullscreen video or game is running, the pill hides and leaves only a thin colored line at the top. When a maximized window covers it, it hides completely. Hold the cursor at the top edge of the screen to peek.
- Smooth spring animations, rendered through the Windows compositor (DWM).

## Install

1. Download `SevenSetup.exe` from the [latest release](https://github.com/sevennxtdoor/Seven/releases/latest).
2. Run it. It installs for your user only (no administrator rights needed) into `%LocalAppData%\Programs\Seven`.
3. Optionally tick "Start Seven when Windows starts".

The installer bundles the .NET runtime, so you don't need to install anything else.

To quit Seven, right-click the pill and choose **Quit Seven**. To remove it, use **Settings → Apps → Installed apps → Seven → Uninstall**.

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
- **Your data stays on your PC.** No account, no telemetry, no analytics, no server of its own. Your to-do list, water count and shelf items are saved only in `%AppData%\Seven\data.json`.
- **No keyboard logging.** Seven never reads what you type. Volume and brightness come from the Windows audio and WMI interfaces, not from your keys.
- **Startup is your choice.** Only if you tick it in the installer, a value named `Seven` is added to `HKCU\Software\Microsoft\Windows\CurrentVersion\Run`. The uninstaller removes it.
- **Notifications** are read through the official Windows notification permission, which Windows asks you to allow. They are only shown in the pill and never sent anywhere.

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
