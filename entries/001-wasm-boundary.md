# 001 — "WASM kernels are faster, period"

**Believed:** 2026-04 → 2026-10 · **Killed:** 2026-10-04 · **Status:** corrected in place

## What we believed

Rewriting hot numeric kernels from TypeScript to Rust-WASM makes them faster. The project framing ("Bun-first engine with Rust-WASM kernels") assumed this as background physics.

## Why it seemed true

It usually is true — for batch workloads. The SIMD dataset kernels in our own harness ran 3-4.7× faster than their scalar paths, and the literature on WASM numeric workloads agrees at scale.

## What killed it

Our first recorded benchmark snapshot (Ryzen 5 5600, Bun 1.4.3, `BENCH_PROFILE=large`): the per-element `WASM loop` median was **6.54 ms** against **3.21 ms** for the plain TypeScript loop at the same workload. The JS↔WASM call boundary cost more per call than the kernel saved per call. One table, both directions.

## What changed

- The snapshot published the losing row in the same table, same font — the recorded-snapshots section of the project's own README, which lists every arm including the one that lost.
- The engineering direction moved from "write more kernels" to "batch across the boundary".
- [bench-notes/ffi-boundary-crossover](https://github.com/Orvii/bench-notes) now states the general rule: measure the crossover size, or don't claim a winner.
