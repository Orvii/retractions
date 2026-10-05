# 004 — "Docs are the spec"

**Believed:** implicitly, always · **Killed:** 2026-10-05 · **Status:** evidence rule added

## What we believed

When code and documentation disagree, one of them is stale and the other is the truth — and for capability questions, docs are the truth, because they express intent.

## Why it seemed true

Docs are written to be read; code is written to run. For "what does this promise" questions, intent is exactly what we want, and docs are intent's native habitat.

## What killed it

Two opposite collisions in one week:

1. opencode issue #46551 reported that configured plugin **file paths** are silently dropped since a code change — while we expected the docs to still promise file paths. Checking the current docs: they no longer do. The *docs had moved* and the issue's premise was stale in the other direction.
2. The atlas's own evidence rule kept catching docs describing flags as available that the code gates behind experimental env vars (Claude Code agent teams; Copilot CLI scheduling).

Neither source is "the spec". They are two witnesses with different failure modes.

## What changed

- Atlas cells cite docs for *promises* and mark `partial` with a note when a flag or gate qualifies the claim; code-level gates are called out in `limitations`.
- House rule: when docs and code disagree, publish both statements with dates and name the disagreement — the delta is usually the interesting finding (see [harness-atlas SYNTHESIS §3](https://github.com/Orvii/harness-atlas)).
