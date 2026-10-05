# Saved searches — the only terms to hunt jobs with

Saad's own 30 saved searches on Upwork (captured 2026-10-05). **Use these terms when
searching for work for him via the MCP.** Do not invent other search terms; these are
what he has decided is relevant.

## THE LIVE LIST — 30 saved searches as of 2026-10-05
Upwork caps saved searches at **30** and job alerts at **3**. The list below is what is
actually configured on the account. When hunting jobs for Saad, use these terms.

**Mobile (11)**
react native · react native developer 🔔 · react native typescript 🔔 · react native node 🔔 ·
flutter · flutter developer · flutter firebase · flutterflow · mobile app developer ·
cross platform mobile · ios android

**React / Next.js (4)**
react js next js · next.js tailwind · react typescript · nextjs supabase

**Node / backend (5)**
nestjs · node postgres · backend developer · full stack developer react node · javascript developer

**MERN (3)**
mern developer · mern stack developer · mean mern

**Data (2)**
postgresql · supabase

**.NET (1)**
asp.net core

**Generalist (4)**
typescript · saas · front end developer · website developer

🔔 = job alert ON (Upwork allows only 3)

### Wanted but blocked by the 30-cap
- **.net developer** — facet counts show **247 payment-verified jobs, 16 at <5 proposals,
  19 at 5-10**. Strongest unclaimed term, and .NET is Saad's best-converting niche
  (Mandi/Harbor Farm, Cerifi, USP, SelfRep, Policy Management). Add it by cutting
  `website developer`, `full stack developer react node` or `ios android`.
- Nothing covers **Angular** (in his profile headline, Cerifi + Policy Management proof)
  or **Stripe / API integration**, both recurring win areas.

### Cap behaviour (observed 2026-10-05)
Deleting a search then refreshing shows 30 again — Upwork appears to BACKFILL the freed
slot from search history rather than restoring the deleted term (`nest.js` and `mean stack`
stayed deleted; `front end developer` and `full stack developer react node` reappeared).
Saving a 31st fails with "Failed to save search". To add one, delete and save in the same
session without refreshing.

## How to run them through the MCP

`find_jobs action=search` with the term in **`title`** (not `query`) to cut noise —
`title` matches the job title only, so every result actually names the role. `query`
does semantic expansion across the whole posting and drags in unrelated work, which is
exactly what makes the web saved-search feed noisy.

**Always pair the term with these filters:**
```
title: "<term>"              # 1-3 key words; terms are ANDed and stemmed
job_type: "hourly"           # or omit to include fixed
proposals_max: 5             # early position only; traction has all come from <5-10
verified_payment_only: true
rate_min: 25                 # see caveat below
sort: "recency"
limit: 10
```

**Caveats learned in use:**
- `title` CANNOT be combined with `query` or `sort=relevance` — both are refused.
- `rate_min` is an OVERLAP filter, not a floor: `rate_min=25` keeps any job whose posted
  MAXIMUM is >= 25, so "$10-$30/hr" still comes back. Filter the real floor client-side.
- `limit` is capped at 10. Page with `cursor` from `pageInfo.endCursor`.
- Multi-word titles are ANDed, so long phrases match nothing. "full stack developer react
  node" as a title returns little; split it or use `skills` instead.
- Saad is on **Freelancer Plus**, so search returns EXACT `proposal_count`, not the
  "20 to 50" tier the web UI shows.

## Then always pull the client record before scoring
`find_jobs action=get` on anything that survives. The search row does NOT carry the
hiring record. `get` returns:
- `client_record` — hires, **jobs_with_hires**, hire_rate_percent, spend, hours, feedback
- `client_feedback` — up to 5 reviews freelancers wrote ABOUT the client
- `preferred_qualifications` — location, English level, contractor type (the gates)
- `activityStat.jobActivity` — invitesSent, totalHired, totalOffered for THIS posting
- `connects_cost`, `applied`

