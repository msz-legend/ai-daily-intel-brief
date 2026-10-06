---
name: ai-daily-intel-brief
description: "Produce a verified AI news brief that combines international and Chinese public reporting, with optional 30-day community context. Use for daily AI roundups, China-plus-global AI digests, and scheduled AI intelligence reports."
---

# AI Daily Intel Brief

Create a concise, fact-checked AI intelligence brief covering the requested date or time window. Treat Chinese and international reporting as complementary sources, not interchangeable evidence.

## Scope

- For a daily brief, use the previous calendar day in the client's timezone unless the user specifies another date.
- For a trend brief, use the period explicitly requested. Do not substitute a 30-day community trend report for a daily news brief.
- Do not create or modify automations unless the user explicitly requests it.
- Keep the skill local while it is being tested. Do not create a repository, commit, or publish to GitHub until the user explicitly asks.

## Source Collection

1. Read and use the installed `agent-reach` skill before searching the web. State which agent-reach route is being used.
2. Prefer primary announcements and established reporting. Confirm publication date and distinguish a report date from the date of the event it describes.
3. Cover both perspectives when the request calls for China-plus-global coverage:
   - International: use at least two independently reported, high-signal items when the news warrants it. Reuters, major business outlets, company releases, regulators, and research institutions are typical sources.
   - China: use at least one directly relevant domestic source. Prefer official bodies, established Chinese media, company announcements, or industry outlets. Verify the original page with agent-reach's Jina Reader where possible.
4. Use agent-reach's Exa search when available. If it is rate-limited or unavailable, use the web route documented by agent-reach to locate public source pages, then retrieve the source article through Jina Reader. Do not invent a search result or treat search snippets as sufficient evidence.
5. Do not prompt for or read browser cookies, credentials, or social-media logins merely to improve coverage. Ask before any such access.

## Optional Community Context

Use the installed `last30days` skill only when the user requests community reaction, recent trend analysis, or a 30-day view. Read its `SKILL.md` and follow its own setup, consent, planning, and output rules.

- Community posts are sentiment and discovery signals. Do not present them as confirmation of material facts without corroborating reporting.
- If a platform is unavailable or partially covered, state the limitation briefly rather than inferring that it was quiet.

## Synthesis

- Lead with the few developments that materially changed product capability, commercial demand, infrastructure, regulation, or deployment.
- Include a China-specific development when Chinese coverage is requested, explaining its implication rather than merely listing a statistic.
- Separate verified reporting from interpretation. Attribute company claims, forecasts, and community opinions.
- Use compact sections or bullets that fit the requested cadence. Link claims inline; do not append an uncurated link dump.
- End with a one- or two-sentence cross-market takeaway that identifies the shared trend and any meaningful difference between China and international markets.

## Verification Before Delivery

Check that each included item has a credible source, an in-window date, and a clear reason for inclusion. Remove duplicate stories and uncorroborated claims. If the evidence is thin, return a shorter brief and name the coverage gap.
