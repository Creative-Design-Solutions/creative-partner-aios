# Connections

**Read this before starting any session.** This is the authoritative registry of every tool your AIOS can reach. Never guess whether something is connected — check here first.

Filled by `/onboard` from your Q4–Q7 answers. Expanded over time as you wire new tools. `/audit` checks this file for coverage and freshness.

| # | Domain | Tool | Mechanism | Auth | Last checked |
|---|---|---|---|---|---|
| 1 | Revenue / Financials | | | | |
| 2 | Database / Backend | | | | |
| 3 | Customer interactions | | | | |
| 4 | Calendar | | | | |
| 5 | Communication | | | | |
| 6 | Project / task tracking | | | | |
| 7 | Notes / meeting intelligence | | | | |
| 8 | Knowledge / files | | | | |

**Mechanism options:**
- `mcp` — MCP server
- `script` — Python/Bash script in `tools/` hitting an API
- `export` — CSV/JSON pipeline
- `key+ref` — `.env` key + `references/{tool}-api.md` guide
- `not yet connected`

---

When you wire a new tool:
1. Add it to this table immediately
2. Save `references/{tool}-api.md` — endpoints, auth flow, common queries — researched once, saved forever
3. Note the date in Last checked

See `references/integrations-guide.md` for what to connect and in what order.