**This is the step that changes verdicts.** A .NET job on 2026-10-05 looked like a strong
early-position find (4 proposals, $20-60/hr, exact stack) until `get` showed
`jobs_posted: 15, jobs_with_hires: 0, hire_rate_percent: 0` with 28 invites already out.

## AUDIT of the web/full-stack terms (tested live via MCP, 2026-10-05)

Each term below was run through `find_jobs action=search` with `title` and `sort=recency`
and the results read. Verdicts are from what actually came back, not guesswork.

### ⛔ REMOVE — these return junk
| Term | What it actually returned |
|---|---|
| **web** | Cold-calling appointment setters, Shopify SEO, a DRONE PILOT for construction footage, QA testers. One word is far too broad. |
| **web browser** | A LOGO DESIGN job for a browser called RatNAV, a Wix redesign, web-scraping-with-proxy, cross-browser QA testing. 5 results in 3 weeks, zero relevant. |
| **html css** | Almost entirely ENTRY LEVEL: a $10 "fix a minor CSS issue" (62 proposals), a $30 beginner asking for tutoring, a $34 Caspio low-code job. 3 of 5 tagged entry_level. Attracts bottom-of-market work and drags the feed down. |

### ⚠️ KEEP BUT DEPRIORITISE — high volume, brutal competition
| Term | Evidence |
|---|---|
| **asp.net core** (new) / **.net developer** | All senior, no junk, but proposal counts were 29, 71, 114, 176. Real work, crowded field. Always pair with `proposals_max`. |
| **website developer** | Overlaps "web developer" territory; tends toward small brochure sites. Keep only if paired with filters. |

### ✅ ADD — tested and strong
| Term | Evidence from the live run |
|---|---|
| **typescript** | With `proposals_max=10` + `verified_payment_only`: 4 results, ALL 6-8 proposals, all senior (fintech React/Node/AWS, Snowflake RBAC platform, full-stack TS storefront). Best signal-to-noise of any term tested. |
| **asp.net core** | Narrower and more senior than bare ".net developer". |
| **nextjs supabase** | Saad's recommended stack pairing (see [[feedback-recommend-custom-stack]]). |
| **react typescript** | Same combination logic that works for mobile. |
| **node postgres** | Backend pairing; combination terms consistently surface lower-proposal jobs. |

### THE PATTERN THAT MATTERS
**Single generic words are crowded and noisy. Two-word stack combinations are not.**

Measured on 2026-10-05:
- `react native` alone -> jobs at 116, 56, 41, 39, 38 proposals
- `react native node` -> jobs at **10** and **15** proposals, same quality, $20-40/hr
- `typescript` + filters -> 4 jobs, all at **6-8** proposals

Why: most applicants are single-discipline. Saad is full-stack AND mobile, so the
combination terms match a much smaller candidate pool. **Lead with combinations.**

## Mobile terms (added 2026-10-05)
**Tier 1 volume:** react native · flutter · mobile app developer
**Tier 2, lower competition (lead with these):** react native node · react native typescript ·
react native developer · flutter firebase · flutter developer · cross platform mobile ·
flutterflow · ios android

**Do NOT add bare "expo"** — tested, and over half the results were trade-show
videographers, expo attendee-list scraping and K-Beauty Expo sourcing reps. Only works
paired, as "react native expo".

## ROUND 2 AUDIT — remaining web terms (tested live, 2026-10-05)

### ⛔ REMOVE — dead or wrong-domain
| Term | Evidence |
|---|---|
| **mean mern** | **ZERO RESULTS.** Upwork returned `empty_reason: filters_no_match`. Nobody writes both acronyms in one title. Delete. |
| **sql database** | DBA and spreadsheet work, not app development: "Restore SQL Backup File" (96 proposals), "Help Create SQL Database and Connect to Excel" (122 proposals), MS SQL performance tuning. Wrong discipline. |
| **full stack mern** | Only 5 results in 5 WEEKS, and the budgets were $10, $50, $10. Thin and cheap. "mern stack developer" covers the same ground better. |

