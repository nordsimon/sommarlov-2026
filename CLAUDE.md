# CLAUDE.md — Nord Challenges

Project guidance for future Claude Code sessions. Read this first.

## What this is
A kids' summer-challenge web game ("Nord Challenges") for two siblings, **August (12)** and
**Lykke (9)**, in Gothenburg. They complete quests to earn ⭐ stars that power a shared family
"journey to London" (the family trip is **25–28 Oct 2026**). English game text with **Swedish hints**
so they practise English but get help. Built as a single static page, deployed on GitHub Pages.

- **Live site:** https://nordsimon.github.io/sommarlov-2026/
- **Repo:** `nordsimon/sommarlov-2026`, default branch **`main`** — work directly on `main`.
- Pages auto-deploys on push to `main` via the built-in "pages build and deployment" (source =
  Deploy from a branch, `main` / root). **No custom workflow** — an earlier auto-enable workflow was
  removed because the Actions token couldn't create the Pages site. Pages was enabled manually once.

## Architecture (deliberate choices)
- **Single self-contained file: `index.html`** (HTML + CSS + vanilla JS, no build step, no framework).
  This is intentional: easy to AirDrop/open anywhere, works offline-ish, trivial to deploy on Pages.
  **The user explicitly declined a React/refactor.** Do NOT introduce a framework or a build pipeline.
  If it must grow, the only sanctioned step is a light split into `data.js` + `app.js` (still no build) —
  and only if asked.
- Other files: `manifest.json` (PWA, standalone), `icon-512.png` (home-screen icon, 1254² PNG),
  `README.md`. There is **no service worker** (so updates always apply, even after Add to Home Screen).
- Verify changes by extracting the `<script>` and running it through Node with DOM stubs (parse check)
  plus small logic tests. Pattern used throughout: `new Function(js + ";return {…};")()` with stubbed
  `document/localStorage/navigator/window/location`. Always parse-check before committing.

## Content vs progress (critical)
- **CONTENT** lives in consts at the top of the script and is re-read each load (updates ship via push):
  `CATS`, `CHALLENGES`, `JOURNEY`, `RANKS`, `BADGES`, `FACTS`.
- **PROGRESS** lives in `localStorage` (`state`, key `roadToLondon_v2`) and must survive content updates.
  `load()` merges saved state onto `defaultState()` so new fields don't wipe players.
  Permanent, never recomputed: `me.stars` (running total), `me.done` (completion keys), `me.evidence`
  (proof photos), multi-completion counts (derived from `me.done`).
- **Challenge `id`s are stable keys.** Adding a challenge → starts at 0. Editing keeps progress.
  **Never reuse an id** for a different challenge.

## Data model
- One player per device: `state.me = {id, name, avatar, stars, totalDone, catCount, done{}, streak,
  bestStreak, lastActive, badges[], evidence[]}`. `id` is a generated `u_xxxx` (free-text names).
- `state.partner` = a lightweight synced snapshot of the sibling (points only). The journey uses the
  **combined** stars (`me.stars + partner.st`).
- Quest types: `daily` (once/day), `weekly` (once/week), `once` (one-time). Optional `max` caps total
  completions (daily quests default to `max:10`; `maxCount()`/`timesDone()`/`isMaxed()`).
- Optional `needsParent:true` exists (gates completion behind the parents password) but **currently no
  quest uses it** (kitchen + local outings were un-gated per request).

## Photos / storage limits
- Proof photos are stored in **IndexedDB** (`roadToLondon`/`photos`), NOT localStorage (which is ~5 MB
  per origin and slow). localStorage only keeps small metadata + the IndexedDB key. Falls back to inline
  base64 if IndexedDB is unavailable. `migratePhotos()` moves any old inline photos into IndexedDB.
- Photos are downscaled to ~640px JPEG q0.5; keep newest `EVIDENCE_CAP = 60`.
- `requestPersist()` calls `navigator.storage.persist()` to resist eviction. Parents' Zone shows usage.
- iOS caveat (documented for the user): non-installed Safari can evict storage after ~7 days → mitigations
  are Add to Home Screen + the backup/export feature.

