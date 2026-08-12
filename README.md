# Keep Sage Alive

A tiny one-page website that gives Sage's sitters a single place to:

- see when Sage needs a sitter and which days people have blocked out (embedded Google Calendar)
- find her food details and delivery dates
- find pet insurance, vet, and microchip info

It's a plain static site hosted free on GitHub Pages. No build tools, no framework, one HTML file.

---

## How it works (the honest version)

- **Viewing** everything happens on this site: calendar + food + insurance in one place.
- **Adding dates** happens in the shared Google Calendar, not on the site. A GitHub Pages site is static, so it can *show* the calendar but can't *edit* it. Your mates add their unavailable days in Google Calendar (where you've given them edit access), and those days appear on the site automatically because it's the same calendar.

So: one shared source of truth, viewable in one spot. That's the trade-off of the free/no-backend approach.

---

## Setup, step by step

### 1. Create the repo
1. Make a new GitHub repository (public), e.g. `keep-sage-alive`.
2. Upload `index.html` (and this README) to it, or push this folder.

### 2. Turn on GitHub Pages
1. In the repo: **Settings > Pages**.
2. Under **Build and deployment > Source**, pick **Deploy from a branch**.
3. Branch: `main`, folder: `/ (root)`. Save.
4. Wait ~1 minute. Your site is live at `https://YOUR-USERNAME.github.io/keep-sage-alive/`.

### 3. Make the shared calendar
1. In Google Calendar (on desktop), create a **new calendar** just for Sage (don't use your personal one). Left sidebar > **Other calendars > +** > **Create new calendar**.
2. Share it with your mates: open that calendar's **Settings > Share with specific people** > add their Google account emails > permission **"Make changes to events"**.
3. Agree on a title convention so entries are readable, e.g. `Dan — can't sit`.

### 4. Embed the calendar into the site
1. Still in that calendar's **Settings**, scroll to **Integrate calendar**.
2. Copy the **Embed code** (the whole `<iframe ...></iframe>`).
3. In `index.html`, find the block that says `PASTE YOUR GOOGLE CALENDAR EMBED CODE HERE` and replace the `<div class="cal-placeholder">...</div>` with your iframe.
4. Optional: add `&mode=MONTH` or `&mode=AGENDA` to the iframe `src` to control the default view.

### 5. Add the "open the calendar" link
1. Get a link your mates can tap to add events. In the calendar Settings under **Integrate calendar** there's a **Public URL** / you can share the calendar link from the three-dot menu in the sidebar.
2. In `index.html`, find `id="cal-link"` and put that URL in the `href`.

### 6. Fill in the details
Open `index.html` and replace every `— add ...` placeholder with the real info: food amounts, delivery dates, vet number, and so on.

### 7. Push and you're done
Commit the changes. GitHub Pages redeploys automatically in a minute. Send your mates the one link.

---

## Privacy note

GitHub Pages sites are **public** to anyone with the link. Don't put anything here you wouldn't want a stranger to read. If you're not comfortable posting the full insurance policy number or microchip number, write "ask Duncan" in those fields and keep the real numbers somewhere private (a note in the shared calendar description, a text, etc.).

---

## Editing later

Everything lives in `index.html`. Edit it directly on GitHub (pencil icon) or locally and push. No rebuild step beyond GitHub Pages' automatic deploy.
