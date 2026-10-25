# Seven

A Dynamic Island for Windows. A small black notch grows out of the top edge of your screen, shows what's going on (music, timers, notifications, charging), and opens into a panel when you hover it.

Free to use. Made by one independent developer. Website and live preview: https://sevennxtdoor.github.io/Seven/

## Features

- **Live activities in the notch**: now playing with equalizer, live synced lyrics, timer and stopwatch, volume indicator, notification banners, charging status. When nothing is happening, a small light drifts slowly across the notch (and settles into a slow pulse when you're away), or it shows the time if you prefer.
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

## Screens Windows may show while installing

Windows double-checks programs it hasn't met often, and every new version of Seven starts fresh.

| Where | What it says | What to click |
|---|---|---|
| Your browser's downloads | "isn't commonly downloaded" | **…** → **Keep** → **Show more** → **Keep anyway** |
| When you open the installer | "Windows protected your PC" | **More info** → **Run anyway** |

## What Seven does, and doesn't

It does:

- Install into your user folder without admin rights, and uninstall cleanly from Settings → Apps.
- Keep one local file, `%AppData%\Seven\data.json`, for your to-dos, water count, shelf links and settings. It's saved through a temporary file, so a crash can't empty it.
- Show Windows notifications in the notch after Windows asks for your permission.
- Start with Windows only if you leave that box ticked in the installer (a value named `Seven` under `HKCU\Software\Microsoft\Windows\CurrentVersion\Run`, removed again by the uninstaller).

It never:

- Reads your keys. Volume and brightness come from the Windows audio and WMI interfaces.
- Saves your clipboard. Clipboard history is off by default; when on, it's text only, in memory, skips what password managers mark private, and is gone when Seven closes.
- Copies your files. The shelf only remembers where they are.
- Has an account, telemetry, analytics or a server of its own.

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
