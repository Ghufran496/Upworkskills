# Upwork MCP — setup + outcome backfill plan

## Status
NOT CONNECTED as of 2026-10-02. No Upwork entry exists in `.mcp.json`, project
settings, or `~/.claude.json` (only `trigger` is configured there).

## Setup (user must do this; OAuth cannot run in a non-interactive session)
1. Open the Upwork email ("Upwork now has an MCP server") and click **Connect Upwork**.
   That flow is the authoritative source of the endpoint URL and scopes. Do not guess a URL.
2. In an INTERACTIVE Claude Code session in this folder, add it via `/mcp`, or:
   `claude mcp add --transport http upwork <url-from-upwork>`
3. Approve the OAuth prompt in the browser.
4. Verify tools are live, then run the backfill below.

## Why this matters more than new features
`assets/applications.md` holds 117 logged rows, 56 of which are real APPLICATIONS,
dating back to 2026-07-03. Almost every result column still reads "applied".
The self-correction loop in SKILL.md ("before writing in a niche you've logged, read
those rows and lean toward openers that got replies") has therefore NEVER fired with
real data. The pipeline has been reasoning from priors since July.

## Backfill procedure (run once connected)
For each of the 56 application rows, oldest first:
1. Match the logged job title/date to the real proposal via the MCP's proposal or
   message history. Title wording in the log is abbreviated, so match on date + client
   + stack rather than exact string.
2. Pull the true terminal state: viewed / no view / replied / interviewed / hired /
   declined / job closed-hired-elsewhere / expired.
3. Rewrite ONLY the final `result` field of that row. Never alter the score, verdict,
   angle, bid or reasoning fields; those are the independent variables being tested.
4. Where a reply exists, append a short `reply:` note with what the client actually said.

## The questions the data should answer
Once results are in, analyse and write findings into `references/winning-patterns.md`:
- **Hook type vs reply rate.** Failure-modes hooks (Lee, Mandi, Nordic fintech) versus
  scoping-question hooks (Yerevan, Prolific) versus honest-disclosure hooks (sandbox
  lead, luxury OTA). Which actually gets opened and answered?
- **Score calibration.** Do 17-19/20 rows convert better than 13-14/20 rows? If not,
  the scoring rubric is decorative and needs re-weighting.
- **Bid-vs-client-average.** Rows where the bid exceeded the client's historical average
  (Web Forms $22 vs $12.19, Austin $40, healthcare $55) versus rows that matched it
  (Cape Town $20). Does bidding above the average cost replies?
- **Proposal-count threshold.** Traction so far has come from posts with <5 to 10
  proposals (Mandi -> offer in 19 min, Nordic <5, Austin <5). Confirm or kill that rule.
- **Honest disclosure.** Rows where a gap was named outright (no Lovable, no Stripe
  Connect Express, no MAUI, no luxury animation portfolio). Did candour help or hurt?

## Layer 0 / Layer 4 (add to the pipeline once the MCP is proven)
- **Layer 0 FETCH** — before qualifying: pull client spend/hours/avg-rate/hire-rate,
  proposal count, and boost-auction state. AUTO-REJECT on eligibility gates (Location,
  English level) before anything is written. 12 jobs died on gates this session and 1
  (Cape Town, 18/20) was written before the 550-Connect boost war was visible.
- **Layer 4 LOG** — after sending: write the row automatically, then poll periodically
  for state changes and update the result field without being asked.

## Guardrails
- The MCP FEEDS the pipeline; it does not replace it. Never let a generic
  auto-drafted proposal go out. What won Lee (1 of 187) and Mandi (offer in 19 minutes)
  was specific diagnosis, which only Layers 1-3 produce.
- Read-only to start: search, client history, messages, contracts. Do NOT enable
  proposal submission until the backfill has proven the data is accurate.
- Saad keeps the final send. The Cape Town form shipped a $25 default rate against a
  $15-20 budget; a human check catches that, an automated send does not.
