# 🇸🇪➜🇬🇧 Nord Challenges — Summer Challenge Game

A light, mobile-friendly game for **August (12)** and **Lykke (9)** to do challenges over
**sommarlov 2026** and collect stars that power the family's journey to our **London trip,
25–28 Oct 2026**.

The game is in **English** so they practise the language, with **Swedish hints** (🇸🇪) on every
challenge for help when they get stuck.

## ▶️ Play online

**https://nordsimon.github.io/sommarlov-2026/**

Open it on each kid's phone and tap **Share → Add to Home Screen** for a full-screen, app-like
experience. Progress is saved **on each phone** in the browser.

## 👧🧒 One phone each + shared journey

Each kid plays on their **own phone**:

1. First launch asks for their **name** and to **pick a character emoji**.
2. The app then asks for an **unlock password** (default **`london`**) **once** — the kids get it by
   doing a physical intro challenge. After that it stays unlocked on that device.
3. They complete quests and earn ⭐ on their own phone.
4. The **journey to London is powered by the combined family total** — both kids' stars added together.
   Every level shows the **points needed**, but the destination name stays hidden until unlocked (a
   surprise). Unlocked London sights get a **"Läs mer"** link to Swedish Wikipedia.

There's an **↻ update button at the top** of every screen so the kids can refetch the latest version
themselves, and switching tabs scrolls back to the top.

### Points
Easy quests still pay (10⭐), but harder ones pay much more — weekly quests 25–55⭐ and one-time
**big quests up to 150⭐**. Daily quests are capped at 10 completions each, so the top levels can't be
farmed quickly: reaching the 9000⭐ top takes steady effort across the summer and lands near the trip.

### 🔗 Syncing their points

**Easiest: QR code.** On the **Sync** tab each phone shows a **QR code**, and there's a **📷 Scan QR code**
button to scan the sibling's QR **inside the app** (this is the reliable way when the app is on the Home
Screen, since a phone-camera scan would open the browser, not the installed app). Points combine
automatically. (QR image generation + the scanner library load from an online service, so they need
internet; Copy/Share/paste the text code still works offline.)

Because they're on separate phones, points are combined with a simple **sync code**:

- On the **Sync** tab each phone shows its own `LDN-…` code.
- Tap **Copy** or **Share** and send it to the sibling (e.g. by message).
- The sibling pastes it under **"Paste … code here"** and taps **Sync points**.
- The family total and the London journey now reflect both kids. Re-share after a big session to keep it current.

> The code only carries points/level (no photos), so it's short enough to text.

### 💾 Moving to another device
To move a kid's whole account (points, completed quests **and** photos) to a new phone, use
**Parents' Zone → Send / save full backup**. On a phone this opens the share sheet, so you can
**AirDrop (iOS) / Quick Share · Nearby Share (Android) / Bluetooth / Messages** the backup straight
to the other device; then open the app there and tap **Restore from backup**. (On desktop it
downloads a `.json` file instead.) This is different from the points code above, which only
combines siblings' totals.

## 💽 Storage & data safety

- **Proof photos are stored in IndexedDB**, not localStorage — localStorage is small (~5 MB per
  origin) and slow for images, while IndexedDB holds far more and is written per-photo. Photos are
  also shrunk to ~640 px JPEG, and only the newest 60 are kept.
- The app calls `navigator.storage.persist()` to ask the browser to **protect the data from
  eviction**. Parents' Zone shows current usage and whether storage is protected.
- **iOS note:** Safari can clear a website's data after about **7 days of not opening it**. Two
  defences: **Add to Home Screen** (installed web apps are exempt), and **make a backup now and
  then** with the button above. The app has no server, so backups are the only off-device copy.

## 📸 Proof photos

Completing a quest requires **evidence**: the kid takes or chooses a **photo**, which is compressed
and saved on their phone. Parents can browse every proof photo in the **Parents' Zone → Proof gallery**
(tap any photo to enlarge, or delete it). Photos never leave the device.

## 🎮 What's in the game

- **Quests** in 9 categories: Reading & Learning 📚, Active & Outdoors 🏃, Elton the Dog 🐶,
  Cooking & Baking 🍳, Helping at Home 🏠, Gothenburg 🚋 (local outings), Creative 🎨,
  Kindness 💛, English & London 🇬🇧.
  - **👪 Parent quests:** activities that need a grown-up (using the stove/oven, paid outings like
    Liseberg or Universeum, boat tours) are marked **👪 Parent** and require the **parents password**
    to complete, so a grown-up approves them. No swimming or water/dangerous activities are included.
  - **Daily** quests can be done once per day, up to **10 times** each over the summer (an `x/10`
    counter shows progress). **Weekly** quests reset each week, and **Big quests** are one-time
    goals worth lots of stars.
  - Each quest has a **"Need help?"** button with a Swedish hint.
- **Stars ⭐** → **Levels & rank titles** (Rookie Traveller → … → London Legend).
- **Combined journey map** from Sweden to London landmarks (Big Ben, London Eye, Tower Bridge,
  Buckingham Palace, museums, Hyde Park, Harry Potter Studios…) unlocking as the family total grows.
- **Day streaks 🔥**, **collectible badges 🏅** (press &amp; hold a badge for the Swedish version), and
  **London facts** that unlock along the way. A floating **?** button explains the controls.
- A **"Where we're going"** card on Home with a Swedish **Läs mer** link about London.
- **Local Gothenburg quests** focus on the neighbourhood (Kungssten/Majorna/Älvsborg) — playgrounds,
  Slottsskogen, Änggårdsbergen, historic spots — not far-away tourist trips.
- Reading is recurring: **log up to 10 books** (Swedish and English) plus **write book reviews**.
- **Countdown** to the trip (25–28 Oct 2026).
- Confetti + a gentle sound on every completed quest. 🎉

## 🔒 Parents' Zone (password protected)

The Parents' Zone is a normal in-page screen (no pop-ups). Tap **Parents** in the bottom bar and enter
the password to:

- View the **proof photo gallery**, and **undo an activity** if the evidence is too weak — it removes
  the photo, takes back the points, re-checks badges, and lets the kid do the quest again.
- **Unlock all stops (preview)** to verify the "Läs mer" links, and **Update app** to refetch the latest version.
- Change the **app unlock password** (default `london`).
- Change the **trip dates** and toggle **sound**.
- Change **which kid** this phone belongs to and the **character emoji**.
- **Change the password.**
- **Reset** this kid's progress or clear synced sibling data (requires re-entering the password).

**Default password:** `london2026` — change it in the Parents' Zone right away (the site is public,
so the default is visible in the source).

## ✏️ Updating content after release (safe for progress)

Game **content** — categories (`CATS`), challenges (`CHALLENGES`), the journey/levels (`JOURNEY`),
badges (`BADGES`) and facts (`FACTS`) — all live at the top of the `<script>` in `index.html`.
Edit them and push to `main`; the live site redeploys and every phone loads the new content on next
open. Because there is **no service worker**, this works even after "Add to Home Screen".

Player **progress** is stored separately in the browser and is never wiped by a content update.
Permanent data: **total points**, **completed challenges (+ their proof photos)**, and
**multi-completion progress** (the `x/10` counters). Progress is keyed by each challenge's `id`, so:

- **Adding** a challenge → it starts fresh at 0 for everyone.
- **Editing** a challenge (text, stars, icon, `max`, category) → keep its `id` and existing progress
  is preserved.
- **Never reuse an `id`** for a different challenge, or its old progress would carry over.

`load()` merges saved progress onto fresh defaults, so new fields added in future releases won't
break existing players.
