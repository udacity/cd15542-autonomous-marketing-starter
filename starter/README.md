# Start Here

## Who you are

You just joined Hartsfield Business Bank (HBB) as a marketing operations specialist, two weeks before the launch of the Momentum Business Suite — the bank's first fully digital product. Competitor activity is moving fast, and the Brand Manager needs a set of vetted messaging angles before the next division planning meeting. You don't have the brand instincts or legacy knowledge the rest of the team has built up over 25 years, and there's no time for a mentor to walk you through it by hand.

You're going to build a small system of AI agents that draft on-brand messaging, audit it, and refine it so you can bring vetted angles to that meeting instead of a blank page.

## Before you start

You should already be comfortable with: the standard marketing lifecycle and its milestone deliverables, using an LLM chat interface (like Claude Code), spreadsheets, basic prompt engineering, and reading brand guidelines. Nothing in the **core path** below requires you to write or edit code.

**Time:** 4-6 hours for the core path. Anything under "Optional / Bonus" at the bottom is separate and not required.

See `PROJECT-INSTRUCTIONS.md` (one level up, at the project root) for the full step-by-step assignment and the exact deliverables you'll submit. This file is a quick orientation to what's in this `starter/` folder and where to find things.

## What's in this folder

- **`.claude/agents/`** — currently empty except for a pointer note. You'll create `message-generator.md` and `brand-auditor.md` here yourself in Steps 3-4 — building these two agents is the actual exercise, not a setup step. `PROJECT-INSTRUCTIONS.md` describes what each one needs to do.
- **`.claude/skills/hbb-trust-audit/`** — an optional, more advanced audit skill (full compliance rubric), already built. For after you've cleared your own core brand-auditor check.
- **`brand/brand-bible.md`** — the brand rubric your brand-auditor agent will check every angle against.
- **`intel/competitive-brief.md`** — the competitive intelligence on Bank of America's small-business push. Read this for your launch angle.
- **`references/`** — the six source PDFs the Brand Bible was synthesized from, in case you want to go to the primary record.
- **`trust/framework.md`** — the audit rubric. Has a plain-language core section at the top (what your brand-auditor agent should check) and an optional advanced section below it.
- **`workspace/`** — your blank working files: `angles-workspace.md` for Step 1 and Steps 5-8, `approved-angles-template.csv` and `approval-record-template.md` for Step 9. Fill these in as you go.
- **`exercises/closed-loop-mcp/`** — the practice ad platform used in Step 10. Fully pre-built — you install and connect it, you never edit its code. See its own `README.md`.

## Optional / Bonus (not required for the core 4-6 hour path)

- The advanced section of `trust/framework.md` and the `.claude/skills/hbb-trust-audit/` skill it powers — the full quality/stability/compliance rubric, including human-oversight tracking modeled on EU AI Act/Colorado AI Act themes.
- Going beyond a single closed-loop MCP round-trip in `exercises/closed-loop-mcp/` — e.g. running a third round, or testing angles you ultimately rejected to see how they'd have performed.
