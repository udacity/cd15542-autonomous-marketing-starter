# Activity: Close the Loop

**Time:** ~1.5–3 hours. **Prerequisite:** the mock ad platform is connected (see `README.md`) and you've read `brand/brand-bible.md` and `intel/competitive-brief.md` (two levels up, at the root of `starter/`) — you'll reuse those angles here.

## The point of this exercise
Generating ad copy once and hoping is not "autonomous marketing." The actual skill is: launch something, measure what really happened, remember it, and let that memory change what you generate next. This exercise makes you do that loop for real, twice, so you can point to evidence it closed — not just describe the idea.

## Round 1 — launch and measure

*If you started `npm run dashboard`, keep that tab open — you'll see each variant land at http://localhost:4319 as you launch it.*

1. Write 4–6 ad variants (headline + description) pitching Hartsfield Momentum, each tagged with the kind of pitch it's making. Use these tags so they're comparable: `local`, `ai-cashflow`, `human-support`, `fee-simplicity`, `generic-fee`, `competitor-comparison`. Mix it up — don't just write all-winning angles; include at least one plain/generic one on purpose.
2. Call `launch_variant` for each one. Note the `variant_id` each returns.
3. Call `get_performance` for every variant **twice** (once now, once again a few minutes later in the same session) — the second pull simulates more flight time and gives you a steadier number than the first.

## Checkpoint — read before generating round 2
Call `query_memory` with no filter. Look at `performance_by_tag`. Answer, in your own words, in a short note:
- Which tags are winning (higher CTR, lower CPA)?
- Which are losing?
- Would you trust this after only 2 pulls per variant, or do you want more data before betting the whole budget on it? Why?

This step matters — an agent (or a marketer) that reacts to noise instead of signal makes worse decisions than one that waits for enough data. Say what "enough" means to you here.

## Round 2 — regenerate, informed by memory

Write 4–6 **new** variants. For each one, write one sentence stating which memory entry/entries justify it — e.g., "doubling down on `ai-cashflow` because it had the best CPA in round 1" or "dropping `generic-fee` entirely — it converted worst." You're not allowed to just write new ads from scratch; every one has to trace back to something `query_memory` actually showed you.

Launch them the same way, pull performance twice each.

## Close the loop — prove it worked

Call `query_memory` again. Compare the aggregate CTR and CPA across **all round 1 variants** vs. **all round 2 variants**. Write a short before/after note:
- Did round 2 outperform round 1 on average?
- If yes — that's the loop closing: data from round 1 produced a measurably better round 2.
- If no — that's a real and useful result too. Say why you think it didn't work (not enough data yet? wrong tags carried over? noise?) — diagnosing a failed loop is part of the skill.

## Reflection — bridging to the real thing
In 3–4 sentences: what would be different connecting this same pattern to a *real* Google Ads or Meta account instead of this simulator? Touch on: OAuth/account setup, needing a real statistical-significance threshold before trusting a result, a real spend cap, and the fact that in the main capstone, nothing reaches this stage without passing the brand + trust/compliance audit first — that gate doesn't go away just because something is testing well.

## What "done" looks like
- `memory/campaign-memory.json` shows both rounds, legible on its own.
- A short written note (round 1 read, round 2 justifications, before/after comparison, reflection) — this is the artifact you'd show an employer as evidence you can execute this pattern, not just explain it.
