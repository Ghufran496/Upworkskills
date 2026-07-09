# Layer 1 — Job qualification & risk (Upwork Seller Assistant layer)

Run this BEFORE writing any proposal. Purpose: don't waste connects on low-quality or high-risk jobs, and enter the writing layer with a clear angle + the right portfolio piece already chosen. Based on the dvcrn "Upwork Seller Assistant" capabilities (risk assessment, budget/client-rating filtering, portfolio matching, application tracking, A/B testing).

## Step 1 — Read client signals (from the job post / client panel)
Pull whatever is visible and note it:
- Payment verified? (unverified = big risk)
- Client total spend / hires / avg rating / reviews given
- Member since / recent activity
- Number of proposals already submitted (fewer = better; <5 on a fresh post is ideal)
- Hire rate (jobs posted vs hires)

## Capability assumption (read before scoring FIT)
Ali has 5+ years and has shipped 50+ projects across web (frontend + backend), mobile apps, SaaS, AI/ML, e-commerce, fintech, Web3, healthcare, and enterprise. **Assume he CAN do any web or mobile project** built with mainstream languages/frameworks/tools. Do NOT lower the FIT score or lean skip just because there's no near-identical past project — if it's web (front or back end), mobile, or app development in his stack, treat it as within his ability and frame the proposal as "yes, I've done this / this is my lane." Reserve low FIT scores for genuinely out-of-scope work: pure graphic/brand design with no dev, a proprietary no-code platform he'd need a portfolio in (e.g. Duda) where the client demands platform-specific examples, or non-software work. Skips should be driven by CLIENT quality, budget-below-floor, integrity gates (fake examples/false claims), or legal risk — NOT by "hasn't done this exact thing."

## Step 2 — Score the job (0–5 each, 20 max)
| Dimension | 0–5 — what to judge |
|---|---|
| **Fit & proof** | Does it fall within Ali's skill set in `profile.md` (web, mobile, cloud, DB, AI — he covers the full stack)? Do we have a real or adjacent proof point for it? Direct proof = 5; skill present but only adjacent proof = 3–4. |
| **Scope clarity** | Is the deliverable clear and bounded, or vague/kitchen-sink? |
| **Value alignment** | Budget vs effort — does it clear Ali's floor and reward outcome pricing? |
| **Client signals** | Payment verified, good history, active, reasonable proposal count |

**Verdict:**
- **17–20 → DRAFT NOW** (high-quality, apply early)
- **14–16 → LATER TODAY** (decent; apply if capacity)
- **≤13 → SKIP** (tell Ali why in one line; don't write it)

Always state the score breakdown and verdict before the proposal. If Ali says write it anyway, write it.

## Step 3 — Risk red flags (2+ flags = recommend skip)
- Unverified payment
- Vague scope with many unrelated goals ("need everything")
- Free/unpaid test task requested
- Budget far too low for the complexity
- Mentions wanting to bypass AI detection, fake reviews, or anything sketchy
- Client has posted many jobs with 0 hires, or long inactivity, or poor ratings given
- "Urgent" + tiny budget + huge scope (classic churn client)
One flag can be fine. Two or more → say "I'd skip this, here's why" unless Ali insists.

## Step 4 — Portfolio match (feeds the Proof line in Layer 2)
Pick the ONE most relevant item from `profile.md` proof bank for this exact job:
- MVP build / turn UI or design into a working app → Peepeep MVP ($4,000); HTML UI → functional MVP ($2,000)
- E-commerce / marketplace / multi-vendor → Multi-vendor MERN platform; Solo-vendor (.NET & React) store
- Fintech / real estate / investment platform → Kudo Property (fractional real-estate)
- Rescue / hard bug / "other devs couldn't fix it" → weekend Next/Node bug rescue; reputation for finding bugs others miss
- Urgent bug fix / Azure → Azure App Insights & Service Bus same-day fix
- AWS / Node backend → AWS Node.js job; MEAN-stack back-end
- Front-end / Figma → responsive landing page from Figma
- SaaS / dashboards / RBAC / APIs → SaaS platform + REST/microservices + RBAC background (DevsComet lead)
- Mobile (React Native / Flutter) → Flutter certification + cross-platform capability; bridge from React product work
- AI / LLM → claimable + AI-assisted workflow, but NO flagship AI project — bridge honestly from integration work; don't fake a headline AI product
Hand this chosen item to the writing layer. Ali claims the full skill set, but the PROOF must be real or a clearly-adjacent project — never invent a metric or client.

## Step 5 — Pick the angle / template (YedanYagami keyword routing)
Map job keywords → opening angle so the hook lands:
| Job keywords | Angle |
|---|---|
| AI, LLM, OpenAI, Claude, chatbot, speech | Lead with the AI integration proof + a sharp technical question |
| agent, orchestration, multi-service | Lead with architecture/scalability |
| dashboard, admin, CRM, internal tool | Lead with "I've shipped multi-role dashboards end-to-end" |
| marketplace, multi-tenant, platform | Lead with Deal Junkie / Unifaires platform outcome |
| rescue, fix, previous dev, legacy | Lead with audit-first, de-risk phase 1 |
| .NET, Blazor, C#, ASP.NET | Lead with .NET depth (many devs on Upwork are JS-only) |

## Step 6 — Log the application (tracking + A/B)
After qualifying + writing, record it in `assets/applications.md` so we track response rates and can A/B test openers. Then also prompt the outcome log (`log.md`) once a reply/hire/ghost happens.

## Batch mode
If Ali pastes several jobs, score them all first, rank by score, and only draft the ones ≥14 — highest first. Report the skip list with one-line reasons.

## Agent mode (when driven by the upwork-agent daemon)
The citizenweb3/upwork-agent scores jobs 0–10 and sends anything ≥4 to Telegram for human triage. When running inside that agent:
- Also emit a **0–10 score = round(our 0–20 score ÷ 2)** so the daemon's threshold and reports work.
- Mapping: 17–20 (≈9–10/10) = strong, apply; 14–16 (7–8/10) = decent; ≤13 (≤6/10) = weak. The daemon still forwards ≥4/10 so Ali can eyeball borderline ones via the Telegram buttons.
- On "Apply", run the full write pipeline (L2 + L3). On "Redo", generate a genuinely different angle (swap the opener/proof), not a reword.
- Keep the proposal to 55–120 words — it's going straight into Upwork's box.
See `AGENT_INTEGRATION.md` at the workspace root for wiring.
