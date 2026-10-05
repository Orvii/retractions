# 005 — "The measurement loop lives on the machine"

**Believed:** 2026-10-04 → 2026-10-05 · **Killed:** 2026-10-05 · **Status:** corrected in place

## What we believed

Monthly measurement loops (npm download snapshots, atlas version-pin drift) belong in systemd user timers on the workstation: zero infrastructure, `Persistent=true` catches missed runs at boot, logs where we look.

## Why it seemed true

It worked, immediately and locally. The timers fired on schedule in testing; `Persistent=true` even covers the laptop-was-asleep case. Every failure mode we imagined was a scheduling failure mode, and systemd solves scheduling.

## What killed it

The failure mode we did not imagine was the obvious one: **the machine off for a week**. A monthly loop that misses its only firing window of the month produces no data and no alarm — silence indistinguishable from "nothing changed". A measurement loop whose availability depends on a single laptop's power state is not a loop; it is a habit with a cron face.

## What changed

- Both loops moved to GitHub Actions scheduled workflows (`harness-atlas/.github/workflows/drift.yml`, org profile's `npm-metrics.yml`), committing their reports back to the repo. The loop now runs wherever GitHub runs; the reports are public artifacts, not local files.
- The systemd timers were removed, not left as backup — two loops writing the same file is a conflict, not redundancy.
- House rule: a loop's home must outlive the machine that authored it. If the loop's output matters, its scheduler must not share a power button with its author.
