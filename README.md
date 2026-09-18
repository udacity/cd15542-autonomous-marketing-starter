# Build, Audit, and Validate a Brand-Safe Messaging System

Starter files for the capstone project in **Autonomous Marketing Systems & Agentic Orchestration** (cd15542).

Hartsfield Business Bank is launching Momentum Business Suite into a competitive market, and every launch angle carries brand and regulatory risk. You will build a two-agent messaging system — a message-generation agent that drafts on-brand angles from source material, and an independent brand-auditor agent that gates every angle on voice, factual grounding, exact character counts, banned language, and review status — then run the generate/audit/revise loop, route approved copy for human review, and validate it against a simulated ad platform over MCP.

## Getting Started

Everything you need is in [`starter/`](starter/). Open that folder as your working directory in Claude Code and follow `PROJECT-INSTRUCTIONS.md` in the classroom.

Read [`starter/README.md`](starter/README.md) first — it maps every provided file and marks what is core path versus optional.

### What you build

Two subagents, in `starter/.claude/agents/`:

- `message-generator.md`
- `brand-auditor.md`

The folder ships with a pointer note only. Building these two agents is the exercise, not a setup step.

### What is provided

* **Source material** — `brand/brand-bible.md`, `intel/competitive-brief.md`, and six HBB reference PDFs in `references/`
* **Working files** — `workspace/` templates for your angle log, staged approvals, and review record
* **Practice ad platform** — `exercises/closed-loop-mcp/`, a pre-built MCP server and dashboard you connect to but never edit
* **Optional** — `.claude/skills/hbb-trust-audit/`, a fuller compliance audit for after your own auditor works

Core path is about 4-6 hours and requires no code writing.

## Project Instructions

Full instructions and the grading rubric are in the classroom.

## License

[License](LICENSE.txt)
