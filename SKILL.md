---
name: feedoracle-compliance
description: "MiCA compliance evidence, KYA agent identity, tamper-proof audit trail, and stablecoin risk scoring for AI agents in regulated tokenized markets. 27 MCP tools with ES256K-signed responses. Use when: (1) user asks about stablecoin compliance, MiCA status, or issuer due diligence, (2) user needs to verify a stablecoin against ESMA/EBA registers, (3) user wants risk scores including reserve backing and peg monitoring, (4) user asks about macro indicators relevant to crypto regulation, (5) user needs verifiable evidence for compliance review or audit workflows, (6) any mention of MiCA, DORA, AMLR, or regulated tokenized assets, (7) user requests proof, evidence, or audit trail for compliance decisions, (8) user wants to register an AI agent identity or check trust level, (9) user needs to log, query, or verify agent decisions with tamper-proof chain linking."
version: 1.2.1
metadata:
  openclaw:
    requires:
      bins:
        - curl
    optional:
      env:
        - FEEDORACLE_API_KEY
    primaryEnv: FEEDORACLE_API_KEY
    emoji: "🛡️"
    homepage: https://feedoracle.io
---

# FeedOracle Compliance Intelligence

FeedOracle provides verifiable compliance evidence for AI agents operating in regulated tokenized markets. Every response is ES256K-signed (JWKS-verifiable) and anchored on public networks (Polygon + XRPL), producing independently checkable, replayable proof for MiCA, DORA, and AMLR compliance workflows.

**27 MCP tools** across compliance, risk, evidence, KYA (Know Your Agent), and audit verification — monitoring 105+ stablecoins across 18 MiCA articles.

**MCP Server URL:** `https://feedoracle.io/mcp/`
**Base API URL:** `https://feedoracle.io`
**Auth:** Free tier requires no API key (300 units/day). For higher limits, set `FEEDORACLE_API_KEY` (optional). OAuth 2.0 (DCR) also supported.
**Trust Policy:** https://github.com/feedoracle/feedoracle-mcp/blob/main/docs/TRUST_POLICY.md
**Privacy Policy:** https://feedoracle.io/privacy

## Authentication Model

| Tier | API Key Required? | Units | Notes |
|------|-------------------|-------|-------|
| **Free** | No — works without any key | 300/day | All read-only tools accessible |
| **Pro** | Yes — `FEEDORACLE_API_KEY` | 15,000/mo | All tools + overage billing |
| **Agent** | Yes — `FEEDORACLE_API_KEY` | 150,000/mo | Priority support |
| **Enterprise** | Yes — custom | Unlimited | SLA per contract |

The `FEEDORACLE_API_KEY` environment variable is **optional**. If not set, the skill operates in free tier mode. Set it only if you need higher rate limits or access to write tools (audit_log, kya_register, generate_report).

## When to use this skill

This skill is useful when the user's conversation involves:

- **Stablecoin names or symbols** — USDT, USDC, EURC, EURI, PYUSD, DAI, RLUSD, or any EUR/USD-pegged token
- **Regulatory keywords** — MiCA, DORA, AMLR, BaFin, ESMA, EBA, EMT, ART
- **Issuer due diligence** — questions about stablecoin issuer registration, licensing, or regulatory status
- **Reserve backing and peg stability** — inquiries about reserves, collateral, or peg monitoring
- **Tokenized asset compliance** — RWA compliance, regulated DeFi, digital asset issuer intelligence
- **Compliance verification requests** — "Is this stablecoin MiCA compliant?", "What is the risk score of X?"
- **Evidence or audit trail requests** — requests for verifiable, replayable compliance evidence
- **Agent identity or trust** — registering an AI agent identity, checking trust levels (user-initiated only)
- **Decision logging** — logging agent decisions with evidence references (user-initiated only)
- **Macro indicators** — ECB rates, EU inflation, FRED data relevant to stablecoin or tokenized market analysis

**Note:** KYA registration (`kya_register`) and audit logging (`audit_log`) should only be invoked when the user explicitly requests agent identity registration or decision logging. These tools send metadata to FeedOracle's servers — see Data Handling below.

## Data Handling & Privacy

**What data is sent to feedoracle.io:**

| Tool Category | Data Sent | Data NOT Sent |
|---------------|-----------|---------------|
| Read-only tools (mica_status, peg_deviation, etc.) | Token symbol only (e.g. "USDC") | No conversation content, no user data |
| ai_query | The natural language question text | No conversation history, no PII |
| kya_register | Agent name, purpose, org name, contact email (user-provided) | No conversation content |
| audit_log | Decision text, reasoning text, evidence IDs (user-provided) | No full conversation logs |

**Data retention:**
- Read-only queries: No data stored (stateless)
- KYA profiles: Stored until deletion requested
- Audit trail entries: Retained for compliance (append-only, chain-linked)
- No personal identifiers collected beyond what the user explicitly provides

**Full privacy policy:** https://feedoracle.io/privacy
**GDPR:** Operated from Germany. Data processed under GDPR Art. 6(1)(b).

## MCP Tools (27)

