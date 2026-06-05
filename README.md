# Youtube-to-MP3-Local-Converter
YouTube to MP3 Local Converter is a lightweight desktop application that converts YouTube videos into high-quality MP3 audio files directly on your local machine. Designed for speed, privacy, and ease of use, it processes downloads locally without relying on external cloud services, giving users full control over their media conversion workflow.

## Getting Started

### Requirements
- Windows 10 or later
- Python 3.8+ (only needed to build the EXE)

**Installation & Setup Instructions**

1) Install Python using the following installer:
https://www.python.org/ftp/python/pymanager/python-manager-26.2.msix

2) Download the file **yt-mp3-exe-builder-v7.zip**.
   
4) Extract the contents of **yt-mp3-exe-builder-v7.zip** to a folder of your choice.
   
6) Open the extracted folder and run **BUILD.bat**.
   
8) Once the build process is complete, navigate to the **yt-mp3-exe\dist folder**.
   
10) Launch the application by running **YouTube-to-MP3.exe**.
    
12) If Windows displays any security warnings or prompts, **allow the application to run** and **approve any necessary exceptions**.
    
14) Your **default web browser will automatically open** and connect to the locally hosted application.
   _(Closing Webpage = Application running in the background will also autostop)_

### First Run

On first launch the app will:
1. Download ffmpeg automatically (~70 MB, one time only)
2. Open `http://localhost:5000` in your browser
3. Be ready to convert

---

## Usage

1. Paste a YouTube URL into the input field (or bulk-paste a list)
2. Choose your quality and format
3. Optionally set a save folder (e.g. `C:\Users\You\Music`)
4. Hit **Convert All** — or turn on **Auto-convert** to skip that step
5. Files save directly to your chosen folder

## Features

| Feature | Description |
|---|---|
| **Batch queue** | Add URLs one at a time or paste a whole list — convert them all in one go |
| **Multiple formats** | Export as MP3, M4A, WAV, or OGG |
| **Quality selector** | Choose 64, 128, 192, or 320 kbps per session |
| **Auto-convert** | Toggle on to start converting the moment a URL is added |
| **Quality badge per item** | Every track in the queue shows its quality and format (e.g. `192 kbps · MP3`) |
| **Per-item progress %** | Live percentage counter on each track while it converts |
| **Overall progress bar** | Gradient bar showing combined progress across all items during batch conversion |
| **Mass download** | Appears automatically when multiple items finish — downloads all at once |
| **Custom save folder** | Type any folder path and files save there automatically, no Download button needed |
| **Auto browser launch** | Opens in your browser automatically on startup |
| **Browser-close shutdown** | Detects when the tab is closed and shuts the server down cleanly |
| **ffmpeg auto-install** | First launch downloads and sets up ffmpeg automatically — no manual setup |
| **Single EXE** | Python, Flask, and yt-dlp are fully bundled — just double-click and run |

## Bug Fixes

- **yt-dlp not found in EXE** — Switched from subprocess to the yt-dlp Python API so it works correctly when bundled
- **PyInstaller flag conflict** — Removed `--collect-all` CLI flag that conflicts when a `.spec` file is used
- **`pyinstaller` command not found** — `BUILD.bat` now uses `python -m PyInstaller` which works regardless of PATH
- **Files not saving to custom folder** — Output path is now snapshotted at job-creation time and passed directly into the conversion thread
- **Browse button scanning entire folder** — Replaced broken folder-picker with a plain text input for the save path
- **Server staying alive after browser close** — Heartbeat system pings every 3s; server shuts down if pings stop for 6s
- **Custom folder files deleted on clear** — Clear now only removes files from the internal default folder, never a user-defined path
