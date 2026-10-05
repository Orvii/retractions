# 002 — "The auth-loader gate is a bug"

**Believed:** briefly, 2026-10 · **Killed:** 2026-10-05 · **Status:** tests now pin the intent

## What we believed

While preparing contract tests for opencode's plugin host (issue #51614), the natural reading of a user report (anomalyco/opencode#45214: "plugin auth loaders are only consulted when auth.json already has an entry") was: silent skip = bug; the test should assert loaders always run.

## Why it seemed true

Silent behavior changes are usually bugs; the report had a clean reproduction and an aggrieved tone. Writing a test that "fixes" the gating felt like the helpful move.

## What killed it

#45214 was **closed as intended**: loaders are consulted only when the auth store has an entry for that provider. The dispatch loop's `if (!stored) continue` is the design, not the defect.

## What changed

- The contract test ([anomalyco/opencode#53234](https://github.com/anomalyco/opencode/pull/53234)) pins the *current* behavior and says so in its body — it will fail loudly if the intent ever changes, which is the useful property.
- House rule adopted: before writing a regression test for reported behavior, check how the duplicate report was *resolved*, not just that it exists. An open issue is a question; a closed one is an answer.
