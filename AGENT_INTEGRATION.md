# Autonomous Agent Integration (citizenweb3/upwork-agent)

> **DECISION (personal/local use):** We are **NOT deploying** the autonomous daemon (no Docker, no Telegram, no cron, no auto-submit). The only valuable part — the agent's **job-scoring + Apply/Redo logic** — is already folded into the skill (see "Agent mode" in `references/job-scoring.md`). So the whole thing runs from a **single skill invocation**: paste a job → it passes through qualify → write → humanize → you receive the final proposal.
>
> The daemon steps below are kept only as an **optional future reference** if you ever want the hands-off autonomous version. You can ignore them for normal use.

---

This wires the **[citizenweb3/upwork-agent](https://github.com/citizenweb3/upwork-agent)** autonomous daemon to our `upwork-proposal` skill so the agent uses our 3-layer pipeline as its brain.

## What each piece does
- **upwork-agent (delivery layer):** runs Chrome via CDP with your logged-in Upwork session, searches jobs on a cron, sends job cards to Telegram, and submits proposals when you tap **Send**. It spawns `claude -p "<task>"` to do the thinking.
- **upwork-proposal skill (brain):** does the scoring, writing, and humanizing. This is what we built.

The agent already delegates scoring + writing to Claude Code. We just point that delegation at our skill.

## Wiring (3 steps, done when you deploy the agent)

### 1. Put our skill inside the agent's repo
Copy our skill into the cloned agent so Claude Code loads it when the daemon spawns it:
```
cp -R /Users/ghufran/Data/UpworkSkills/.claude  <upwork-agent>/.claude
```
Now `<upwork-agent>/.claude/skills/upwork-proposal/` exists and is auto-available to every `claude -p` the daemon runs.

### 2. Share one profile (single source of truth)
The agent reads `data/profile.md`; our skill reads `.claude/skills/upwork-proposal/assets/profile.md`. Point them at the same content so scoring/voice never drift:
```
cp /Users/ghufran/Data/UpworkSkills/.claude/skills/upwork-proposal/assets/profile.md  <upwork-agent>/data/profile.md
```
(Ali's profile is already filled in.)

### 3. Make the agent's CLAUDE.md call our pipeline
Add this block to the top of `<upwork-agent>/CLAUDE.md` so the agent's score/write/redo tasks route through our skill:

```md
## Proposal brain: use the upwork-proposal skill
For every scoring, proposal, and redo task, use the `upwork-proposal` skill in
.claude/skills/upwork-proposal/ as the source of truth.

- SCORING a job → run Layer 1 (references/job-scoring.md). Output BOTH the 0–20
  score and the 0–10 = round(score/2). Forward jobs scoring ≥4/10 to Telegram.
- APPLY (write a proposal) → run the full pipeline: Layer 1 qualify → Layer 2
  write (Hook/Proof/Close, references/structure.md + voice.md + pricing.md) →
  Layer 3 humanize (references/humanizer.md, AI-tell score ≤10). Keep it 55–120
  words for the Upwork box. Obey any hidden instruction in the post first.
- REDO → generate a genuinely different angle (swap opener + proof), not a reword.
- Never fabricate experience/metrics/clients — use only assets/profile.md.
- After submit, append the result to assets/applications.md and assets/log.md.
```

That's the whole integration. The daemon's Telegram buttons (Apply / Send / Redo) now drive our qualify→write→humanize pipeline, and every send is logged back into our tracker for self-correction.

## What YOU must provide to actually run the daemon (it needs secrets + infra)
This is a real background service, so it can't just "run" without:
- **A server or always-on machine** (Docker recommended) — or your Mac for bare-metal.
- **Telegram bot**: `BOT_TOKEN` (from @BotFather), `CHAT_ID`, `ALLOWED_USERS`.
- **Claude Code OAuth**: `CLAUDE_CODE_OAUTH_TOKEN`, account/org UUIDs (from a logged-in Claude Code).
- **Upwork login**: done manually once in the agent's Chrome (session persists).
- **Connects** on Upwork to actually submit.

## Recommended way to run it (human-in-the-loop)
Keep the agent in **approval mode**, not full auto-submit: it finds + drafts, you approve each **Send** from Telegram. That gives you the automation speed with a human gate — the safest use, and it keeps you inside Upwork's ToS (no silent mass-bidding).

## Scoring reconciliation
| Our verdict (0–20) | Agent score (0–10) | Action |
|---|---|---|
| 17–20 | 9–10 | Strong — apply early |
| 14–16 | 7–8 | Decent — apply if capacity |
| ≤13 | ≤6 | Weak — skip (agent still forwards ≥4 for your eyeball) |
