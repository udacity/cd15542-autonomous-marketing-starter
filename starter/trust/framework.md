# Trust Framework — Hartsfield Momentum Ad Copy & Angle Evaluation

*Governs AI-generated marketing output for this project only (competitive-response angles for Momentum Business Suite). This is an operational checklist for this workflow, not a certified legal compliance program — anything flagged "compliance: blocker" still requires real legal/compliance sign-off before it ships, per Brand Bible §8.*

## Core check, in plain terms

For the Step 4 exercise, your auditor needs five checks and nothing more: voice (`brand/brand-bible.md` §3-4), factual grounding (§6-7), exact character counts on RSA-style copy (don't estimate), hard-banned language (§9), and the review-status marker from Step 3 — a missing marker is a REJECT on its own, same as any other flag. The `brand-auditor` agent you build in Step 4 (`.claude/agents/brand-auditor.md`) should do exactly this and nothing more. Use that for the core path.

Everything below this point — the full three-dimension rubric, the EU AI Act/Colorado AI Act-aligned compliance checks, the `hbb-trust-audit` skill that implements it — is **advanced / optional material**. It's here because it's what a real launch would actually need before shipping, and it's a good stretch goal if you have time, but it is not required for the core 4-6 hour submission.

---

## Purpose
Every AI-generated ad angle or piece of copy must pass through this rubric before it is eligible for human review. The rubric has three dimensions, each scored per angle, each with defined severities and a fallback action.

## Dimension 1 — Quality
| Check | Blocker | Warning | Note |
|---|---|---|---|
| Factual grounding | Claim has no traceable source (Brand Bible §7, product sheet, or cited competitor research) | Claim is directionally true but not verbatim-sourced | Phrasing could be tighter but claim is sound |
| Brand voice adherence | Sounds like the "Never sounds like" list (Brand Bible §4) | Voice is close but not fully declarative/plain | Minor tone drift |
| Character caps (RSA copy) | Headline > 30 chars or description > 90 chars | N/A — caps are hard limits | N/A |

**Fallback:** Blocker → auto-reject, log reason, do not pass to human review. Warning → pass through with a flag for the human reviewer. Note → pass through silently, logged for pattern-tracking only.

## Dimension 2 — Stability
| Check | Blocker | Warning | Note |
|---|---|---|---|
| Consistency across regenerations | Re-running the same prompt produces a materially different factual claim about HBB or the competitor | Same claim, different phrasing each time (expected) | N/A |
| Version diffing | No prior version exists to diff against (first run) — not a failure, just flagged for visibility | — | — |

**Fallback:** Blocker → hold, re-run once; if it recurs, route to manual research rather than trusting either output.

## Dimension 3 — Compliance (checklist, not legal certification)
Applies HBB's real compliance guardrails (Brand Bible §8–10) plus EU AI Act / Colorado AI Act–style themes relevant to AI-generated marketing content:

| Check | Blocker | Warning | Note |
|---|---|---|---|
| Hard-banned term present (Brand Bible §9) | Any hard-banned term/phrase found | — | — |
| Named-competitor comparison | Present without legal-review flag attached | Present, correctly flagged for legal review | — |
| APY/rate claim | Rate stated without disclosure in the same unit of communication (Brand Bible §10) | Rate + disclosure present but disclosure incomplete (missing date or variable statement) | — |
| FDIC claim | Shortened/implied FDIC language | Full phrase present but placement unclear | — |
| Testimonial | Used without a note that consent/release is required | — | — |
| AI-disclosure / human-oversight theme (EU AI Act / CO AI Act) | Angle presented as final/ready-to-publish with no human-review marker **tracked as metadata (status field, e.g. the pipeline's `round`/CSV `Status` column) — never written inline into the character-capped headline/description text itself** | — | — |

**Fallback:** Blocker → hold for legal/compliance review, never auto-published. Warning → pass to human review with the flag visible. This checklist cannot certify legal compliance — it exists to catch the same violations HBB has already told us are non-negotiable, before a human ever has to.

## Severity Roll-Up Rule
An angle with **any Blocker** in any dimension does not advance past this stage — it is dropped from the current round, logged with the specific check and reason, and (in the pipeline) routed back for one revision attempt. An angle with only Warnings/Notes advances to human review with all flags attached, not silently.

## EU AI Act / Colorado AI Act — What This Actually Covers
This project does not make a legal determination of compliance under either law. What it does, as a good-faith operational control:
- **Human oversight:** no AI-generated angle reaches a Google Sheet or any publishing surface without passing through this rubric and a human approval step (see `workspace/approval-record-template.md` once populated).
- **Transparency:** every angle carries its full audit trail (which checks fired, at what severity, what round) — nothing is presented as "AI wrote this and it's fine" without a visible reasoning trail.
- **No deceptive/manipulative content:** the hard-ban and disclosure-placement rules above are the direct implementation of this principle for financial marketing specifically.
- **Limitation, stated plainly:** neither the EU AI Act nor the Colorado AI Act is fully operationalized by this checklist. A real compliance/legal review is required before any of this output is used in a live campaign, particularly one touching EU consumers or Colorado residents.
