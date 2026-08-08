# CBR Eindhoven — Examenroutes trainer

A free, single-file web app for practising around **CBR Eindhoven (Hoevenweg 20)**. It contains **11 unofficial practice routes**, Google Maps links, video timelines, observation notes, car questions, special-manoeuvre practice, a 15-question self-test, live roadworks sources and locally saved progress.

**Live site:** https://dwn-dev.github.io/-examenroutes-eindhoven/

## Disclaimer

This is an unofficial study tool and is **not affiliated with or endorsed by the CBR**. The CBR does not publish fixed exam routes. The cards combine:

- Broad waypoint-based practice loops
- Two publisher animations
- Two full-video reconstructions from Verkeersschool Weber
- One instructor-reported NH Geldrop navigation scenario

None is a guaranteed CBR route. Google Maps can recalculate between waypoints, and several residential turns in the videos remain approximate. Current signs, markings, traffic lights, road layouts, construction and speed limits always take precedence over this app, an old video or navigation.

## Features

- **11 routes** with stable IDs, ordered instructions, risk notes and Google Maps links
- **Two full Weber video routes** with source metadata, confidence labels, embedded playback, segmented Maps links and timestamp timelines
- **Two short publisher animations** using canonical `youtube.com/watch?v=` URLs and reconstruction/confidence labels
- **Car questions** — tap-to-reveal cards for vehicle checks
- **Special manoeuvres** — the official requirement is separated from a broader eight-technique practice toolbox
- **Self-test** — 15 scenarios with explanations; the best score is saved
- **Dynamic training plan** — one exam-date setting drives the countdown and all displayed dates
- **Roadworks guidance** — live official sources instead of unverified dated closure claims
- **No build or dependencies** — one `index.html`

## Route IDs and saved progress

Progress and notes are keyed by route `id` in the central `ROUTES` array. Existing IDs must never be renamed or reused, even when a route title changes or a new route is inserted.

The 2023 Weber route deliberately keeps its existing `stratum` ID, while the added 2022 route uses `weber-2022-waalre`. This prevents existing driven counts and notes from being reassigned.

Checklist ticks are keyed by array index, so append new checklist items instead of reordering existing ones.

## Factual basis

- CBR practical-exam overview: https://www.cbr.nl/nl/rijbewijs-halen/auto/praktijkexamen-auto/hoe-gaat-het-praktijkexamen-auto
- CBR Rijprocedure B: https://www.cbr.nl/nl/service/nl/artikel/rijprocedure-b-printversie
- CBR tussentijdse toets: https://www.cbr.nl/nl/rijbewijs-halen/auto/praktijkexamen-auto/tussentijdse-toets-doen
- CBR Eindhoven location: https://www.cbr.nl/nl/service/nl/route-locaties/tonen-op-cbr-locaties/examencentrum-eindhoven-3
- Rijksoverheid motorway speed limits: https://www.rijksoverheid.nl/vraag-en-antwoord/verkeersveiligheid/wat-is-de-maximumsnelheid-voor-auto-s-op-de-snelweg

The complete exam is approximately 55 minutes and the drive approximately 35 minutes. The current Rijprocedure B says two special manoeuvres are tested, at least one involving reversing. A valid tussentijdse-toets exemption applies to the first subsequent practical exam, subject to current CBR conditions.

## Run locally

Open `index.html` in a browser, or serve the folder with any static HTTP server.

## Publish with GitHub Pages

In the repository settings, choose **Pages → Deploy from a branch → `main` / root**. GitHub Pages will publish the current `main` branch.

## How progress saving works

On the public web the app uses `localStorage` per browser and device. Inside a Claude artifact it can use the artifact storage API. If neither is available, it falls back to in-memory state that resets on reload. No account is required and no saved progress leaves the device.

## Maintaining the app

- **Routes:** edit the central `ROUTES` array. Keep all existing `id` values stable.
- **Route totals:** do not hardcode them. The UI derives the count from `ROUTES.length`.
- **Exam date:** change `EXAM_DATE` once, using `YYYY-MM-DD`. All date text uses `Europe/Amsterdam`.
- **Video evidence:** keep publication metadata, timestamps and confidence wording with each video route. Do not promote approximate residential turns to exact street instructions without visual proof.
- **Roadworks:** review the linked Eindhoven, Veldhoven, Van A naar Beter and Rijkswaterstaat sources. Update the last-reviewed date, but do not add a closure unless a current official source confirms it.
- **External links:** retain `target="_blank"` with `rel="noopener noreferrer"`.
- **Checklist:** append items rather than reordering them, because saved ticks are index-based.

## License

MIT — see `LICENSE`.
