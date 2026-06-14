# 🇸🇪➜🇬🇧 Road to London — Summer Challenge Game

A mobile-friendly game for the kids (age 9 & 12) to do challenges over **sommarlov 2026**
and collect stars on the way to our **London trip during höstlov (vecka 44, 26–30 Oct 2026)**.

The game is in **English** so they practise the language, with **Swedish hints** (🇸🇪) on every
challenge for help when they get stuck.

## ▶️ How to play

It's a single file — **`index.html`**. No internet, no install, no account needed.

1. Open `index.html` in any web browser (works great on a phone).
2. **To get it on a kid's phone:** email/AirDrop/message the file to the phone and open it,
   or host it (see below). Then tap the browser's **"Add to Home Screen"** — it opens
   full-screen like a real app.
3. Pick a player, do quests, earn ⭐, and travel from Sweden to London!

> All progress is saved **on that device** in the browser's local storage. Each phone keeps
> its own progress, so ideally each kid plays on their own device (the game still has two
> player profiles either way).

## 🎮 What's in the game

- **Two player profiles** (names & emoji avatars set by parents).
- **Quests** in 6 categories: Reading & Learning 📚, Active & Outdoors 🏃, Helping at Home 🏠,
  Creative 🎨, Kindness 💛, English & London 🇬🇧.
  - **Daily** quests reset every morning, **Weekly** quests reset each week, and **Big quests**
    are one-time goals worth lots of stars.
  - Each quest has a **"Need help?"** button that reveals a Swedish hint.
- **Stars ⭐** are the score → they fill up **Levels** with fun rank titles.
- **Journey map** from home in Sweden all the way to London landmarks (Big Ben, London Eye,
  Tower Bridge, Buckingham Palace…). New stops unlock as stars add up.
- **Day streaks 🔥** to reward playing every day.
- **Badges 🏅** for milestones.
- **London facts** unlock as you travel.
- **Countdown** to the London trip.
- Confetti + a little sound on every completed quest. 🎉

## 🔒 Parents' Zone (password protected)

Tap **Parents** in the bottom bar and enter the password. There you can:

- Change the **trip date** for the countdown.
- Turn **sound** on/off.
- Edit each **player's name and avatar**.
- **Change the password.**
- **Reset** one player's progress or everything (requires re-entering the password — it can't be undone).

**Default password:** `london2026` — change it in the Parents' Zone right away.

## 🌐 Optional: host it online

So the kids can open a link instead of a file, you can host it for free with GitHub Pages:
push this repo, then enable **Settings → Pages → Deploy from branch** and pick the branch.
The game will be at `https://<user>.github.io/<repo>/`.

## ✏️ Customising the challenges

All challenges live in the `CHALLENGES` array near the top of the `<script>` in `index.html`.
Each one has English text (`en`), a Swedish hint (`sv`), a star value, a category, and a type
(`daily` / `weekly` / `once`). Add or edit freely.
