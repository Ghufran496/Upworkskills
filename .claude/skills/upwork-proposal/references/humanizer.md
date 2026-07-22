# Layer 3 — Humanizer QA pass (AI-tell scoring)

Every proposal gets scored and cleaned before Saadullah sees it. Goal: reads like a sharp human typed it in 90 seconds, not like ChatGPT. Based on the blader/humanizer 33-pattern set + Aboudjem 0–100 scoring, tuned for short Upwork proposals.

## ⛔ MANDATORY FINAL GATE — do this LITERALLY every time, never rubber-stamp
Before showing ANY proposal or screening answer, character-scan the ENTIRE output text for these three things. This is a real check you perform, not a label you attach:
1. **Em dash `—` and en dash `–`** — scan for the actual characters. If ANY appear, replace each with a period, comma, colon, or a reworded sentence, then scan again. A hyphen in a compound word (e.g. "full-stack", "real-time") is fine; the — and – punctuation dashes are NOT.
2. **Banned words** from `voice.md` — scan for each. Zero allowed.
3. **Greeting + "Best regards, Saad" sign-off** — both present.

**You may NOT write the QA line "no em/en dashes" (or any AI-tell score) unless you have literally just scanned the final text for the `—` and `–` characters and confirmed zero.** If you did not scan, do not claim it. Rubber-stamping this line is a process failure — the whole point of this layer is that the claim is earned, not assumed. If a dash slips through, the QA was fake.

## Two-pass process
- **Pass 1 — Rewrite:** scan for the patterns below, fix each, keep meaning + length.
- **Pass 2 — Audit:** ask "what still sounds AI here?", fix what's left, then run the MANDATORY FINAL GATE above (literal character scan for —, –, banned words) before output.

## AI-tell score (0–100 — lower is better)
Start at 0, add points for each tell present in the proposal. **Target ≤10. If >15, rewrite before output — do not show Saadullah a proposal above 15.** Report the score in the QA note.

| Tell | Points each |
|---|---|
| Any banned word/phrase from `voice.md` | +8 |
| Em-dash or en-dash used at all in a proposal | +6 |
| Opens with "I hope this…", "I came across…", "As a [role] with X years…" | +10 |
| Rule of three ("fast, reliable, and scalable") | +6 |
| Negative parallelism ("not just X, it's Y") | +6 |
| Superficial -ing phrase faking depth ("leveraging cutting-edge…") | +6 |
| "From X to Y" false range | +5 |
| Generic upbeat closer ("Looking forward to hearing from you") | +6 |
| Over-hedging ("I believe I could possibly…") | +5 |
| Copula avoidance ("serves as", "boasts", "stands as") | +4 |
| Uniform sentence lengths / no burstiness (3+ similar-length sentences in a row) | +8 |
| Signposting ("Let's dive in", "Here's what you need to know") | +5 |
| Vague claim with no number/specific ("high-quality solutions") | +6 |
| Sycophantic filler ("I'd be absolutely thrilled") | +4 |
| Emoji beyond at most one (and only if job tone is casual) | +5 |
| No specific client detail in the first HOOK sentence (the line after the greeting) | +8 |
| Missing greeting line or missing sign-off | +6 |

## The tells that matter most for proposals (fix on sight)
1. **Self-intro opener** — never start with yourself. Start with their problem.
2. **Banned words** (`voice.md`) — zero tolerance.
3. **Em dashes** — replace with periods or commas.
4. **Uniform rhythm** — vary sentence length hard. A 6-word sentence next to a 20-word one. Use a fragment.
5. **Vague adjectives instead of numbers** — "robust app" → "app that handled 10k users." Pull the number from `profile.md`.
6. **Generic closer** — replace with a specific next step.

## Required structure (not penalized — these are expected)
A greeting line ("Hi [name],") and a sign-off ("Best regards, Saad") are REQUIRED and never count as AI-tells. Only the cliché forms are penalized: "I hope this message finds you well" (greeting) or a next-step replaced by "Looking forward to hearing from you" (close). A clean "Best regards, Saad" is fine.

## Human-texture moves (add lightly, don't overdo)
- One contraction-heavy, slightly informal line.
- A concrete, checkable detail only someone who read the post would write.
- Occasionally start a sentence with "And" or "So" — humans do.
- One short fragment for rhythm. Like this.

## Output of this layer
A cleaned proposal + a one-line QA note: `AI-tell score: X/100 (cleaned)`. The QA note may only state "no em/en dashes" after the literal character-scan in the MANDATORY FINAL GATE was actually done. If you couldn't get below 10, say why. Never emit a QA note you did not earn by scanning.
