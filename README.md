# Data, AI & Digital — Project Pipeline

Single-page agile project pipeline for Canyon Labs' Data, AI & Digital function. Built for executive prioritization meetings: top initiatives ranked, status and progress visible, plus a phased roadmap to the Canyon Connect end state.

**Live:** [`https://canyon-labs-tools.github.io/data-ai-digital-pm/`](https://canyon-labs-tools.github.io/data-ai-digital-pm/)

## What it does

- **Top initiatives.** Ranked priority list. Drag the rank number to reorder. Click any field to edit. Status (on track / at risk / blocked / done / planned), owner, and % progress.
- **Roadmap to Canyon Connect.** Five-phase journey from foundation through production cutover. Edit titles, details, and state inline.
- **Snapshot strip.** Auto-computed counters: active initiatives, average progress, at-risk count, current phase.
- **Persistence.** Every edit saves to `localStorage`. Toolbar offers Export (JSON), Import (JSON), Print (clean handout), Reset (back to defaults).

## Why a single HTML file

This is a personal exec-prep tool, not a multi-user system. Single file. No backend. No build. Open it in any browser. Works offline once loaded. Compare `canyon-kudos` — same pattern, same reasoning.

If/when the data needs to be shared live across multiple people, the right move is to swap localStorage for Supabase, not to restructure as a Next.js app. That's a future decision — see `CLAUDE.md` for the parking lot.

## Local development

```bash
git clone git@github.com:canyon-labs-tools/data-ai-digital-pm.git
cd data-ai-digital-pm
open index.html        # or: python3 -m http.server 8000
```

That's the whole workflow. No `npm install`, no `npm run dev`.

## Theming

Tokens come from the `canyon-labs-brand` skill (CSS variables inlined at the top of `index.html`). Colors, gradients, typography, and the mountain mark all match the rest of the Canyon Labs portfolio. To update, copy the latest tokens from the brand skill's `colors-and-type.css` into the `<style>` block under the `:root` selector.

## Editing the seed data

Default initiatives and roadmap phases live in the `DEFAULT_DATA` constant at the top of the `<script>` block. Changes there ship to all users. User edits override defaults via `localStorage` until they hit Reset.

## Classification

**Internal.** No customer or regulated data. See `CLAUDE.md` for the portfolio context.

## License

Internal Canyon Labs use. Canyon Labs™ is a trademark of Ultradent Products, Inc.