### ⚠️ KEEP BUT EXPECT A CROWD
| Term | Evidence |
|---|---|
| **full stack developer react node** | Works despite being 5 words, but proposal counts were 124, 173, 51, 38. Real jobs, brutal field. Always pair with `proposals_max`. |
| **asp.net core** | All senior, zero junk, but counts of 29, 71, 114, **176**. |

### ✅ CONFIRMED STRONG
| Term | Evidence |
|---|---|
| **next.js supabase** | Best web term tested. 6 results in 5 days: a $750 security audit on a Claude-Code-built app (**14 proposals**), a French-language React/Next/Supabase role (**13 proposals**), a $5,500 legaltech build. Directly matches [[feedback-recommend-custom-stack]]. |
| **typescript** + filters | 4 results, ALL at 6-8 proposals, all senior. |

### 🔤 STEMMING NOTE
`nextjs supabase` and `next.js supabase` return **IDENTICAL** results — Upwork stems the
dot away. No need to keep both spellings of the same term. Same likely applies to
`nest.js`/`nestjs`, so one of that pair is redundant.

### ❌ TESTED AND REJECTED (do not add)
| Term | Why |
|---|---|
| **saas** | A sales-role magnet: cold callers, B2B appointment setters, lead generation, and a Lottie animator. Almost no engineering. |
| **expo** | Trade-show videographers, expo attendee scraping, K-Beauty sourcing reps. |
| **web**, **web browser**, **html css** | See Round 1 audit above. |

## ⚠️ CORRECTION — MCP `title` SEARCH IS NOT THE SAME AS UPWORK WEB SEARCH (2026-10-05)

**The Round 1 and Round 2 audits above over-reached, and two deletions were WRONG.**

### The mistake
MCP `find_jobs action=search` with **`title`** matches the JOB TITLE ONLY.
Upwork's own web search (`upwork.com/nx/search/jobs?q=...`) matches the **WHOLE POSTING**:
title + description + **skill tags**.

So "zero results" from a `title` search means only "no job TITLE contains these words."
It does NOT mean the term is dead on Upwork.

### Proven counter-examples
| Term | My `title` test said | Upwork web search actually shows |
|---|---|---|
| **mean mern** | ZERO results, "delete it" | **146 jobs** (114 payment-verified). Top hits were a full-time React/Next/NestJS role with wallets+ledgers+reconciliation, a $10,000 Lead Developer & Architect post, and the Romania React/Next/Node/Stripe/OpenAI job. The acronyms live in the **skill tags** (`MERN Stack`), never the title. **KEEP IT.** |
| **saas** | "sales-role magnet, do not add" | **3,032 payment-verified jobs**, incl. **467 with fewer than 5 proposals**. The sample I pulled happened to be top-heavy with sales roles; at that volume the engineering work is obviously present. **KEEP IT.** |

### Rules going forward
1. **A saved search on Upwork behaves like `query`, not `title`.** When judging a saved-search
   TERM, use `query` (whole-posting match) or check the web count. Reserve `title` for cutting
   noise when hunting a specific role right now.
2. **Never call a term dead from a `title` search alone.** Acronyms and stack names
   (MERN, MEAN, Supabase, NestJS) usually appear in SKILL TAGS, which `title` cannot see.
3. **Do not generalise from 10 results on a high-volume term.** `saas` has 3,000+ jobs; a
   single page of 10 says nothing about the other 2,990.
4. Upwork's web UI exposes **proposal-count buckets as facet counts** ("Fewer than 5 (467)").
   That is a faster way to judge a term's quality than reading individual rows.

### Deletions that still stand (weak relevance, not zero volume)
- **web**, **web browser** — returned drone pilots, logo design, cold callers. Too broad in
  any mode.
- **html css** — real volume, but dominated by $10-30 entry-level fixes.
- **sql database**, **full stack mern** — the returned work was DBA/spreadsheet and cheap
  respectively. Lower confidence than the two above; check the web facet counts before deleting.
