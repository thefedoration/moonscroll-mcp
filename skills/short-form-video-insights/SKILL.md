---
name: short-form-video-insights
description: >-
  Research and analyze short-form video on Instagram Reels, TikTok, and
  YouTube Shorts via the Moonscroll remote MCP. Use when the user asks about
  trends, creators, hooks, formats, competitors, or performance signals for
  short-form social video.
---

# Short-form video insights (Moonscroll)

## When to use

- Trend or niche research on Instagram Reels, TikTok, or YouTube Shorts
- Creator or competitor briefs grounded in public short-form content
- Ideation for hooks, formats, captions, or posting angles
- Summarizing themes, formats, or engagement patterns across a set of videos

## Prerequisites

- Moonscroll MCP connected as a **remote** server at `https://api.moonscroll.ai/mcp`
- Prefer tools exposed by the live MCP session over guessing names or parameters
- If auth is required, complete the client OAuth / token flow first — never invent API keys

## Workflow

1. **Clarify the ask** — platform(s), niche, time window, creators/accounts, and output format (brief, table, bullet insights).
2. **Discover tools** — list Moonscroll MCP tools from the current session; match the closest tool to the ask.
3. **Query narrowly** — start with one platform or creator; expand only if needed.
4. **Ground claims** — attribute insights to tool results (URLs, titles, metrics the server returns). Do not fabricate view counts or engagement.
5. **Synthesize** — turn raw results into actionable insights: hooks, formats, topics, posting patterns, gaps.
6. **Cite sources** — include video or profile links from tool output when available.

## Output guidance

Prefer structured responses:

- **Summary** — 3–5 bullets of the main takeaway
- **Evidence** — specific videos/creators with links and metrics from Moonscroll
- **Patterns** — recurring hooks, lengths, CTAs, or visual formats
- **Recommendations** — next experiments the user could try (clearly labeled as suggestions)

## Guardrails

- Public insights only — do not attempt private account access or scrape outside Moonscroll tools
- Respect platform and Moonscroll terms; avoid requesting bulk harvesting beyond what the tools allow
- If a tool errors or returns empty data, say so and suggest a narrower query
- Do not invent credentials, endpoints, or undocumented tool parameters

## Related links

- Product: https://moonscroll.ai/
- API docs: https://api.moonscroll.ai/docs/
- Privacy: https://moonscroll.ai/privacy-policy/
