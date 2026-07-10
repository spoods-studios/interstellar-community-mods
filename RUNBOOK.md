# Runbook — interstellar-community-mods

Curated and featured community mods — the showcase/curation home for mods
built with `interstellar-mod-sdk`. Currently a **dormant scaffold**: no
curated mods or curation process yet. Activates at **Phase 4**, alongside
`interstellar-mod-sdk` — and additionally depends on Steam Workshop
integration existing before a curation process makes sense.

## Skills available here

| Skill | What it does |
|---|---|
| `/community-mods-start` | Auto-fires on the first turn of any session here. Reads `vault/context.md` + `vault/conventions.md`, checks `vault/decisions/` for recent entries, surfaces git status and `.planning/STATE.md` (if present), prints a compact briefing. |
| `/community-mods-end [--discard]` | Session close — appends `vault/learnings/sessions.md`, captures any gray-area decision to `vault/decisions/`, commits (no push). `--discard` skips all writes. |
| `gsd-*` phase-loop ceremonies (`gsd-new-milestone`, `gsd-discuss-phase`, `gsd-plan-phase`, `gsd-execute-phase`, `gsd-verify-work`, `gsd-code-review`) | Seeded once `/bootstrap-repo community-mods` activates this repo. |

## Lifecycle & gate tier

**Tier t3 — Standard Review** (`gate-tiers.md`). Milestone close needs a
standard `gsd-code-review` run, or a plain checklist review for curation
content (mod QA, licensing/attribution). No mandatory multi-vendor grid, no
mandatory playtest. Broken/unsafe mod listings still block; cosmetic nits
don't.

**Dependency note:** curation work is blocked not just on Phase 4 opening
but on **Steam Workshop integration** existing — check `interstellar-mod-sdk`
and the engine's Steamworks status before expecting `.planning/` here even
after Phase 4 nominally lights up.

**Activation flow:** `/bootstrap-repo community-mods` from a studio session
→ `gsd-new-project` fed the PRD/Roadmap sections scoped to this repo →
`gsd-new-milestone` per the org manifest's community-mods slice (Phase 4).

## What do I do next?

| State | Action |
|---|---|
| Repo still dormant | Nothing to do here — work starts once Phase 4 (and Steam Workshop) routes through `/bootstrap-repo community-mods`. |
| Just bootstrapped | Run `gsd-new-milestone` using the manifest's community-mods slice; confirm Steam Workshop integration is actually live before scoping curation work. |
| Mid-milestone | Check `.planning/STATE.md`, then run the next phase: `gsd-discuss-phase` → `gsd-plan-phase` → `gsd-execute-phase` → `gsd-verify-work`. |
| Phase complete | Standard review — `gsd-code-review` or a plain curation checklist. No playtest gate at this tier. |
| Milestone slice complete | File the review record, then run `/studio-milestone status` in `studio` to write back the slice and get the `Next up:` line. |
| Session ending | `/community-mods-end` (or `--discard` for a purely exploratory session). |
| Unsure | Read `../studio/RUNBOOK.md`. |

## Org context

- `../studio/RUNBOOK.md` — org-wide skill catalog + current state
- `../studio/vault/project/Milestone Playbook.md` — full open → close → devblog tutorial
- `../studio/vault/project/gate-tiers.md` — full tier definitions (this repo is t3)
- Standing obligations auto-surface at every session start via the SessionStart hook — nothing to run to see them.
