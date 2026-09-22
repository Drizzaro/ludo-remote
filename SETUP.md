# Ludo King — Admin Remote Dice Control Setup Guide

## Overview

This system lets you monitor active Ludo matches and control dice values in real-time from any phone or computer browser.
- **Match Number System**: Every game automatically generates a unique 4-digit Match Number (e.g. `#1234`) displayed cleanly at the top-left of the game screen.
- **Zero Disruptions**: No popup bubbles or dialogs appear when a match starts.
- **Admin Portal**: Protected by a login screen where admins can see live matches and control dice for any player color.

---

## Step 1: Create a Free Firebase Project

1. Go to: [https://console.firebase.google.com](https://console.firebase.google.com)
2. Click **Add project** → Name it (e.g. `ludo-control`)
3. Disable Google Analytics (optional) → **Create project**

---

## Step 2: Enable Realtime Database

1. In your Firebase project sidebar: **Build** → **Realtime Database**
2. Click **Create database**
3. Choose a location → Start in **Test mode** → **Enable**
4. Copy the Database URL shown (e.g. `https://YOUR-ID-default-rtdb.firebaseio.com`)

---

## Step 3: Register Android App & Add `google-services.json`

1. In Firebase Console: Project Overview → **Add app** → Click **Android** icon
2. Android package name: `com.vinaykpro.ludoking`
3. Click **Register app**
4. Download `google-services.json`
5. Place the downloaded file at: `app/google-services.json`

---

## Step 4: Set Database URL in Android App

Open: `app/src/main/java/com/vinaykpro/ludoking/RemoteControlManager.java`

Update this line with your actual Firebase project URL:
```java
public static String FIREBASE_DB_URL = "https://YOUR-PROJECT-ID-default-rtdb.firebaseio.com";
```

---

## Step 5: Open or Host the Admin Controller Website

The web controller file is at: `remote_controller/index.html`

### Option A — Instant Local Use (No Hosting Required)
Simply double-click `remote_controller/index.html` in your browser, or open it on any device.

### Option B — Free Cloud Hosting (Netlify Drop)
1. Visit [app.netlify.com/drop](https://app.netlify.com/drop)
2. Drag and drop the `remote_controller` folder
3. Instantly get a public URL accessible from any mobile phone or browser

### Option C — GitHub Pages
1. Push this repository to GitHub
2. Repository Settings → Pages → Select `main` branch → `/remote_controller` directory

---

## Step 6: How to Log In & Control Matches

1. Open the website.
2. Sign in with the admin credentials:
   - **Username**: `admin`
   - **Password**: `admin4ludo`
3. Paste your Firebase Database URL in the top bar (e.g. `https://your-id-default-rtdb.firebaseio.com`) and click **Save & Connect**.
4. When a match starts in the Android app:
   - The match number is displayed at the top-left (e.g. `#4829`).
   - The match will automatically appear under **Live Matches** on the website.
   - You can click on the match in the list, or type the match number directly in the **Match #** box and click **Go**.
5. Tap **1, 2, 3, 4, 5, or 6** for any color (Red, Green, Blue, Yellow):
   - The game phone will instantly roll that exact number on that player's turn!
   - Tap **🎲** to return that color to normal random rolling.
   - Use **All Sixes** or **All Random** for batch actions.
