# Launch Playbook

Five tasks. Roughly 30 minutes end-to-end.

---

## 1. Wire the form (5 min)

The form currently logs to console. Pick one backend.

### Option A: Formspree (easiest)

1. Go to https://formspree.io and sign up
2. Create a new form named "Polish Waitlist"
3. Copy the endpoint URL (looks like `https://formspree.io/f/abc1234`)
4. In `index.html`, find `REPLACE_WITH_YOUR_FORM_ENDPOINT` and replace with that URL
5. Free tier: 50 submissions per month — fine for waitlist phase

### Option B: Tally (better dashboard, free unlimited)

1. https://tally.so → create form → embed code
2. Either replace the form action, or replace the entire `<form>` block with their embed iframe

### Option C: Custom

If you want submissions piped to your own DB or email, point the form at any endpoint that accepts a POST with `application/x-www-form-urlencoded`. The fields are `email`, `tool[]`, `frequency`, `willingness`.

---

## 2. Push to GitHub (5 min)

From inside the `polish-landing/` folder:

```bash
git init
git add .
git commit -m "initial: polish landing page"
git branch -M main
```

Then create the repo. Either via the `gh` CLI:

```bash
gh repo create polish-landing --public --source=. --push
```

Or manually: create an empty repo at https://github.com/new, then:

```bash
git remote add origin https://github.com/YOUR_USERNAME/polish-landing.git
git push -u origin main
```

---

## 3. Deploy (5 min)

### Recommended: Vercel

1. https://vercel.com → sign up with GitHub
2. "Add New" → "Project" → import the `polish-landing` repo
3. Framework preset: **Other** (it's static HTML, no config needed)
4. Click Deploy
5. You get a live URL like `polish-landing-yourname.vercel.app` in ~30 seconds

### Alternative: Cloudflare Pages

Faster CDN, similar process. https://pages.cloudflare.com

### Alternative: GitHub Pages

Free, but slower to update. In repo Settings → Pages → Source: `main` branch, root folder. URL becomes `yourname.github.io/polish-landing`.

---

## 4. Custom domain (optional, 10 min)

If you want a real domain:

1. Buy one — Namecheap, Porkbun, or Cloudflare Registrar ($10–15/yr)
   - Suggestions: `polish.tools`, `tryapolish.com`, `polishmeeting.com`
2. In Vercel: Project → Settings → Domains → Add → enter your domain
3. Vercel shows you DNS records — add them at your registrar
4. SSL provisions automatically in a few minutes

---

## 5. Distribute (ongoing)

The landing page is the easy part. The signal comes from getting eyes on it.

### Day 1 launch posts

**Reddit** (lead with the Zoom hallucination quote, link soft, title is the hook)
- r/sales — "Anyone else getting hallucinated commitments in their AI meeting summaries?"
- r/freelance — "Quick question for consultants who send meeting recaps to clients"
- r/consulting — "Building a tool to verify AI meeting notes — does this resonate?"
- r/projectmanagement — "How are you catching errors in your AI summary tools?"
- r/SaaS — same hook, different angle for the founder crowd
- r/indiehackers — Show & Tell post, transparent about the validation phase

**Twitter / X**
- Pin a thread: 1) the Zoom user's hallucinated quote, 2) the data (35% rate, 63% OKR failure), 3) what you're building, 4) link
- Reply to anyone tweeting frustration about Otter / Fathom / Granola accuracy

**LinkedIn**
- Longer prose version, target audience: agency owners, AEs, project managers, consultants
- Lead with the "this almost cost me a client" angle

**Hacker News**
- Hold off on Show HN until you have 10+ signups. Then post Tuesday or Thursday morning EST

### What NOT to do yet

- Don't ProductHunt-launch on a waitlist. Save it for v1.
- Don't pay for ads on a waitlist either. Spend $0 on validation.

---

## 6. Monitor

Keep a simple table of the four form fields so the signal is legible:

| Email | Tool(s) | Meetings/wk | $5 willingness |
|---|---|---|---|

Three thresholds to watch:

- **Strong:** 50+ signups, ≥40% "yes" on $5, top 3 notetakers cover ≥70% of users → ship the build
- **Mixed:** 20–50 signups, WTP 50/50 → email the top 5 most-engaged for 15-min calls before writing code
- **Weak:** <15 signups, mostly "no" / "depends" → reposition before building anything

---

## When validation hits, here's the build plan

Saturday:
- Fork your `labformat-agent` infrastructure
- Scaffold the prompt chain (cleanup pass → cross-check pass → audience-tune pass)
- Build the paste-in UI
- Wire the verify flag system

Sunday:
- Cross-check mode (the hallucination flagger)
- Follow-up email generator
- Stripe per-doc checkout
- Deploy to same domain

You already shipped a $7 SaaS once. This is the same architecture.
