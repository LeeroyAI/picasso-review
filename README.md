# PICASSO

**The next iteration of AI Momentum.** A single-page concept asset, published for reaction.

🔗 **Live:** https://leeroyai.github.io/picasso-review/

PICASSO is not a new framework. It is what AI Momentum learnt. The proven phases hold. We have expanded them to build the capability, governance, operating model and behaviours needed to sustain AI across the enterprise, plus an AIM Hub that turns all of it into repeatable delivery.

This repo hosts the interactive asset and collects structured feedback on it.

---

## What the asset covers

PICASSO reads as one word across three levels.

| Level | Elements | Role |
|-------|----------|------|
| **Five phases** | Pulse, Ignite, Accelerate, Scale + Operate, Orchestrate | Move through in sequence |
| **Two threads** | Change (the human thread), Sherpa (the delivery thread) | Run through every phase |
| **One canvas** | Governance | Sits beneath all of it |

Behind the phases sits the **AIM Hub**, the backplane that turns discovery signal into cohort allocation, delivery agendas and reusable assets.

The page also carries the operating position: the shift from AI curiosity to agentic orchestration, and the sales and delivery paradigm that shift demands.

---

## How feedback works

The page has a built-in feedback widget. No email. No rekeying.

1. A reviewer taps **Share feedback** and answers a few structured prompts: who they are, an overall rating, what landed, and an optional note.
2. On submit, the page posts to a Google Apps Script web app.
3. The script appends one row to a private Google Sheet.

Reviews collate live in the Sheet. Six columns: Submitted, Reviewer, Rating, What landed, Note, Page. Sort and filter like any sheet.

The Sheet is private to the owner. Only the append endpoint is public, and it cannot read the Sheet back.

---

## Repo structure

```
index.html                   The published asset. Self-contained. No build step.
README.md                    This file.
archive/change-thread.html   The 12 Aug change thread exploration, kept for reference.
assets/PICASSO-concept.pdf   The concept PDF export.
_source/                     Local working material. Git ignored, never published.
```

Everything lives in `index.html`: markup, styles, and vanilla JavaScript in one file. HTML, CSS and JS are inlined. No frameworks, no dependencies, no compile.

---

## Updating the page

1. Edit `index.html`.
2. Commit to `main`.

GitHub Pages rebuilds automatically. Give it a minute, then hard-refresh.

### Changing the feedback endpoint

The endpoint lives in one marked line near the bottom of `index.html`:

```js
var FEEDBACK_ENDPOINT = "https://script.google.com/macros/s/.../exec";
```

The widget posts with `mode: 'no-cors'`, so it shows "sent" without reading a response. That is expected for an Apps Script target. The row still lands.

If you edit the Apps Script, **redeploy the same deployment** (Deploy, Manage deployments, edit, New version). A brand new deployment issues a new URL and breaks the wiring.

---

## Version control

The full design lineage is in git. Twenty iterations from 28 July to 17 August are replayed as dated commits, so `git log` reads as the evolution of the concept.

```bash
git log --oneline                            # the lineage, newest first
git log -p index.html                        # what changed, iteration by iteration
git show <sha>:index.html > /tmp/old.html    # open any past version
```

### Working rules

1. Branch for anything beyond a typo. Never edit main directly.
2. One commit per meaningful change. Say what changed, not "update".
3. Merge to main when it is ready to be seen. Pages rebuilds automatically.
4. Tag every cut shared with reviewers: `git tag -a review-2 -m "Second review cut"`.

`_source/` holds the original iteration files, the audio overview and the internal response document. It is git ignored, so internal material never reaches the remote.

---

## Design notes

- **Light and dark.** Defaults to light. A toggle switches modes. Colours run off the Insentra web token system.
- **Interactive.** Element tiles and delivery cards expand in place. A maturity console models the change axes.
- **Accessible.** Roving tabindex, ARIA roles and states, reduced-motion handling throughout.

---

## Status

Concept for reaction. Shared to gather structured feedback before the next iteration.
