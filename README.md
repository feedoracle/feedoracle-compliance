<div align="center">

# 🛡️ FeedOracle Compliance Intelligence

**Verifiable compliance evidence for AI agents in regulated tokenized markets**

[![License: MIT-0](https://img.shields.io/badge/License-MIT--0-brightgreen.svg)](https://spdx.org/licenses/MIT-0.html)
[![API Status](https://img.shields.io/badge/API-Live-success.svg)](https://feedoracle.io/mcp/health)
[![MCP Tools](https://img.shields.io/badge/MCP_Tools-53-blue.svg)](https://feedoracle.io/mcp)
[![ClawHub](https://img.shields.io/badge/ClawHub-feedoracle--compliance-orange.svg)](https://clawhub.ai/feedoracle/feedoracle-compliance)
[![Endpoints](https://img.shields.io/badge/API_Endpoints-260+-purple.svg)](https://feedoracle.io/docs)

ES256K-signed responses · JWKS-verifiable · On-chain anchored (Polygon + XRPL)
Designed for MiCA, DORA, and AMLR compliance workflows.

[Get Started Free](https://feedoracle.io/mcp/) · [API Docs](https://feedoracle.io/docs) · [MCP Server](https://github.com/feedoracle/feedoracle-mcp) · [Trust Policy](https://github.com/feedoracle/feedoracle-mcp/blob/main/docs/TRUST_POLICY.md)

</div>

---

## ⚡ Quick Start — Connect in 10 Seconds

No login, no API key needed for free tier:

```bash
# Claude Code (one command)
claude mcp add --transport http feedoracle https://feedoracle.io/mcp/

# Claude Desktop — add to claude_desktop_config.json
{
  "mcpServers": {
    "feedoracle": {
      "url": "https://feedoracle.io/mcp/"
    }
  }
}
```

Free tier: **300 units/day** — start querying immediately.

### Try It Now

```bash
# MiCA compliance check (no auth needed)
curl -s -X POST https://feedoracle.io/mcp \
  -H "Content-Type: application/json" \
  -H "Accept: application/json, text/event-stream" \
  -d '{"jsonrpc":"2.0","id":1,"method":"initialize","params":{"protocolVersion":"2024-11-05","capabilities":{},"clientInfo":{"name":"test","version":"1.0"}}}'
```

> Every response includes an ES256K signature verifiable via [JWKS](https://feedoracle.io/.well-known/jwks.json) — no trust in FeedOracle required.

---

## 🤖 What This Skill Does

Your agent **automatically** uses FeedOracle whenever a conversation involves:

| Trigger | Examples |
|---------|----------|
| 🪙 **Stablecoin names** | USDT, USDC, EURC, EURI, PYUSD, DAI, RLUSD |
| 📋 **Regulatory keywords** | MiCA, DORA, AMLR, ESMA, EBA, BaFin |
| 🏦 **Issuer due diligence** | Issuer registration, licensing, reserve backing |
| 📊 **Peg monitoring** | Peg stability, collateral, reserve assessment |
| 🔍 **Evidence requests** | "Show proof", "audit trail", "compliance verification" |
| 🤖 **Agent identity** | KYA registration, trust scoring, tool access |
| 📝 **Decision logging** | Audit log, chain verification, tamper detection |
| 🏛️ **Tokenized assets** | RWA compliance, regulated DeFi |

---

## 🔧 MCP Tools (27)

### Compliance — 11 tools
| Tool | Description |
|------|-------------|
| `compliance_preflight` | Pre-flight PASS/WARN/BLOCK decision |
| `mica_status` | MiCA authorization status (ESMA/EBA cross-referenced) |
| `mica_full_pack` | Full 12-article MiCA evidence pack |
| `mica_market_overview` | Market-wide MiCA status dashboard |
| `peg_deviation` | Real-time Art. 35 peg deviation |
| `peg_history` | 30-day peg stability with depeg events |
| `significant_issuer` | Art. 45/58 significant issuer check |
| `interest_check` | Art. 23/52 interest prohibition scan |
| `document_compliance` | Art. 29/30/55 recovery/redemption/audit |
| `reserve_quality` | Art. 24/25/53 reserve composition |
| `rlusd_integrity` | RLUSD reserve attestation |

### Risk & Evidence — 6 tools
| Tool | Description |
|------|-------------|
| `evidence_profile` | Multi-dimensional evidence grade A-F |
| `evidence_leaderboard` | Top protocols by evidence grade |
| `evidence_bundle` | Multi-framework evidence aggregation |
| `custody_risk` | Custodian SIFI status, concentration risk |
| `market_liquidity` | DEX liquidity depth, exit channels |
| `macro_risk` | US macro risk composite (86 FRED series) |

### AI Gateway — 3 tools
| Tool | Description |
|------|-------------|
| `ai_query` | Natural language evidence query |
| `ai_explain` | Grade explanation with counterfactual path |
| `ai_provenance` | Full cryptographic provenance chain |

### KYA (Know Your Agent) — 2 tools ✨ NEW
| Tool | Description |
|------|-------------|
| `kya_register` | Register agent identity, receive trust score (0-100) |
| `kya_status` | Check trust level and tool access permissions |

Trust levels: **UNVERIFIED** → **KNOWN** → **TRUSTED** → **CERTIFIED**. Higher trust unlocks sensitive tools like `generate_report` and `evidence_bundle`.

### Audit Trail — 3 tools ✨ NEW
| Tool | Description |
|------|-------------|
| `audit_log` | Log chain-linked decision with evidence references |
| `audit_query` | Query agent's decision history |
| `audit_verify` | Verify chain integrity (tamper detection) |

Every entry is SHA256 chain-linked — if any entry is modified, all subsequent hashes break. Regulators can independently verify.

### System — 2 tools
| Tool | Description |
|------|-------------|
| `ping` | Connectivity test |
| `generate_report` | Signed XRPL-anchored PDF report |

---

## 🔐 Enterprise Trust Layer

Every response includes 6 trust layers:

```
evidence{}    → SHA-256 content hash + pack_id + blockchain anchor
jws{}         → RFC 7515 ES256K compact token (kid: fo-ecdsa-v1)
sla{}         → confidence (0-1), freshness, per-source health, tier
trust{}       → signature_present, schema_valid, registry_logged, replayable
schema_ref    → Versioned JSON Schema (e.g. "mica/v1")
verify_url    → Independent verification link
```

**Trust Policy v1.0** — Formal evidence governance with Dispute-SLA (4h acknowledge, 24h classify, 5 business days resolve). [Read full policy →](https://github.com/feedoracle/feedoracle-mcp/blob/main/docs/TRUST_POLICY.md)

---

## 🔄 Audit Workflow Example

```
1. Agent calls mica_status("USDC")          → fo-abc123
2. Agent calls peg_deviation("USDC")         → fo-def456
3. Agent calls compliance_preflight("USDC")  → fo-ghi789
4. Agent decides: PASS
5. Agent calls audit_log(
     decision="PASS",
     evidence_request_ids=["fo-abc123","fo-def456","fo-ghi789"],
     reasoning="USDC verified, peg stable, preflight PASS"
   ) → trail_id + chain_hash
6. Regulator calls audit_verify(client_id)   → valid: true
```

---

## 📦 Install as ClawHub Skill

```bash
npx clawhub@latest install feedoracle-compliance
```

Or add manually to `~/.openclaw/openclaw.json`:

```json
{
  "skills": {
    "entries": {
      "feedoracle-compliance": {
        "enabled": true,
        "env": {
          "FEEDORACLE_API_KEY": "your_key_here"
        }
      }
    }
  }
}
```

---

## 💰 Pricing

| Tier | Units | Price | Best for |
|------|-------|-------|----------|
| **Free** | 300/day | €0 | Evaluation & testing |
| **Pro** | 15,000/mo | €49/mo | Compliance teams |
| **Agent** | 150,000/mo | €299/mo | AI agents in production |
| **Enterprise** | Unlimited | Custom | Regulated institutions |

All tiers include ES256K-signed responses, JWKS verification, and on-chain anchoring.
Payments via Stripe or USDC (Polygon).

→ [feedoracle.io/pricing](https://feedoracle.io/pricing)

---

## 🌐 The FeedOracle MCP Ecosystem

| Server | URL | Tools | Focus |
|--------|-----|-------|-------|
| **Compliance** | `feedoracle.io/mcp/` | 27 | MiCA, KYA, Audit Trail, Evidence |
| **Macro** | `feedoracle.io/mcp/macro/` | 13 | FRED/ECB data, regime classification |
| **Risk** | `feedoracle.io/mcp/risk/` | 13 | Stablecoin 7-signal risk scoring |

**53 MCP tools total** across 3 servers. All responses cryptographically signed.

---

## 🔗 Links

| Resource | URL |
|----------|-----|
| 🌐 Website | [feedoracle.io](https://feedoracle.io) |
| 📖 API Docs | [feedoracle.io/docs](https://feedoracle.io/docs) |
| 🤖 MCP Server | [github.com/feedoracle/feedoracle-mcp](https://github.com/feedoracle/feedoracle-mcp) |
| 🛡️ Trust Page | [feedoracle.io/trust](https://feedoracle.io/trust/) |
| 🔑 Pricing | [feedoracle.io/pricing](https://feedoracle.io/pricing.html) |
| 📊 Uptime | [uptime.feedoracle.io](https://uptime.feedoracle.io) |
| 🦞 ClawHub | [clawhub.ai/feedoracle/feedoracle-compliance](https://clawhub.ai/feedoracle/feedoracle-compliance) |
| 📋 Trust Policy | [docs/TRUST_POLICY.md](https://github.com/feedoracle/feedoracle-mcp/blob/main/docs/TRUST_POLICY.md) |
| 🔐 JWKS | [feedoracle.io/.well-known/jwks.json](https://feedoracle.io/.well-known/jwks.json) |
| 🔌 OAuth Discovery | [feedoracle.io/.well-known/oauth-authorization-server](https://feedoracle.io/.well-known/oauth-authorization-server) |

---

## 📄 License

[MIT-0](https://spdx.org/licenses/MIT-0.html) — use freely in any agent or application. No attribution required.