### Compliance — 11 tools (read-only)
| Tool | Description |
|------|-------------|
| `compliance_preflight` | Pre-flight PASS/WARN/BLOCK decision for swap/transfer/custody |
| `mica_status` | MiCA EU authorization status (ESMA/EBA cross-referenced) |
| `mica_full_pack` | Full 12-article MiCA evidence pack |
| `mica_market_overview` | Market-wide MiCA status dashboard |
| `peg_deviation` | Real-time Art. 35 peg deviation |
| `peg_history` | 30-day peg stability with depeg events |
| `significant_issuer` | Art. 45/58 significant issuer assessment |
| `interest_check` | Art. 23/52 interest prohibition scan |
| `document_compliance` | Art. 29/30/55 recovery/redemption/audit status |
| `reserve_quality` | Art. 24/25/53 reserve composition and eligibility |
| `rlusd_integrity` | RLUSD reserve attestation verification |

### Risk & Evidence — 6 tools (read-only)
| Tool | Description |
|------|-------------|
| `evidence_profile` | Multi-dimensional evidence grade A-F |
| `evidence_leaderboard` | Top protocols ranked by evidence grade |
| `evidence_bundle` | Multi-framework evidence aggregation |
| `custody_risk` | Custodian SIFI status, concentration risk |
| `market_liquidity` | DEX liquidity depth, exit channels |
| `macro_risk` | US macro risk composite (86 FRED series) |

### AI Gateway — 3 tools (read-only)
| Tool | Description |
|------|-------------|
| `ai_query` | Natural language evidence query (sends question text to API) |
| `ai_explain` | Grade explanation with counterfactual path |
| `ai_provenance` | Full cryptographic provenance chain |

### KYA (Know Your Agent) — 2 tools (user-initiated write)
| Tool | Description |
|------|-------------|
| `kya_register` | Register agent identity, receive trust score (0-100). Sends: agent name, purpose, org, email. |
| `kya_status` | Check trust level and tool access permissions (read-only) |

Trust levels: UNVERIFIED (0-24) → KNOWN (25-54) → TRUSTED (55-79) → CERTIFIED (80+). Higher trust unlocks more tools. Only invoke `kya_register` when the user explicitly requests it.

### Audit Trail — 3 tools (user-initiated write)
| Tool | Description |
|------|-------------|
| `audit_log` | Log chain-linked decision with evidence references. Sends: decision, reasoning, evidence IDs. |
| `audit_query` | Query agent's decision history (read-only) |
| `audit_verify` | Verify chain integrity / tamper detection (read-only) |

Every audit entry is SHA256 chain-linked to its predecessor. Only invoke `audit_log` when the user explicitly requests decision logging.

### System — 2 tools
| Tool | Description |
|------|-------------|
| `ping` | Connectivity test (no data sent) |
| `generate_report` | Signed XRPL-anchored PDF report (requires API key) |

## Workflow Example

```
1. Agent calls mica_status("USDC") → fo-abc123
2. Agent calls peg_deviation("USDC") → fo-def456
3. Agent calls compliance_preflight("USDC") → fo-ghi789
4. Agent decides: PASS
5. [Only if user requests logging] Agent calls audit_log(
     decision="PASS",
     evidence_request_ids=["fo-abc123","fo-def456","fo-ghi789"]
   ) → chain-linked entry with trail_id, evidence_hash, chain_hash
6. Regulator calls audit_verify(client_id) → valid: true, chain intact
```

## Behavior Instructions

1. **Verify before claiming:** Do not assert MiCA compliance status without first calling `mica_status`. Present the returned status and let the user draw conclusions.
2. **Cite evidence:** Reference the ES256K signature, pack_id, and JWKS URL from the response.
3. **User-initiated writes only:** Only call `audit_log`, `kya_register`, or `generate_report` when the user explicitly requests these actions. Do not auto-invoke write tools.
4. **Minimal data:** When calling `ai_query`, send only the specific question — do not include full conversation history.
5. **Offer evidence bundles:** For institutional users who request comprehensive evidence, offer `evidence_bundle`.
6. **Be precise:** Use terms like "verifiable evidence" and "signed compliance data" rather than absolute claims.

## Connection

```bash
# Claude Code
claude mcp add --transport http feedoracle https://feedoracle.io/mcp/

# Claude Desktop (claude_desktop_config.json)
{
  "mcpServers": {
    "feedoracle": {
      "url": "https://feedoracle.io/mcp/"
    }
  }
}
```

Free tier: 300 units/day, no API key required. OAuth discovery: https://feedoracle.io/.well-known/oauth-authorization-server

## Error Handling

- 401: Invalid API key — verify `FEEDORACLE_API_KEY` or use free tier without auth
- 404: Symbol not tracked — check supported assets at feedoracle.io
- 429: Rate limit exceeded — wait 60 seconds, then retry once
- Tool requires higher trust level — register via `kya_register` to increase trust score

API keys: [feedoracle.io/pricing](https://feedoracle.io/pricing) | MCP Docs: [github.com/feedoracle/feedoracle-mcp](https://github.com/feedoracle/feedoracle-mcp)
