# ATL Partners — Portfolio Intelligence Hub

Single-page portal that lazy-loads five standalone tool iframes for ATL Partners' Aerospace, Transportation & Logistics portfolio.

---

## Folder layout

```
pages_portfolio/
├── index.html          ← Hub shell — the page GitHub Pages serves
└── tools/
    ├── aero-accessories.html     Aero Accessories · Part 145 MRO Acquisition Intelligence
    ├── arrive-logistics.html     Arrive Logistics · Shipper Target-Account Intelligence
    ├── trident-solutions.html    Trident Solutions · Defense Program & Contract Pipeline
    ├── skymark-rampmaster.html   SkyMark + Rampmaster · Airport Fueling Territory
    └── sky-leasing.html          SKY Leasing · Fleet & Airline Health Dashboard
```

---

## Deploy to GitHub Pages

> **Repo name:** The playbook body hard-codes tool URLs under
> `https://syedr64.github.io/ATLPartners_Intelligence_Portal/`. To keep those
> links live, the GitHub repo hosting this content must be named
> **`ATLPartners_Intelligence_Portal`** (case-sensitive). If a different name
> is used, update the five `link(...)` targets in `generate_atl_partners.js`
> (Appendix E plus each `4A–4E` tool line) and regenerate the `.docx`.

### Option A — Repo root (simplest)

1. Copy `pages_portfolio/` contents to the **root** of a new repo named
   `ATLPartners_Intelligence_Portal` (so `index.html` is at `/`).
2. Repo → Settings → Pages → Source: **Deploy from branch** → `main` → `/` (root).
3. Push. Pages builds in about 60 seconds.

### Option B — `/docs` subfolder (existing repo)

Place the contents in a `/docs` folder and point Pages at `main /docs`.

### Option C — `gh-pages` branch

Orphan a `gh-pages` branch, copy the contents, push, and point Pages at that branch.

---

## Notes

- **No build step.** All five tools are self-contained single-file HTML. No npm, no bundler.
- **Lazy loading.** An iframe's `src` is set only when the user first clicks that tool. The hub shell loads instantly.
- **Mobile RAM saver.** At ≤ 768px, background iframe `src` values are cleared after 8 s of inactivity so the browser can reclaim memory.
- **Fixed-viewport tools** (currently Aero Accessories map) are wrapped in a horizontally scrollable container on narrow screens rather than being rewritten.
- **Full-screen button** on every header strip opens the tool directly in a new tab.
- **Illustrative only.** All revenue opportunity figures and scoring are illustrative planning proxies, not forecasts.

---

## Customisation quick-reference

| What | Where in `index.html` |
|---|---|
| Change accent color | `.nav-item.active` border-left, `.dot-xx` — search `#5b8dd6` |
| Add a sixth tool | Copy one `<div class="tool-pane">` block; add `nav-item` and `topbar-tab`; add ID to `TOOLS` array |
| Change unload delay | `MOBILE_UNLOAD_DELAY = 8000` in the script block |
| Swap the tool accent palette | `.acc-xx` and `.dot-xx` classes near the bottom of the `<style>` block |
