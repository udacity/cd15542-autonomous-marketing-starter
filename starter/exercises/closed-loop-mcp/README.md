# Closed-Loop Optimization Exercise — Mock Ad Platform

*This is required for Step 10 of `PROJECT-INSTRUCTIONS.md`. It's already fully built for you: you're not writing or editing any code here, just installing and connecting a ready-made tool, the same way you'd install any app. Two commands, no code to touch.*

A practice ad platform that runs entirely on your own computer. No Google Ads account, no Meta account, no login, no waiting on anyone's approval. It behaves like a real ad platform — you launch ad variants, you pull back performance numbers — except the "customers" clicking your ads are a simulator, not real people.

**What you're actually practicing:** connecting an AI agent to a live system through MCP (the tool-calling protocol real marketing agents use to talk to real ad platforms), reading results back, and using a memory log to make your next round of ads smarter than your first. That loop — try, measure, remember, improve — is the real skill. We only swapped the ad account for a practice one.

Full walkthrough: see `activity-guide.md` in this folder. Read that first — this file is just setup.

## One-time setup

The server is pre-built — you're installing it, not writing it. Two commands, both run from a terminal, neither requires you to open or edit any code file:

1. Install the pre-built tool's dependencies (already done if you're reading this after we built it, but if you ever move this folder):
   ```
   cd "exercises/closed-loop-mcp"
   npm install
   ```
2. Connect the pre-built server to Claude Code:
   ```
   claude mcp add mock-ad-platform -- node "$(pwd)/server.js"
   ```
   (Run this from inside the `closed-loop-mcp` folder so `$(pwd)` points at the right place. You're pointing Claude Code at a file that already exists — you never need to open `server.js` yourself.)
3. That's it — no accounts, no keys, no OAuth. Start a new Claude Code session and the tools `launch_variant`, `get_performance`, `query_memory`, and `pause_variant` will be available.

## Watching it live (recommended)

In a separate terminal tab, from this folder, run:
```
npm run dashboard
```
Then open **http://localhost:4319** in your browser and leave the tab open. It auto-refreshes every few seconds, showing a bar chart of CTR by angle tag and a table of every variant with its status. This is just a viewer — it reads `memory/campaign-memory.json`, it doesn't change anything. You'll see it update live as you launch variants and pull performance during the activity.

**Important: run this command yourself, in your own terminal tab — don't ask Claude/an agent to start it for you in the background.** A process an AI agent starts in the background can silently die between messages without warning; a process you start yourself in a terminal window stays up for as long as that window is open, exactly like any other local dev server. If you're going through this activity with an agent's help, this is the one step to type yourself.

### If localhost:4319 won't load
1. Check the terminal tab you ran `npm run dashboard` in — is it still open, and does it still show `Closed-loop dashboard running at http://localhost:4319`? If the tab got closed or the command stopped, just re-run `npm run dashboard`.
2. If re-running gives an error like `EADDRINUSE` / "address already in use," it's already running somewhere (maybe another terminal tab) — you don't need a second copy, just open the browser tab.
3. Double-check the URL is exactly `http://localhost:4319` (not https, not a different port).
4. This dashboard is separate from the MCP server itself — you can do the whole exercise through Claude Code's tools without it running at all. It's a nice-to-have viewer, not a requirement.

## What each tool does
- **`launch_variant`** — publish an ad (headline, description, angle tags) into the simulated campaign.
- **`get_performance`** — pull performance for a variant. Call it more than once over the course of a session — each call simulates more flight time, so early reads are noisier than later ones. That's intentional.
- **`query_memory`** — see everything you've launched so far, aggregated by angle tag, so you can compare "local" angles against "AI cash flow" angles etc. instead of eyeballing individual ads.
- **`pause_variant`** — stop something that's underperforming, with a reason logged.

## Where results live
`memory/campaign-memory.json` — a plain, human-readable log the server writes to automatically. Open it any time. See `memory/README.md` for how to read it.

## Resetting
To start over with a clean slate, replace the contents of `memory/campaign-memory.json` with:
```json
{ "variants": [] }
```
