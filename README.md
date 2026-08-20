# Tiny Turf — iOS App Store Setup

This folder is a ready-to-go Capacitor project. Your game lives in `www/index.html`.

## What's in here
- `www/index.html` — your actual game (the HTML file from before)
- `package.json` — dependencies Capacitor needs
- `capacitor.config.json` — tells Capacitor this is an iOS app called "Tiny Turf"

## Step 1 — Install Node.js (if you don't have it)
Download from https://nodejs.org (get the LTS version). This runs on Windows/Mac/Linux — no Mac required for this step.

## Step 2 — Install dependencies
Open a terminal in this folder and run:
```
npm install
npx cap add ios
```
This creates an `ios/` folder with a full Xcode project inside — but you don't need Xcode yourself. Codemagic will build it.

## Step 3 — Push this whole folder to GitHub
1. Create a free GitHub account if you don't have one (github.com)
2. Create a new repository (e.g. "tiny-turf")
3. Push this folder to it:
```
git init
git add .
git commit -m "Tiny Turf initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/tiny-turf.git
git push -u origin main
```

## Step 4 — Apple Developer account
Sign up at https://developer.apple.com/programs — $99/year. You need this regardless of build method; it's what lets you sign and submit apps.

## Step 5 — Codemagic
1. Sign up at https://codemagic.io (free tier covers this fine to start)
2. Connect your GitHub repo
3. Choose "Capacitor" as the project type
4. Connect your Apple Developer account inside Codemagic (they walk you through certificates/provisioning)
5. Run a build — Codemagic builds on their own cloud Mac, signs it, and can submit directly to App Store Connect

## Step 6 — App Store Connect listing
Once the build is submitted, go to https://appstoreconnect.apple.com to fill in your app's name, screenshots, description, age rating, etc. before it goes to review.

## Notes
- Change `appId` in `capacitor.config.json` from `com.yourname.tinyturf` to something unique to you (usually reverse-domain style, e.g. `com.johnsmith.tinyturf`) before building.
- Apple review can reject bare "webview wrapper" apps that feel too thin — it may help to add a native touch later (haptics, push notifications) via Capacitor plugins so it doesn't read as just a website in a box.
