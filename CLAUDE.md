# data-ai-digital-pm

## Read first (every session, before any non-trivial work)

This tool is part of Canyon Labs' internal-tools portfolio. The portfolio's
navigation and governance lives in **one place** — read it first:

- **GitHub:** https://github.com/canyon-labs-tools/portfolio/blob/main/CLAUDE.md
- **Local:** /Users/clint/Dev/Knowledge Base/portfolio/CLAUDE.md

That file is the **single source of truth** for the Knowledge Map (where
every kind of cross-cutting context lives), the 5-layer architecture, the
hard rules, the agent team, and the Tier 1 RFC. Don't duplicate its content
here; point at it.

## Tool-specific notes

### What this tool is

A single-file HTML project pipeline for the Data, AI & Digital function. Its job is to be the working surface for executive prioritization meetings: top initiatives ranked, status, owner, % progress, and a phased roadmap toward the Canyon Connect end state.

### Classification

**Internal.** No customer or regulated data. State persists in the visitor's browser via `localStorage`. JSON export/import for sharing.

### Stack

- Single static `index.html` — no backend, no dependencies beyond Google Fonts (Titillium Web + PT Sans)
- Brand tokens inlined from the `canyon-labs-brand` skill (colors, typography, gradient, mountain mark)
- Hosted on GitHub Pages (`https://canyon-labs-tools.github.io/data-ai-digital-pm/`)
- **Stack deviation vs. portfolio Next.js default:** intentional. This is a one-page tool with no server-side state — Next.js would be over-engineering. Compare `canyon-kudos` for the same pattern.

### Editing data

Default seed data is in the `DEFAULT_DATA` constant at the top of the `<script>` block. Edits made in the running page are saved to `localStorage` under key `canyonLabsDataAIDigitalPM_v1`. Reset button restores defaults.

To change defaults shipped to all users, edit `DEFAULT_DATA` in `index.html` and push. Existing users keep their localStorage edits unless they hit Reset.

### Sections

1. **Snapshot** — auto-computed counters: active initiatives, average progress, at-risk count, current Canyon Connect phase.
2. **Top initiatives** — drag-to-reorder, click-to-edit, status dropdown, owner, % progress.
3. **Roadmap to Canyon Connect** — five phases, click-to-edit, planned/active/done state.

### Things to remember

- **Every keystroke saves.** No save button. No spinner. Toast confirms exports/imports.
- **Print stylesheet** strips toolbar / add / delete chrome. Use Cmd-P to make a clean handout for an exec meeting.
- **localStorage is per-browser per-machine.** If the data needs to live in multiple places, the workflow is Export → commit JSON to this repo or a shared location → Import on the other machine.
- **No tests** — single-file static HTML, no build step.

### Future work parked here

- **Add a Decision log** section (was deferred from v1 elicitation).
- **Add an Open questions / blockers** section (also deferred).
- **Add an Exec meeting agenda** view that filters to "what changed since last meeting" — useful prep view.
- **Wire to Launchpad with AAD gating** once an admin AAD group is named (see `LAUNCHPAD_INTEGRATION.md` in the launchpad repo).
- **Optional:** swap localStorage for Supabase if the data needs to be shared / live across machines. Would move it from "a personal exec-prep tool" to "a team-visible portfolio tracker." Decision deferred — keep simple until it hurts.