## Passwords
- **App unlock:** default `london`, stored in `state.appPassword`. One-time per device
  (`state.appUnlocked` persists). Case-insensitive. Lock screen uses a large per-character "PIN box"
  indicator that fills as you type; auto-submits when full.
- **Parents' password:** default `london2026`, `state.password`. Gates the Parents' Zone, resets,
  full backup, and (if ever used) parent-gated quests.
- Both are public in source since the site is public — fine for this use case.

## Syncing (combine the two kids' points)
- **QR only** (manual text code was removed). Each phone shows a QR (generated via api.qrserver.com
  image — needs internet) encoding a `?sync=…` deep link. The other phone uses the **in-app camera
  scanner** (Sync tab → "Scan QR code"). In-app scanning is required because a phone-camera scan opens
  Safari, which has separate storage from the installed home-screen app.
- Scanner: `BarcodeDetector` when available (Android), else lazy-loads `jsQR` from CDN (iOS). `?sync=`
  deep links opened in-browser are auto-applied via `applyPendingSync()` (kept as a fallback path).
- **Full device migration** (incl. photos) = Parents' Zone → "Send / save full backup" (uses the OS
  share sheet: AirDrop / Nearby Share / Bluetooth) and "Restore from backup".

## UX conventions / decisions made
- **Light, airy theme** (off the original dark navy). Keep it minimal; the user asked to reduce emojis —
  keep only meaningful ones (quest icons, journey landmark icons, nav glyphs, ⭐ currency, avatars).
  Use the `ico()` helper to add spacing between an emoji and following text.
- **Swedish hints** go through the single `sv()` helper → compact line with a small "SV" label
  (no flag emoji).
- **Journey/levels:** show ALL stops with the points needed, but **hide the destination name until
  unlocked** ("Level N" + stars while locked; emoji + name + Swedish + a **"Läs mer"** link to
  **Swedish** Wikipedia once unlocked — English links were rejected as too hard). Powered by combined stars,
  tops out at 9000 ("London Legends").
- **Completing a quest must NOT reorder the list** (stable, defined order). Category switching updates
  only the quest list (`#qlist`, partial re-render) to preserve scroll. Scroll-to-top only on tab change.
- **Parents' Zone is in-page screens, NOT modals** (modals scrolled badly). The only remaining modal is
  the quest photo-capture flow and the QR scanner.
- **Proof on completion:** completing a quest requires a photo; parents browse them in the gallery and
  can **Undo an activity** (weak evidence) → refunds points, frees the slot, re-checks badges.
- Top bar has an **↻ update** button (cache-busting reload) so kids can update themselves.
- Badges: **press & hold** shows the Swedish translation (`svNm`/`svDs`).
- The floating "?" help button was added then **removed** at user request.

## Point design
- Tuned for two kids over ~19 weeks (15 Jun → 25 Oct), combined target 9000.
- Easy quests 10⭐ (incl. badminton/gymnastics/trampoline — kept low on request), standard 15, outdoor
  boosted (bike/play-out 25, forest hike 45, berries 40, Elton walk 25, long forest walk 50, Elton
  practice 20), weekly 25–55, one-time big quests up to 150. Daily cap (10×) keeps the top a steady-effort
  goal that lands near the trip.
- Reading: "finish a book" is recurring up to 10 (Swedish 70⭐, English 100⭐) + write a book review.

## Local (Gothenburg) quests
- Keep them **local and walkable around Kungssten/Majorna/Älvsborg**, not far tourist trips (user
  removed Liseberg/Universeum/Paddan/Maritiman/Slottsskogen/Änggårdsbergen). Examples kept: Engelska
  Skolan schoolyard, find a historic place nearby, playground, Kungsladugård/Gathenhielmska old houses,
  local library, Röda Sten.

## Git / workflow
- Commit + push to `main` only when changes are complete (user has been pushing each change live).
- Commit message footer convention used in this repo:
  `Co-Authored-By` is NOT used here; messages end with a `https://claude.ai/code/session_…` line.
- Do NOT open PRs unless asked. Do NOT put model identifiers in committed artifacts.

## Pet / family facts
- Dog is **Elton** (loves training and forest walks). No swimming/water or dangerous activities.
