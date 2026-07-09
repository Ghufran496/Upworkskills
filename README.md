# UpworkSkills

A best-of-breed Claude skill for winning Upwork proposals, built by synthesizing the strongest public Claude/Claude-Code proposal skills.

## What's here

`.claude/skills/upwork-proposal/` — the skill. Invoke it in Claude Code with `/upwork-proposal`, or just paste a job post and it triggers automatically.

Runs as a **3-layer pipeline**: **Qualify** (score the job + client risk, decide draft/skip) → **Write** (Hook/Proof/Close in your voice) → **QA** (quality pass).

> **Sharing this workspace?** Everything the skill needs ships inside `.claude/skills/upwork-proposal/` — the canonical spec, all rules, and the full profile/projects. Anyone who opens this workspace and uses `/upwork-proposal` gets the exact same structure and behavior. (Personal Claude memory does not transfer, but nothing critical lives only there.)

**`references/pipeline.md` is the canonical spec** — the definitive structure, scoring method, output format, and non-negotiable rules. Read it first.

```
.claude/skills/upwork-proposal/
├── SKILL.md              # 3-layer pipeline + routing brain + hard rules
├── references/
│   ├── pipeline.md       # ★ CANONICAL SPEC — structure, scoring, format, rules
│   ├── job-scoring.md    # LAYER 1: job scoring, client risk, portfolio match, angle
│   ├── structure.md      # LAYER 2: Hook → Proof → Close
│   ├── voice.md          # anti-AI voice rules + banned words
│   ├── pricing.md        # pricing strategy & phased estimates
│   ├── objections.md     # objection handling + follow-ups
│   └── examples.md       # calibration examples by niche
└── assets/
    ├── profile.md        # Ali's real voice + proof (filled in)
    ├── applications.md   # every qualified job logged (response tracking + A/B)
    └── log.md            # outcome log; the skill learns from it
```

## Setup (one time)
1. Open `.claude/skills/upwork-proposal/assets/profile.md` and fill in every `[BRACKET]` — your niches, real outcomes with numbers, rates, links, voice sample. This is what makes proposals yours instead of generic.

## Use
- Paste an Upwork job post → get a copy-paste-ready proposal, screening answers, a suggested bid, and why it wins.
- "How much should I charge for this?" → priced recommendation.
- "Client said my price is too high" → objection reply.
- After sending, tell it the result so it logs the outcome and gets smarter over time.

## Autonomous agent (optional delivery layer)
`AGENT_INTEGRATION.md` wires the [citizenweb3/upwork-agent](https://github.com/citizenweb3/upwork-agent) daemon to this skill: the agent finds jobs (Chrome/CDP), pushes them to Telegram, and submits on your approval — using our qualify→write→humanize pipeline as its brain. It needs infra + secrets (Telegram bot, Claude OAuth, Upwork login) to run.

## Ideas synthesized
- **Job qualification: scoring + client risk + portfolio match + application tracking + A/B** (dvcrn *Upwork Seller Assistant*) — Layer 1
- Hook/Proof/Close proposal template + routing table + banned-word voice engine (Martin Garramon's online-hustle)
- Keyword→template/angle routing & specificity-over-adjectives (YedanYagami template pack)
- 55–75 word brevity + 1–10 job scoring threshold (n8n Vollna / Nick Saraev formula)
- Quality-analysis + optimization pass (LiveWithCodeAnkit AI-Driven tool) — Layer 3
- Pricing strategy + phased cost estimates (contract-and-proposal-writer)
- Objection handling & self-correcting outcome log (full sales-system pattern)
