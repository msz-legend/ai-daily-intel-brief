---
name: ai-daily-intel-brief
description: "Produce a verified AI news brief that combines international and Chinese public reporting, with optional 30-day community context. Use for daily AI roundups, China-plus-global AI digests, and scheduled AI intelligence reports."
---

# AI Daily Intel Brief

Create a concise, fact-checked AI intelligence brief covering the requested date or time window. Treat Chinese and international reporting as complementary sources, not interchangeable evidence.

## Scope

- For a daily brief, use the previous calendar day in the client's timezone unless the user specifies another date.
- If the last delivered brief ended mid-day and days were skipped, cover the whole gap as one declared catch-up window (for example, `10-18 11:35 → 10-21 10:15`) and date every item by its event or first-report date. Do not present a multi-day catch-up as a single-day brief.
- For a trend brief, use the period explicitly requested. Do not substitute a 30-day community trend report for a daily news brief.
- Do not create or modify automations unless the user explicitly requests it.
- Keep the skill local while it is being tested. Do not create a repository, commit, or publish to GitHub until the user explicitly asks.

## Source Collection

1. Read and use the installed `agent-reach` skill before searching the web. State which agent-reach route is being used.
2. Prefer primary announcements and established reporting. Confirm publication date and distinguish a report date from the date of the event it describes.
3. Use aggregators (daily roundup pages, homepages, newsletters) for discovery only. Verify each headline against a primary source or independent reporting; two aggregators repeating each other are one source, not two.
4. Check first-publication date, not just the page's "updated" timestamp. A homepage or roundup can resurface an older story: if the first public date is outside the window, drop it even if it appears today.
5. A missing current-day roundup page is not evidence of a quiet day. If the page is absent or returns an error, fall back to primary feeds and search instead of reporting "no news".
6. For releases, read the boundaries as well as the features: license, supported hardware, supported models, and what the README explicitly excludes. For an inference or serving stack, check whether KV cache, prefill/decode disaggregation, load balancing, and multi-vendor support are actually included; report the missing pieces instead of implying a complete production stack.
7. Cover both perspectives when the request calls for China-plus-global coverage:
   - International: use at least two independently reported, high-signal items when the news warrants it. Reuters, major business outlets, company releases, regulators, and research institutions are typical sources.
   - China: use at least one directly relevant domestic source. Prefer official bodies, established Chinese media, company announcements, or industry outlets. Verify the original page with agent-reach's Jina Reader where possible.
8. Use agent-reach's Exa search when available. If it is rate-limited or unavailable, use the web route documented by agent-reach to locate public source pages, then retrieve the source article through Jina Reader. Do not invent a search result or treat search snippets as sufficient evidence.
9. Do not prompt for or read browser cookies, credentials, or social-media logins merely to improve coverage. Ask before any such access.
10. When a story rests on a paywalled report or an unannounced roadmap, label it as reported or unconfirmed ("据报道/未官宣") and do not promote it to a headline fact. A draft filing is not a public filing; say "draft prospectus" when that is what the source saw.

## Numbers and Claims

- Attribute every performance, price, revenue, and benchmark figure to its source and basis: company-reported (厂商口径/自报), independent test, filing, or analyst estimate.
- Give the comparison that makes a number interpretable (year-over-year, per unit, contract total, or denominator). Do not leave a sensational figure standing alone.
- For financial items, separate GAAP net loss from non-cash accounting charges and state the adjusted or operating basis when the source does. Do not repeat a headline loss without the accounting context.
- For open-source traction, query the GitHub API (stars, forks, created date, last push) instead of relying on a screenshot or a social post's claim.
- For benchmarks, say who ran them and whether the comparison is self-selected. Prefer independent leaderboards; flag vendor-run results. If only a vendor-provided article exists, label it single-source/vendor-run rather than presenting it as independent.

## Optional Community Context

Use the installed `last30days` skill only when the user requests community reaction, recent trend analysis, or a 30-day view. Read its `SKILL.md` and follow its own setup, consent, planning, and output rules.

- Community posts are sentiment and discovery signals. Do not present them as confirmation of material facts without corroborating reporting.
- If a platform is unavailable or partially covered, state the limitation briefly rather than inferring that it was quiet.
- A run can be partially successful: one keyword or platform may return data while another fails with a navigation or auth error. Report what was collected, name the failure, and stop after the documented retry budget instead of hammering the platform.
- Keep engagement numbers attached to the posts you cite (likes, views, replies) so the reader can judge representativeness; quote the strongest technical criticism as well as the praise.

## Synthesis

- Lead with the few developments that materially changed product capability, commercial demand, infrastructure, regulation, or deployment.
- Include a China-specific development when Chinese coverage is requested, explaining its implication rather than merely listing a statistic.
- Separate verified reporting from interpretation. Attribute company claims, forecasts, and community opinions.
- Use compact sections or bullets that fit the requested cadence. Link claims inline; do not append an uncurated link dump.
- Keep non-AI engineering news out of AI headlines. If it is materially useful to the reader (for example, a critical runtime CVE or a CA revocation), put it in a clearly separate "工程提醒" line.
- End with a one- or two-sentence cross-market takeaway that identifies the shared trend and any meaningful difference between China and international markets.

## Verification Before Delivery

Run this checklist before sending:

- Every headline has an in-window event date and at least one primary or independent source; headline claims have two independent sources where available.
- The first-publication date was checked; resurfaced older stories were removed.
- Vendor and self-reported numbers are tagged and not phrased as independent fact.
- Release limitations (missing components, hardware or model support, license) are stated when they change the conclusion.
- Drafts, leaks, and paywalled reports are labeled as such.
- Community coverage states which platforms and keywords succeeded and which failed; no silence is inferred from missing data.
- Duplicate stories are merged; thin evidence yields a shorter brief with an explicit coverage gap.
