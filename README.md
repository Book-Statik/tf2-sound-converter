TF2 Sound Converter

A small local desktop app for turning any audio file into a Team Fortress 2 hitsound or killsound, packaged and ready to drop into your TF2 folder.

Everything runs locally in the app window — audio is never uploaded anywhere.

Features
Drag & drop or browse to load an audio file (.wav, .mp3, .ogg, .m4a, .flac, or any browser-decodable audio)
Preview the file before converting
Choose whether it becomes a Hitsound or Killsound
Adjust output volume (-24 dB to +12 dB) before export
Export TF2 ZIP — a ready-to-extract archive with the correct tf/custom/... folder structure
Download WAV — just the converted .wav file, if you want to place it manually
Built with Electron, so it runs as a normal desktop app on Windows and Linux
Installation
Run from source

Requires Node.js (includes npm).

bash
npm install
npm start

This launches the app in an Electron window.

Build a standalone app
bash
# Linux AppImage
npm run package:linux

# Windows installer (.exe)
npm run package:windows

Packaged builds are placed in the dist/ folder by electron-builder.

Usage
Launch the app.
Drag an audio file onto the drop area, or click it to browse for one.
Pick Hitsound or Killsound.
Adjust the output volume slider if needed.
Click Export TF2 ZIP to download a zip file, or Download WAV to just get the audio file.
Extract the ZIP directly into your TF2 installation folder (it already contains the correct tf/custom/TF2SoundConverter/sound/ui/ path), or place the WAV manually at:
   tf/custom/TF2SoundConverter/sound/ui/hitsound.wav
   tf/custom/TF2SoundConverter/sound/ui/killsound.wav
Restart TF2 (or reload the custom content) to hear your new sound in-game.
How it works
Audio decoding and resampling happen in-browser via the Web Audio API (AudioContext.decodeAudioData).
The decoded audio is resampled to 44.1kHz, volume-adjusted, and encoded into a 16-bit PCM WAV file.
For the ZIP export, the WAV is packed (uncompressed/"stored") into a .zip with the folder structure TF2 expects for custom sounds.
Project structure
├── main.js         # Electron entry point / window setup
├── index.html      # App UI and all conversion logic
├── package.json    # Dependencies and build config (electron-builder)
└── README.md
Notes
No internet connection or server is used — conversion happens entirely on your machine.
Only the left audio channel is used for conversion (output is mono), which matches typical TF2 hitsound/killsound files.
