# Sye's Sleep Tracker 🌙

A small sleep tracker that lives on your phone's home screen and works like a normal app.

- **One big button**: tap *Start sleep* when the baby falls asleep and *Wake up* when they wake. The timer keeps going even if you close the app.
- **Today at a glance**: total sleep, number of naps and the longest stretch.
- **Bar chart**: daily sleep for the last 7, 14 or 30 days, split into night (purple) and naps (orange). Tap a bar to see that day.
- **History**: tap any entry to fix the times or delete it. Use **+ Add** for sleeps you forgot to log.
- **Private**: all data stays on your phone. Nothing is uploaded.
- **Works offline** once it has been opened once.

A "day" runs from 7am to 7am, so a night's sleep counts toward the evening it started. Sleep between 7pm and 7am counts as night, and anything else counts as a nap.

---

## One-time setup (about 5 minutes, no coding)

The app has to be put online once so your phone can open it. GitHub can do this for free.

### Step 1: Make this project public

GitHub only hosts free websites from public projects. This doesn't expose any of your baby's data, because that data only ever lives on your phone. The project contains just the app's code.

1. Open this project on github.com and tap **Settings** (top menu; on a phone, use "Desktop site" mode).
2. Scroll to the very bottom, to the **Danger Zone**, and tap **Change visibility** → **Make public**. Then confirm.

### Step 2: Turn on GitHub Pages

1. Still in **Settings**, tap **Pages** in the left menu.
2. Under **Build and deployment** → **Source**, choose **Deploy from a branch**.
3. Under **Branch**, pick **`claude/baby-sleep-tracker-app-vhuai3`** (or **`main`**, if this has been merged), leave the folder as **/ (root)**, and tap **Save**.
4. Wait about a minute and refresh the page. A link like this appears at the top:
   **`https://slavvitanov.github.io/Sleep-tracker/`**

### Step 3: Put it on your home screen

**iPhone** (use Safari)
1. Open the link above in **Safari**.
2. Tap the **Share** button (the square with an arrow) → **Add to Home Screen** → **Add**.

**Android** (use Chrome)
1. Open the link in **Chrome**.
2. Tap the **⋮** menu → **Add to Home screen** (or **Install app**).

Open it from the new home-screen icon from now on. It opens full screen like a real app.

---

## Good to know

- **Change the name**: tap the round initial in the top-right corner.
- **Back up your data** now and then: tap the round initial, then **Save a backup**, and keep the file somewhere safe (Files, Google Drive, email it to yourself). If you get a new phone, use **Restore from backup**.
- **Always use the home-screen icon.** Data saved in the home-screen app and data saved in a normal browser tab are kept separately.
- **Two phones?** Each phone keeps its own log. You can move entries between phones with backup and restore.
- **Updates**: if the app changes here, it updates itself the next time you open it with internet.

### Alternative if you'd rather keep the project private

Go to **[app.netlify.com/drop](https://app.netlify.com/drop)** on a computer. Download this project as a ZIP (green **Code** button → **Download ZIP**) and unzip it. Then drag the folder onto that page. You get a free link and can follow Step 3 with it.
