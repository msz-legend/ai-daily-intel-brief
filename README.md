# AI Daily Intel Brief

A Codex skill for concise, verified AI news briefs. It combines international reporting with Chinese public sources, distinguishes reporting from interpretation, and supports a separate 30-day community-context mode when explicitly requested. When briefs were skipped, it covers the gap as a declared catch-up window with per-item dates instead of pretending the gap was one day.

## Install

Clone the repository into the Codex skills directory:

```powershell
git clone https://github.com/msz-legend/ai-daily-intel-brief.git "$HOME/.codex/skills/ai-daily-intel-brief"
```

Restart Codex or start a new chat after installation. Invoke it with a request such as:

```text
$ai-daily-intel-brief Give me the latest China and global AI news.
```

## Requirements

- Codex or another agent host that supports `SKILL.md` skills.
- The `agent-reach` skill, used for web research and public-page verification.
- `last30days` is optional and is used only when a user specifically requests a 30-day trend or community-reaction view.

The skill never asks for social-media credentials or browser cookies merely to improve coverage.

## Verification Rules

- Prefer primary announcements, regulators, research institutions, and established reporting.
- Verify publication date and distinguish it from the event date; check first-publication date so resurfaced older stories are excluded.
- Use aggregators for discovery only; two aggregators repeating each other are one source, not two.
- Do not treat a search-result snippet as proof of a claim.
- Attribute company plans, forecasts, and community sentiment; tag vendor and self-reported numbers.
- Read release limitations (license, hardware or model support, missing components) before implying a complete production stack.
- Label drafts, leaks, and paywalled reports as unconfirmed.
- If community coverage is partial, state what succeeded and what failed; do not infer silence.

## License

[MIT](LICENSE)
