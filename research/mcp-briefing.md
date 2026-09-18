# Model Context Protocol (MCP) — Research Briefing

**Prepared:** 2026-09-18
**Project:** MCP research kickoff
**Data sources:** encyclopedia-style reference lookup (Wikipedia), market data service (ETH price + 7-day history), public code search (GitHub)

---

## 1. Background

**Lookup status:** Search-style lookups for MCP ("Model Context Protocol", "MCP protocol Anthropic", "Claude AI data access standard") returned **no results**, and the direct article lookup timed out twice before succeeding on the third attempt. The successful lookup returned the summary below, so this section is based on an actual returned reference — not guesswork. (Reliability note: the reference search endpoint also returned empty for unrelated control terms such as "artificial intelligence", so only the direct title fetch was usable.)

**As returned by the reference source (Wikipedia, article "Model Context Protocol"):**

> "The Model Context Protocol (MCP) is an open standard and open-source framework introduced by Anthropic in November 2024 to standardize the way artificial intelligence (AI) systems like large language models (LLMs) integrate and share data with external tools, systems, and data sources. MCP provides a standardized interface for reading files, executing functions, and handling contextual prompts. Following its announcement, the protocol was adopted by major AI providers, including OpenAI and Google DeepMind."

**Plain-language summary:**

MCP is a shared, open standard — think of it as a universal adapter — that lets AI assistants (typically LLM-based) connect to external tools and data sources through one consistent interface, instead of every application having to build a bespoke integration for every tool. It was introduced by Anthropic in November 2024 and covers three kinds of capability: reading files/data, executing functions (calling tools), and handling contextual prompts. Per the reference source, other major AI providers — including OpenAI and Google DeepMind — adopted the protocol following its announcement.

---

## 2. Market snapshot — Ethereum (ETH)

Figures below are **as-returned values** from the market data service, exactly as received and unrounded.

| Metric | Value (USD) | Timestamp (as returned) |
|---|---|---|
| Current ETH price | 2589.26 | 2026-09-18T17:36:25Z |
| Week history — first data point | 2514.8468192459 | 2026-09-12T00:00:00Z |
| Week history — last data point | 2415.9596535243 | 2026-09-17T00:00:00Z |

Full daily series returned for the "past 7 days" request (6 daily points, as returned):

| Date | ETH/USD |
|---|---|
| 2026-09-12 | 2514.8468192459 |
| 2026-09-13 | 2525.2672615902 |
| 2026-09-14 | 2476.6825261637 |
| 2026-09-15 | 2514.7595504678 |
| 2026-09-16 | 2397.497260165 |
| 2026-09-17 | 2415.9596535243 |

**Notes:**

- The "past 7 days" request returned six daily data points (2026-09-12 through 2026-09-17); 2026-09-18 has no completed daily point yet — the current price is the intraday value.
- Rationale for including ETH: the prototype's payment leg runs on Ethereum.
- *Derived figures (computed here, NOT returned by the service):* first→last across the returned week ≈ −3.9%; last returned point→current price ≈ +7.2%.

---

## 3. Adoption scan — MCP in public code

Queries run against public code search (GitHub code search):

| Query | Approx. hits |
|---|---|
| `modelcontextprotocol language:go` | ~41,280 |
| `modelcontextprotocol in:path` | ~16,960 |
| `mcp server filename:README.md` | ~594,944 |
| Repository search: "Model Context Protocol" | ~29,993 repos |

**Most notable repositories/files found:**

1. **`mark3labs/mcp-go`** — "A Go implementation of the Model Context Protocol (MCP), enabling seamless integration between LLM applications and external data sources and tools." (notable file: `mcp/meta.go`)
2. **`zeromicro/go-zero`** — a cloud-native Go microservices framework shipping a built-in MCP server module (notable file: `mcp/server.go`) — evidence of MCP being absorbed into established infrastructure projects rather than staying confined to AI-specific tooling.
3. **Official ecosystem (from repository search):** `modelcontextprotocol/servers` (~90.4k stars), `modelcontextprotocol/python-sdk` (~24.3k stars), `modelcontextprotocol/typescript-sdk` (~13.4k stars), `modelcontextprotocol/modelcontextprotocol` (the specification itself, ~9.2k stars), and `wong2/awesome-mcp-servers` (~4.3k stars).

**Caveats:**

- The bare term `mcp` is ambiguous and matches unrelated acronyms; the ~595k figure is an upper bound that includes clear false positives (top hits in that query included repositories unrelated to Model Context Protocol). Queries using the full term `modelcontextprotocol` are the reliable signal.
- Code-search hit counts vary with query phrasing and should be treated as approximate.

---

## Follow-ups

Tracked in this repository under the issue titled **"MCP research follow-ups"**, including:

- Fact-checking the Background section against the primary specification.
- Expanding the market snapshot to additional assets beyond ETH.
