---
name: hbb-trust-audit
description: Audits Hartsfield Business Bank (HBB) ad angles / marketing copy against the project's Trust Framework and Brand Bible before they're eligible for human review. Use this whenever asked to check, audit, score, flag, or gate AI-generated HBB ad copy, RSA angles, or campaign lines for quality, stability, or compliance issues — including phrases like "run these through the trust check," "audit these angles," "is this copy safe to ship," or "check against the brand bible." Always run this before any HBB ad angle is marked approved or exported to a review sheet.
---

# HBB Trust Audit

Evaluate one or more candidate ad angles/copy lines for Hartsfield Business Bank's Momentum campaign against the project's governing documents, and return a structured PASS/REJECT verdict per angle.

## Source of truth — read these fresh each time, don't rely on memory
1. `trust/framework.md` — the three dimensions (Quality, Stability, Compliance), their check tables, and severity/fallback rules.
2. `brand/brand-bible.md` — the actual claims, voice rules, and hard bans the framework's checks point back to (especially §4 voice, §7 approved claims, §8 legal-review-required, §9 hard bans, §10 compliance mechanics).

Do not hardcode or paraphrase these rules from memory across sessions — the docs are the authority and may change. If either file is missing, stop and say so rather than guessing at rules.

## Procedure

For each candidate angle/line given to you:

1. **Quality dimension** — check factual grounding (can every claim be traced to Brand Bible §7 or the product sheet in `/references`?), brand voice adherence (does it match §4's voice pillars and avoid the "never sounds like" list?), and — if it's RSA copy — character caps: headline ≤ 30 characters, description ≤ 90 characters. Count characters exactly; don't estimate.
2. **Stability dimension** — if you're given prior-round versions of the same angle (or told this is a re-run), compare factual claims across versions for material drift. If this is the first time you're seeing this angle, note that explicitly rather than treating consistency as unknown/failed.
3. **Compliance dimension** — check against Brand Bible §8 (legal-review-required patterns: named-competitor comparisons, specific APY figures, "best" without citation, unverified approval-speed claims), §9 (hard bans — reject immediately if present), and §10 (placement rules — e.g. an APY claim must carry its disclosure in the same line/unit, not deferred). Also check for a human-oversight marker: does the angle present itself as ready-to-publish, or is it clearly still a draft pending human sign-off? Missing that marker is a compliance flag, not a technicality.
4. **Assign severity per flag** — blocker, warning, or note — using the framework doc's tables as the authority for what counts as which. When a check isn't explicitly covered by the tables, use judgment but say so in the flag's reasoning rather than inventing a severity silently.
5. **Roll up to a verdict**: any blocker anywhere → REJECT. Only warnings/notes (or nothing) → PASS. A REJECT is not a rewrite — don't silently fix the copy; report why it failed so a human or an upstream revision step can act on it.

## Output format

For each angle, return:

```
### Angle: "<the copy or angle text>"
Verdict: PASS | REJECT
Flags:
- [severity] <dimension> — <specific rule cited, e.g. "Brand Bible §9 hard ban: 'guaranteed'"> — <one-line reasoning>
(list all flags found, not just the first one; if none, write "No flags.")
```

If auditing a batch, present one block per angle in the order given, then a one-line summary count (e.g. "3 PASS, 2 REJECT").

Be exhaustive on blockers — missing one defeats the point of the audit — but don't invent flags that aren't grounded in the two source documents.
