# Polish

A verification layer for AI meeting notes. Cross-checks summaries from Otter, Fathom, Granola, Zoom, Teams, or any other AI notetaker against your transcript and flags hallucinations before you hit send.

This repo is the waitlist landing page.

## What's here

- `index.html` — the entire landing page (single-file, no build step)
- `LAUNCH.md` — step-by-step deployment + distribution playbook
- `.gitignore` — standard ignores

## Stack

- Vanilla HTML / CSS / JS
- IBM Plex Sans + IBM Plex Mono via Google Fonts CDN
- No frameworks, no build, no dependencies

## Local preview

Open `index.html` directly in your browser, or:

```bash
python3 -m http.server 8000
# visit http://localhost:8000
```

## Before deploying

Two placeholders in `index.html` that need replacing:

1. `REPLACE_WITH_YOUR_FORM_ENDPOINT` — wire to a Formspree or Tally endpoint (5 min, see `LAUNCH.md`)
2. `@mike` in the footer — swap for your handle if different

## Validation thresholds

Decision rules for the waitlist signal:

- **50+ signups in 2 weeks, ≥40% answer "yes" to $5/check** → ship the build
- **20–50 signups, WTP split 50/50** → talk to top 5 engaged signups before committing
- **<15 signups, mostly "no" or "depends"** → reposition before writing a line of code

## Pricing

- Free: unlimited basic cleanup + 1 verification check / month
- Per check: $5 per verified report, no signup
- Pro: $11 / month for unlimited

## License

Personal project. Code is yours to learn from. Brand and copy are not.
