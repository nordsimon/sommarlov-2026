# 🇸🇪➜🇬🇧 Road to London — Summer Challenge Game

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

1. First launch asks **"Who are you?"** → pick **August** or **Lykke**, then **choose a character emoji**.
2. They complete quests and earn ⭐ on their own phone.
3. The **journey to London is powered by the combined family total** — both kids' stars added together.

### 🔗 Syncing their points
Because they're on separate phones, points are combined with a simple **sync code**:

- On the **Sync** tab each phone shows its own `LDN-…` code.
- Tap **Copy** or **Share** and send it to the sibling (e.g. by message).
- The sibling pastes it under **"Paste … code here"** and taps **Sync points**.
- The family total and the London journey now reflect both kids. Re-share after a big session to keep it current.

> The code only carries points/level (no photos), so it's short enough to text.

## 📸 Proof photos

Completing a quest requires **evidence**: the kid takes or chooses a **photo**, which is compressed
and saved on their phone. Parents can browse every proof photo in the **Parents' Zone → Proof gallery**
(tap any photo to enlarge, or delete it). Photos never leave the device.

## 🎮 What's in the game

- **Quests** in 6 categories: Reading & Learning 📚, Active & Outdoors 🏃, Helping at Home 🏠,
  Creative 🎨, Kindness 💛, English & London 🇬🇧.
  - **Daily** quests can be done once per day, up to **10 times** each over the summer (an `x/10`
    counter shows progress). **Weekly** quests reset each week, and **Big quests** are one-time
    goals worth lots of stars.
  - Each quest has a **"Need help?"** button with a Swedish hint.
- **Stars ⭐** → **Levels & rank titles** (Rookie Traveller → … → London Legend).
- **Combined journey map** from Sweden to London landmarks (Big Ben, London Eye, Tower Bridge,
  Buckingham Palace, museums, Hyde Park, Harry Potter Studios…) unlocking as the family total grows.
- **Day streaks 🔥**, **collectible badges 🏅**, and **London facts** that unlock along the way.
- **Countdown** to the trip (25–28 Oct 2026).
- Confetti + a gentle sound on every completed quest. 🎉

## 🔒 Parents' Zone (password protected)

Tap **Parents** in the bottom bar and enter the password to:

- View the **proof photo gallery**.
- Change the **trip dates** and toggle **sound**.
- Change **which kid** this phone belongs to and the **character emoji**.
- **Change the password.**
- **Reset** this kid's progress or clear synced sibling data (requires re-entering the password).

**Default password:** `london2026` — change it in the Parents' Zone right away (the site is public,
so the default is visible in the source).

## ✏️ Customising the challenges

All challenges live in the `CHALLENGES` array near the top of the `<script>` in `index.html`.
Each has English text (`en`), a Swedish hint (`sv`), a star value, a category, and a type
(`daily` / `weekly` / `once`). Add or edit freely — pushes to `main` auto-deploy to the live site.
