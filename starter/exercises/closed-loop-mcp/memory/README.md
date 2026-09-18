# campaign-memory.json — how to read it

This file is the entire memory layer for the exercise. There's no database — it's a plain JSON file the server writes to every time you launch a variant or pull its performance, and you can open it directly at any point to see exactly what's been recorded.

## Shape

```json
{
  "variants": [
    {
      "variant_id": "v_a1b2c3d4",
      "headline": "...",
      "description": "...",
      "angle_tags": ["local", "human-support"],
      "status": "active | paused",
      "launched_at": "ISO timestamp",
      "pulls": 2,
      "performance": {
        "impressions": 1400,
        "clicks": 34,
        "conversions": 3,
        "spend": 82.50,
        "ctr": 0.0243,
        "cpa": 27.50
      },
      "events": [ ... a chronological log of launched / performance_pull / paused events ... ]
    }
  ]
}
```

## What to actually look at
- **`pulls`** — how many times you've checked this variant's performance. `pulls: 1` means the number is noisy; treat it skeptically.
- **`performance.ctr` / `performance.cpa`** — the two headline metrics. Higher CTR and lower CPA are both good.
- **`angle_tags`** — this is what lets you compare "did local-bank angles beat AI-cashflow angles," not just "did variant A beat variant B." Use `query_memory` (a tool, not this file) to get that comparison pre-aggregated — but this file is where you can always double-check its math by hand.
- **`events`** — the audit trail. If you paused something, the reason you gave is here.

You never need to edit this file. It's read-only from the learner's side — the server owns writing to it.
