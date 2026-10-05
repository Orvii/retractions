# 007 — "The transparent lockup was the light banner"

**Believed:** 2026-10-05, for one commit · **Killed:** same day, by the brand owner · **Status:** corrected in place

## What we believed

When assembling the org profile's theme-aware banner pair, the transparent-background horizontal lockup was published as `banner-light.png` — the asset light-theme readers receive.

## Why it seemed true

It *looked* correct in isolation: a light-theme asset should sit on light backgrounds, and a transparent PNG adapts to any of them. The reasoning was generic ("transparent = flexible") instead of specific ("what did the brand actually ship for light surfaces?").

## What killed it

One sentence from the brand owner: the real light asset is the white-backgrounded lockup; the transparent one is a different artifact with a different job. On GitHub's light surface the transparent version floated without its intended canvas — visibly wrong to the person whose brand it is, invisible to everyone else.

## What changed

- `banner-light.png` is now the backgrounded lockup; the transparent one remains as `banner-light-transparent.png` for surfaces that genuinely need it ([orvii profile repo, assets/](https://github.com/Orvii/.github)).
- House rule: brand assets are chosen by asking the brand owner which artifact is *the* one for a surface — not by inferring from file properties. Flexibility is not a brand decision.
