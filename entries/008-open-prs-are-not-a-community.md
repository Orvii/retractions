# 008 — "Eight open PRs meant an active community"

**Believed:** 2026-10-05, for one pull request · **Killed:** same day, by the user · **Status:** PR closed, contribution withdrawn

## What we believed

Ischca/awesome-agents-md looked like a living list worth contributing to: the contribution rules were detailed and specific (unicorn keyword, two-PR review, exact entry format), and the repo carried eight open pull requests. We opened PR #27 against it, formatted to the letter.

## Why it seemed true

Activity was inferred from the wrong signal. Open PRs read as "people are contributing here"; detailed rules read as "maintainers care". Neither is a maintainer signal. A pile of unmerged PRs is what a repo looks like *after* its maintainer stops merging — the rules were written when someone was still reading them.

## What killed it

The user checked what we had not: `pushed_at` and, decisively, the date of the last *merged* PR — May 2025, over a year stale. The eight open PRs were not a queue; they were a graveyard. The PR was closed with an apology comment and the local clone deleted.

## What changed

- Due diligence before any curated-list contribution is now three signals, checked in this order: `pushed_at`, **last merged PR date**, and open-PR age. Rules compliance is not the goal; a merged contribution is.
- The rule is permanent house policy (recorded in memory as
  `curated-list-due-diligence`) and re-applied on 2026-10-06: kyrolabs/awesome-agents
  passed liveness but auto-closes brand-new repos, so no submission; e2b-dev and
  punkpeye lists show no recent merges, so no submission.
- The lesson generalizes: **a queue nobody drains is not a community.** Count what
  left the system (merges, releases, responses), never what entered it.
