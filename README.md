# Contraction Tracker

Track labour contractions: length, interval, last-hour statistics and a hint when the 5-1-1 rule is reached.
UI languages: German, English, French. Dark by default, switchable to light with the button in the header.
All entries stay on the device (in the browser or in the app); nothing is sent anywhere.

## Structure

```
web/        The app as HTML (runs in any browser, on GitHub Pages and as an installable web app)
android/    Android project that shows the same files from web/ as a native app
.github/    Automation: publishes web/ to GitHub Pages and builds the Android APK
```

Changes are made only in `web/index.html`. The Android app picks up the file automatically on the next build.

## 1. Web app on GitHub

1. Create a new repository on github.com (e.g. `contraction-tracker`).
2. Unzip the archive, open the `contraction-tracker` folder and upload its **contents**
   (`.github`, `android`, `web`, `README.md`) to the `main` branch. `.github` must sit at the repository root.
3. In the repository: **Settings → Pages → Build and deployment → Source: GitHub Actions**.
4. Under **Actions**, the workflow "Deploy web app to GitHub Pages" runs. Afterwards the app is available at
   `https://<your-github-name>.github.io/contraction-tracker/`.

Note: a GitHub Pages site is publicly reachable. Nobody can see the recorded contractions, though,
because they are stored only in the browser of each device.

### Install as an app

- **PC (Chrome or Edge):** open the page → click the install icon in the address bar
  (or menu → "Install app"). It then gets its own window and a Start menu icon.
- **Android (Chrome):** open the page → menu ⋮ → "Add to home screen" / "Install app".
- **iPhone (Safari):** open the page → Share → "Add to Home Screen".

After the first visit the app also works offline.

Without GitHub: just open `web/index.html` in a browser by double-clicking it.

## 2. Android app (APK)

### Option A: let GitHub build it

1. After uploading, the workflow "Build Android app" runs automatically under **Actions**.
2. Open the finished run → download `contraction-tracker-apk` under **Artifacts** and unzip it.
3. Copy `app-debug.apk` to the phone and open it. Android asks once whether to allow installs
   from this source → allow.

### Option B: build it yourself with Android Studio

1. Install Android Studio.
2. **File → Open** → select the `android` folder. Android Studio downloads Gradle and the SDK itself.
3. Connect the phone via USB (developer options + USB debugging on) and click **Run ▶**,
   or use **Build → Build App Bundle(s) / APK(s) → Build APK(s)**.

The app keeps the screen on while it is open and vibrates briefly on each tap.

## Important

This tracker is no substitute for medical advice. If your waters break, you bleed, have constant severe pain
or feel less movement from the baby, contact your midwife, hospital or emergency services (112) right away.
