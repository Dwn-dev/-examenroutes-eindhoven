# CBR Eindhoven — Examenroutes trainer

A free, single-file web app for practising the driving-exam terrain around **CBR Eindhoven (Hoevenweg 20)**: eight reconstructed practice loops with one-tap **Open in Google Maps** links, known hazard spots, the car questions (binnen & buiten), all 8 bijzondere verrichtingen with local location patterns, a 15-question self-test, a roadworks snapshot, and saved progress (routes driven, notes, checklist, best quiz score).

**Live demo:** enable GitHub Pages on this repo (see below) and your site is at `https://<your-username>.github.io/<repo-name>/`

---

## ⚠️ Disclaimer

Unofficial study tool — **not affiliated with or endorsed by the CBR.** The CBR does not publish exam routes and examiners compose the ride on the day; these loops reconstruct the *terrain* documented by driving schools and route-video platforms. Roadworks data is a dated snapshot: the yellow signs on the road always win. Speed limits on the signs always beat anything in this app.

## Features

- **8 routes** covering the documented exam areas (Zeelst, Meerhoven, Gestel, Veldhoven, Aalst, Afrit 29, Oerle, Blaarthem), each with turn-by-turn steps, hazard notes and a Google Maps deep link that pins the waypoints
- **Car questions** — 16 tap-to-reveal Q&A cards for the voertuigcontrole (outside / under the bonnet / inside)
- **Bijzondere verrichtingen** — the 3-assignment system explained, all 8 techniques, and where each tends to happen around this exam centre
- **Self-test** — 15 scenario questions with explanations; best score saved
- **Plan** — countdown-driven training phases + least-practised-route coaching
- **Roadworks snapshot** — dated, with live links (gemeente Eindhoven, Veldhoven, Vananaarbeter, Rijkswaterstaat)
- **No build, no dependencies** — one `index.html`, works offline once loaded

## Run it locally

Open `index.html` in a browser. That's it.

## Publish on GitHub Pages

1. Create an empty repo on GitHub (e.g. `cbr-examenroutes-eindhoven`). Don't add a README — this folder already has one.
2. From this folder:

   ```bash
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```

   (The repo is already initialised with an initial commit.)
3. On GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch → Branch: `main` / `(root)` → Save.**
4. After a minute your site is live at `https://<your-username>.github.io/<repo-name>/`.

No-terminal alternative: create the repo on github.com → **uploading an existing file** → drag everything in this folder → commit → enable Pages as in step 3.

## How progress saving works

The app detects its environment: on the open web it uses `localStorage` (per browser/device), inside a Claude artifact it uses the artifact storage API, and if neither is available it falls back to in-memory (resets on reload). No accounts, no server, no data leaves the device.

## Maintaining it

- **Routes** live in the `ROUTES` array in `index.html` — copy an existing object to add route 9. `id` must stay stable (progress is keyed on it); `waypoints` are plain "street, city" strings that Google Maps geocodes.
- **Roadworks**: update the snapshot list in the yellow card and change the `Snapshot:` date whenever you refresh it.
- **Checklist**: append new items at the end only — saved ticks are keyed by index.
- **Exam date**: the countdown and plan use `new Date(2026,7,27)` (month is 0-based). Change both occurrences for a new date.

## Adapting for another CBR location

Change `CBR` (start/finish address), rewrite `ROUTES` for that city's documented terrain, and redo the hotspots/roadworks sections. The rest is location-independent.

## License

MIT — see `LICENSE`.
