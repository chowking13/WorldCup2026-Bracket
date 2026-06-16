# World Cup 2026 Bracket — Windows Desktop App (.exe)

This builds the bracket into a real Windows installer (`.exe`). After installing,
it runs in its own window with its own icon and Start-menu entry — no browser.
Your scores and predictions save automatically between launches.

There are two ways to produce the `.exe`. Pick whichever fits you.

---

## OPTION 1 — Build in the cloud (no Windows PC, nothing to install)

GitHub builds the `.exe` for you on a real Windows machine and gives it to you to
download. Easiest route if you don't have a Windows computer set up for development.

1. Create a free account at https://github.com
2. Make a new repository (the green **New** button). Name it anything, e.g.
   `wc2026-bracket`. Leave it empty (no README).
3. Upload this whole folder to it:
   - On the new repo page click **"uploading an existing file"**
   - Drag in **all** files and folders from this project (including the hidden
     `.github` folder — see note below) and click **Commit changes**.
4. Open the **Actions** tab of your repo. A job called **"Build Windows
   Installer"** starts automatically. Wait ~3-5 minutes for the green check.
5. Click into that finished run, scroll to **Artifacts**, and download
   **"World-Cup-2026-Bracket-Windows-Installer"**. Unzip it — your `.exe` is inside.

That `.exe` is the installer. Double-click it on any Windows PC to install the app.

> Note: if dragging doesn't include the `.github` folder (some browsers hide
> dotfolders), use **GitHub Desktop** (https://desktop.github.com) to add the
> folder instead, or re-zip the whole folder and upload that.

---

## OPTION 2 — Build it yourself on a Windows PC

1. Install **Node.js** (LTS) from https://nodejs.org
2. Open **Command Prompt** or **PowerShell** in this folder.
3. Run:

       npm install
       npm run dist:win

4. The installer appears in the new `dist/` folder:

       dist/World Cup 2026 Bracket Setup 1.0.0.exe

Double-click it to install.

---

## Files in this project

    main.js                                Electron startup (window + loads bracket)
    index.html                             The bracket (all HTML/CSS/JS in one file)
    package.json                           App metadata + Windows build settings
    build/icon.png                         App icon
    .github/workflows/build-windows.yml    The cloud-build recipe (Option 1)

To update the bracket later, replace `index.html` and rebuild.

---

## Notes

- **First-launch warning:** because the app isn't code-signed (signing needs a paid
  Microsoft certificate), Windows SmartScreen may say "Windows protected your PC."
  Click **More info -> Run anyway**. Normal for indie/unsigned apps.
- **Size:** the installer is ~80-150 MB because it bundles the Chromium runtime
  that lets it run without a browser. Standard for Electron apps.
- **Saved data** lives on each machine locally. Use the in-app **Export / Import**
  buttons to move a bracket between computers.
