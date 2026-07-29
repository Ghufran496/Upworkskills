# CANONICAL PIPELINE SPEC — read first, always follow

This is the definitive structure, format, and rules for every Upwork proposal produced by this skill. Any user of this workspace must follow this exactly. It ships with the workspace (it is not stored in personal memory).

## The 3-layer flow (run in order on every job)
```
JOB PASTED
   │
   ▼  LAYER 1 — QUALIFY   → score 0–20, decide APPLY or SKIP   (references/job-scoring.md)
   │
   ▼  LAYER 2 — WRITE     → Greeting → Hook → Proof → Close → Sign-off   (structure.md, voice.md, pricing.md)
   │
   ▼  LAYER 3 — QA/HUMANIZE → AI-tell score 0–100, rewrite until ≤10   (humanizer.md)
   │
   ▼  FINAL OUTPUT (the block at the bottom of this file)
```

## LAYER 1 — Scoring method (how to calculate)
Score the job 0–5 on each of four dimensions (20 total):
| Dimension | Judge |
|---|---|
| Fit & proof | Matches his stack? Real project to cite? (High by default — he can do any web/mobile job in his stack; see job-scoring.md "Capability assumption".) |
| Scope clarity | Clear + bounded, or vague/kitchen-sink? |
| Value alignment | Clears the $15 floor and pays fairly? |
| Client signals | Payment verified, rating, hire rate, spend, proposal count? |

**Verdict:** 17–20 = DRAFT NOW · 14–16 = APPLY · ≤13 = SKIP.
**Red flags (2+ = skip regardless):** unverified payment, low/again-terminated client, budget below floor, fake-example/false-claim gate, legal risk, spray-client pattern.
**Before writing:** (1) get the client's NAME from the recent-history reviews (a past freelancer's reply often names the client — use the CLIENT name, never the freelancer's); (2) pick the ONE best-matching real project from profile.md **following the PROJECT PRIORITY ORDER below**; (3) choose the opening angle from the job's real pain.

**PROJECT PRIORITY ORDER (hard rule — applies to every proposal):**
1. **⭐⭐ FLAGSHIP** tier in `profile.md` — the proper full production systems. Lead with these, and use one even if the job only overlaps it 1–2%.
2. **⭐ TOP PRIORITY** — only if nothing flagship fits.
3. **Secondary** — only if nothing above fits.
4. **Describe-only** projects (e.g. HelloDrew, Metanoa) are cited by name with **NO link** (their demos are down). Only ever paste URLs that actually work.
5. **⛔ RETIRED** projects are never used, linked, or mentioned in any form (currently Krigen AI).

## LAYER 2 — Proposal structure (exact format)
```
[Magic phrase on line 1 — ONLY if the job demands one, e.g. "AI Builder"]

Greeting            "Hi [Client name]," or "Hi there,"

HOOK (1–2 sent.)    Open on THEIR problem / the real risk, never a résumé line.
                    BEST-PROVEN FORM: name 2-3 specific production FAILURE MODES from
                    their own feature list (state advancing while a side-effect never
                    fired, two systems drifting apart, anything that fires twice), then
                    say how you build those paths. See references/winning-patterns.md.

PROOF (1–3 sent.)   ONE concrete, relevant project from profile.md, with a link.
                    Numbers and specifics beat adjectives.

CLOSE (1–2 sent.)   One specific, low-friction next step (a question or clear action).

Sign-off            Best regards,
                    Saad
```
Length 55–150 words (shorter wins). Answer any screening questions separately, one concrete line each.

## LAYER 3 — QA / humanize (must pass before output)
Score AI-tells 0–100 and rewrite until ≤10 (never show >15). Point-adders: banned word (+8), em/en dash (+6), "hope this finds you well"/"I'm a dev with X years" opener (+10), rule of three (+6), vague claim (+6), uniform sentence lengths (+8), missing greeting or sign-off (+6). Do a second pass: "what still sounds AI?" and fix it.

## Output format (what the user receives — always this block)
```
--- QUALIFICATION ---
Score: XX/20 (fit · scope · value · client) → VERDICT
Client signals + any red flags
Angle + proof chosen

--- PROPOSAL ---
[greeting → hook → proof → close → sign-off]

--- SCREENING ANSWERS ---   (only if the job has questions)

--- SUGGESTED BID ---
[amount + one-line rationale; never below the floor]

--- WHY THIS WINS ---
[2–3 bullets]

--- QA ---
AI-tell score: X/100 · word count · checks
```

## Non-negotiable rules (apply to every proposal)
1. Never fabricate a metric, client name, or project. Use only profile.md; else a bracketed placeholder, flagged.
2. Never skip for "no identical past project" — any web (front + back) or mobile/app job in his stack is his lane. Skips are for bad client / sub-floor budget / integrity gate / legal risk only.
3. Always greet at the top and sign off "Best regards, Saad".
4. No em/en dashes. Human tone, varied sentence lengths, contractions. Zero banned words (voice.md).
5. Obey any hidden magic phrase first (line 1).
6. Bid at or above the $15 floor; on expert jobs quote for value, never the low anchor. Individual-only jobs = apply solo, no "team"/"we".
7. Log every job to assets/applications.md (and outcomes to log.md) so the skill learns.
8. Match the job to the closest 2–3 real projects/links from profile.md.
```
