# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm start        # serve on http://localhost:3000
npm run dev      # same, no clipboard notification
```

No install step needed — uses `npx serve` (zero local dependencies).

## Architecture

Single-page static HTML workshop. All markup, CSS, and JS live in `public/nbn_workshop.html` — no build step, no bundler.

**File layout:**
- `public/index.html` — all HTML content (~1160 lines); edit this to add/change prompts
- `public/css/styles.css` — all styles; edit for visual changes
- `public/js/app.js` — three functions: `switchTab`, `toggleAccordion`, `copyPrompt`

**Content structure in index.html:**
- Two tab panels: `#panel-fault` (9-prompt chain) and `#panel-fun` (4 activities)
- Each prompt card: `.prompt-card` > `.prompt-header` + `.prompt-body` + accordion toggle + `.accordion-content`

**To add a prompt:** copy an existing `.prompt-card` block, give the `<pre>` a new id (e.g. `p10`), update the step badge, title, role pill, and `onclick="copyPrompt(this, 'p10')"`.

**To add a tab:** add a `.tab-btn` in `.tabs`, add a matching `<div class="activity-panel" id="panel-X">` in `<main>`.
