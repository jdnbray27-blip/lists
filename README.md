# Lists — shared checklists

A single-file HTML app: pre-fab list templates (grocery, packing, chores, etc.),
your own custom lists as tabs, checkable items, and optional **live sharing**
with other people via a free Firebase backend.

## Run it locally right now
Just double-click `index.html` (or open it in a browser). It works immediately
in **solo/local mode** — your lists save to that browser only (localStorage).

## Host it on GitHub Pages (so others can open it)
1. Create a new GitHub repo (e.g. `my-lists`).
2. Add `index.html` (and this README) to the repo, commit, push.
3. Repo → **Settings → Pages** → Source: `main` branch, `/ (root)` → Save.
4. Your app is live at `https://<your-username>.github.io/my-lists/`.

That alone gives everyone a copy of the app, but each person's changes stay
in their own browser (no sharing yet) — do step below for real collaboration.

## Enable live multi-user sharing (free, ~5 minutes)
GitHub Pages only serves static files, so to actually sync data between
people you need a tiny free database. Firebase Firestore is the simplest fit:

1. Go to <https://console.firebase.google.com> → **Add project** (free, no card needed).
2. In the project: **Build → Firestore Database → Create database → Start in test mode**.
3. **Project settings** (gear icon, top left) → scroll to **Your apps** → click the
   `</>` (Web) icon → register an app (any nickname) → copy the `firebaseConfig`
   object it shows you.
4. Open `index.html`, find the `firebaseConfig` object near the top of the
   `<script>` section, and paste your values in place of the placeholders.
5. Commit and push. GitHub Pages auto-updates in ~1 minute.

Now: anyone who opens your page URL with the **same `?room=` code** in the
address bar sees the same lists, live, as they're edited. Use the
**"Copy share link"** button in the header to send someone a link that
already has the room code baked in — they just open it and it's the same board.

### Notes on Firestore "test mode"
Test mode makes the database open to anyone who has your config (fine for a
small shared tool among friends/colleagues, not for sensitive data). Test mode
rules expire after 30 days — if sync stops working after a month, go back to
Firestore → Rules and extend/open them again, or write permanent rules if you
want this long-term.

## What you get
- Multiple **tabs**, each its own list.
- **"+ New list"** button → pick a pre-fab template (grocery, packing,
  to-do, chores, movie watchlist, books, project tasks, gift ideas) or start blank.
- Add/edit/check off/delete items inline.
- Progress bar + done count per list.
- Rename a list by clicking its title.
- Delete a list via the ✕ on its tab.
- Share link with a room code; everyone on that room/URL sees the same data
  update live (once Firebase is configured).
