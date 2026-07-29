# Winning patterns — proven from real client feedback

Real wins, with the client's own words on WHY. This file exists because a client explained his reasoning in detail, which is rare and worth copying.

## ⚠️ These are TOOLS, not a template — use judgment
Do NOT force a pattern onto every job. Pick the hook that actually fits the job in front of you. A failure-modes hook on a brochure-site job would read as absurd and lose the bid.

**Use the failure-modes hook WHEN the job involves:** production systems with real users, payments/billing, third-party integrations or webhooks, data sync/reconciliation, multi-step workflows with state, "fix/stabilize/rescue our app", inherited codebases, anything where correctness matters more than looks.

**Do NOT use it when the job is:** a marketing/brochure site, a landing page, Figma-to-HTML implementation, design-led or animation-led work, SEO, a small one-off fix, or anything where the client's real concern is aesthetics, speed of delivery, or cost. There, the right hook is about THEIR actual priority (conversion, pixel accuracy, launch speed, ease of self-updating). See `structure.md` for hook patterns generally.

The transferable principle across every job type is not "talk about failures", it is: **open on the thing this specific client is actually worried about, in concrete terms only an experienced person would use.** For a payments platform that is silent billing drift. For a landing page it might be conversion or pixel fidelity. For a rescue job it is not breaking what works.

---

## WIN #1 — "Failure modes, not features" (Lee Yanik, vet-imaging SaaS workflow platform, Jul 2026)

**Result:** Shortlisted out of **187 proposals** (173 never even opened). Moved straight to next stage. Client's average paid rate: $56/hr.

**What the client actually said:**
> "I reviewed a large number of applicants, and yours stood out because you focused on **workflow integrity rather than just technology**."
> "Your comments about billing failures, PDF consistency, and Stripe webhook handling showed me that you've **worked on real production SaaS applications, not just built features**."

### The pattern that won it (reuse this)
**Name the specific ways the system fails in production, not the features you can build.**

The winning hook was three concrete failure modes drawn from the client's own feature list:
- "a case that reaches 'report delivered' while billing never fired"
- "a PDF that renders differently than what the vet approved"
- "a Stripe webhook that double-posts"

Then one line of stance: *"I build those paths so they fail loudly and reconcile cleanly."*

**Why it works:** anyone can claim a stack. Only someone who has run a system in production knows what *silently breaks*. Naming those failures is unfakeable proof of experience, and it instantly separates you from the 90% who write "I have 5+ years in React/Node."

### How to generate the failure-mode hook for any job
1. Read the client's feature list (e.g. cases, reports, PDF, billing, Stripe, QuickBooks).
2. Ask: **where do these features touch each other?** The seams are where production breaks.
3. Pick 2–3 seam failures that are specific, plausible, and embarrassing if they happened:
   - state that advances while a downstream side-effect never fired (billing, email, sync)
   - two systems that drift out of agreement (DB vs Stripe, preview vs export, app vs accounting)
   - anything that can fire twice (webhooks, retries, queues) or partially write
   - a document/number the client shows a customer that turns out wrong
4. State how you handle them: fail loudly, idempotent handlers, reconcile, append-only ledger.

**Domain examples that transfer:**
- E-commerce: order marked paid but inventory never decremented; refund not reflected in ledger
- Booking: slot double-booked under concurrent requests; cancellation without refund
- Auctions: race conditions on simultaneous bids; last-second bid lost
- Video/media: preview does not match final export
- Data platforms: sync marked complete on partial write; reconciliation drift
- Any payments work: webhook double-post, subscription state drift, proration mismatching the invoice

### Other elements that contributed (keep doing these)
- **Magic phrase first** ("Radiology" on line 1) — cleared the read-check gate.
- **Two FLAGSHIP proofs mapped 1:1 to his two hardest asks** (Cirqley billing portal → billing workflow/admin; Ad Submission Portal → Stripe + third-party integration), each with *what Saad personally built*, exactly as the post demanded.
- **Honesty about a gated link** ("login-gated") instead of pretending it was browsable. Builds trust, costs nothing.
- **"I would rather execute against your spec than re-litigate it"** — mirrored the client's stated wish for execution over discovery.
- **One sharp scoping question** (QuickBooks Online vs Desktop; invoice created in QBO or synced after Stripe collects) — a question only someone who has done the integration would ask.
- **Bid $20/hr on a $25-45 posting.** NOTE: this won attention but was UNDER-priced for a client paying $56/hr avg. Next time bid $40-45. Do not repeat the low anchor.

### Follow-through that kept it alive (the conversation matters as much as the proposal)
- **Truncated message:** he cut off mid-sentence; Saad said so plainly and asked him to resend, while still stating what he would prepare. Never guess and prepare the wrong thing.
- **Unpaid evaluation announced:** accepted warmly, then asked two professional questions (expected time/deadline, design-only or working code). Result: client volunteered a fair scope (2–4 hrs, 3 days, design and reasoning, explicitly not production work). Asking scope questions read as senior, not reluctant.
- **Reinforced the strongest card while waiting:** sent a short unprompted note on production Stripe multi-tenant billing (prorations, subscription state drift, double-fired webhooks) and offered to screen-share. This doubled down on exactly what won the shortlist.
- **Brevity when the client has already decided.** Once he set the process, the reply was ~75 words. Long replies at that stage add nothing.

---

## Distilled rules
1. **Open on what THIS client is actually worried about, in concrete terms.** For production/payments/integration work that means failure modes (highest-leverage move found so far). For design/marketing work it means conversion, pixel fidelity, or launch speed. Match the hook to the job, never force one pattern.
2. **Prove experience through specificity.** "Webhooks that fire twice" beats "experience with Stripe." Same principle applies elsewhere: "if Figma says 24px it is 24px" beats "pixel-perfect."
3. **Map each proof to a named client requirement**, and say what YOU personally built.
4. **Be honest about gaps and gated links.** It reads as confidence and it survives interviews.
5. **Ask one question only an experienced person would ask.** It doubles as proof.
6. **Mirror the client's stated priority** in their own words (execution vs discovery, quality vs speed).
7. **Do not under-bid a client who pays well.** Check their avg-paid rate and bid near it.
