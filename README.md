# Sye's Sleep & Feed Tracker 🌙🍼

A small tracker for sleeps and feeds that lives on your phone's home screen and works like a normal app.

- **A little face** at the top that keeps Sye company. It's animated frame by frame, with round eyes and flat lids. It sleeps while Sye sleeps, and is awake and curious otherwise.
  - It blinks, glances around and looks wherever you tap.
  - It gets drowsy the longer Sye is awake: heavier lids after 1½ hours, half-closed after 2 hours, and nodding off and yawning after 2½ hours.
  - It yawns when a sleep starts and pops its eyes open on wake-up.
  - Its pupils grow when you tap Liquids or Solids, and it chews when you log solids.
  - Tap it and it looks surprised, or tap it five times quickly. If Sye is asleep, it just peeks one eye open.
- **One big button**: tap *Start sleep* when the baby falls asleep and *Wake up* when they wake. The timer keeps going even if you close the app.
- **Feeds**: tap **Liquids** or **Solids** under the timer.
  - **Liquids**: choose Milk, Formula or Water and optionally type the amount in ml, or tap a quick size. It remembers your last amount.
  - **Solids**: type what was eaten (e.g. *potato, broccoli*) or tap suggestions, and optionally add the amount in grams. Suggestions learn from foods you've logged before.
- **Today at a glance**: night sleep (last night, or tonight once it's evening), total nap time and number of naps today, the longest stretch, plus time since the last drink, millilitres drunk today and the last meal.
- **Sleep chart**: like Apple Health. **7D / 14D / 30D** show one column per day, with the time of day running down from 7am to 7am. Each sleep is a block at the time it happened (night in purple, naps in yellow), so the gaps show when Sye was awake. **24H** shows the last 24 hours on one horizontal line. Feeds show as dots at the time they happened (light blue for liquids, green for solids). Use the **Feeds** switch under the chart to hide or show them. The heading shows night sleep and naps as separate totals (averages for 7D–30D). Tap a day, a sleep block or a feed dot for details.
- **Timeline**: sleeps and feeds together, newest first, with each day's totals and the time between drinks. It starts with the last 3 days; tap **Show more days** to load 3 more. Tap any entry to change or delete it. Use **+ Add** for anything you forgot to log.
- **Private**: all data stays on your phone, unless you turn on sync with your partner (optional, see below).
- **Sync with your partner** (optional): log on either phone and see it on both.
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

- **Settings and the baby's name**: scroll to the top and tap the round initial in the top-right corner.
- **Back up your data** now and then: tap the round initial, then **Save a backup**, and keep the file somewhere safe (Files, Google Drive, email it to yourself). If you get a new phone, use **Restore from backup**.
- **Always use the home-screen icon.** Data saved in the home-screen app and data saved in a normal browser tab are kept separately.
- **Two phones?** Without sync, each phone keeps its own log. To share one log, set up [sync](#sync-between-two-phones).
- **Updates**: if the app changes here, it updates itself the next time you open it with internet.

---

## Sync between two phones

Sync lets you and your partner log on either phone and see the same log on both, live. It uses **Firebase**, Google's free app database. You set it up once, which takes about 10 minutes. A computer makes it easier, but a phone works too.

**Cost:** free. Firebase's free "Spark" plan doesn't need a card, and a baby log uses a tiny fraction of its limits.

**Privacy:** the log is stored in your own Firebase project. Your two phones share a random 20-character **family code**, which works like a password. Anyone who has the code can see and change the log, so keep it between the two of you.

### Part 1: Create the database (once)

1. Go to **[console.firebase.google.com](https://console.firebase.google.com)** and sign in with a Google account.
2. Tap **Create a project** (it may say **Get started with a Firebase project**).
   - Name it `sleep-tracker` and tap **Continue**.
   - If it asks about **Gemini** or **Google Analytics**, turn them **off**. You don't need them.
   - Tap **Create project**, wait a few seconds, then tap **Continue**.
3. In the left menu, open **Build** (or **Databases & Storage**) → **Firestore Database**, and tap **Create database**.
   - If it asks for an edition, pick **Standard**.
   - **Location**: choose one near you (for example `eur3 (europe)` in Europe, or `nam5 (us)` in the US). Tap **Next**.
   - Choose **Start in production mode** and tap **Create**.
4. When the database opens, tap the **Rules** tab at the top.
   - Delete everything in the box.
   - Open [`firestore.rules`](firestore.rules) in this project, copy all of it, and paste it into the box.
   - Tap **Publish**.
5. Go back to the project's home page (**Project Overview**, top left). Tap **+ Add app** and choose the **Web** icon, which looks like `</>`.
   - Nickname: `Sleep app`. Leave **Firebase Hosting** unticked. Tap **Register app**.
   - You'll see a box of code containing `const firebaseConfig = { apiKey: "...", ... };`. **Copy that `{ ... }` part.** You can ignore the rest.

### Part 2: Connect the app to it (once)

Either:

- **Easiest:** paste the `firebaseConfig` block to Claude and ask it to turn on sync. It will put it in the right place for you.

Or do it yourself on github.com:

1. Open [`sync-config.js`](sync-config.js) in this project and tap the **pencil** icon (Edit).
2. Replace `null` in the last line with the `{ ... }` block you copied. The last line should look like `window.SYNC_CONFIG = { apiKey: "...", ... };`.
3. Tap **Commit changes**.

These settings aren't secret, because every Firebase website includes them. The rules from step 4 and your family code are what keep the log private.

Wait a minute or two for the website to update. Then close the app on your phone completely and open it again.

### Part 3: Link the two phones

**On your phone:**
1. Open the app and tap the **round initial** (top right) → **Sync with partner** → **Start syncing**.
2. Tap **Send code to partner** and send it by WhatsApp, iMessage or email.

**On your partner's phone:**
1. Open the app link and **add it to the home screen** (see Step 3 at the top), then open it from the icon.
2. Tap the **round initial** → **Sync with partner** → **I have a code**.
3. Paste the code (pasting the whole message works too) and tap **Join**.

That's it. A **green dot** on the round initial means everything is synced. Sleeps and feeds that were already on either phone are kept and merged.

| Dot on the initial | Meaning |
|---|---|
| 🟢 Green | Synced and up to date |
| 🟠 Orange | Offline or connecting. Changes are saved and will sync later |
| 🔴 Red | Something's wrong with the setup. Check Part 1 step 4 (Rules) and Part 2 |

### Alternative if you'd rather keep the project private

Go to **[app.netlify.com/drop](https://app.netlify.com/drop)** on a computer. Download this project as a ZIP (green **Code** button → **Download ZIP**) and unzip it. Then drag the folder onto that page. You get a free link and can follow Step 3 with it.
