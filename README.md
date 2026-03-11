# 🛡️ FeedOracle Compliance — OpenClaw Skill

An [OpenClaw](https://openclaw.ai) skill that gives AI agents access to **MiCA compliance intelligence and stablecoin risk scoring** for regulated tokenized markets.

Every API response is **ECDSA-signed and multi-chain anchored** (Polygon + XRPL) — making it audit-grade for MiCA, DORA, and AMLR compliance workflows.

---

## Install

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

Get your free API key at [feedoracle.io/dashboard](https://feedoracle.io/dashboard) — 100 calls/day free.

---

## What this skill does

Your agent automatically uses FeedOracle whenever a conversation involves:

- 🪙 Stablecoin names (USDT, USDC, EURC, EURI, PYUSD...)
- 📋 MiCA, DORA, AMLR, ESMA, EBA, BaFin regulatory topics
- 🏦 Regulated tokenized assets or RWA compliance
- 🔍 Requests for verifiable, replayable compliance evidence

---

## API Capabilities

| Endpoint | Description |
|----------|-------------|
| `GET /v1/stablecoin/risk/{symbol}` | Risk score (0-100), peg stability, reserve backing |
| `GET /v1/mica/status/{symbol}` | MiCA compliance status, ESMA/EBA registration |
| `GET /v1/macro/{indicator}` | 86 FRED + 20 ECB macro series |
| `POST /v1/evidence/bundle` | ECDSA-signed audit bundle with Polygon TX hash |
| `GET /v1/registry/issuer/{name}` | Issuer license lookup |

---

## Why FeedOracle?

**MiCA full enforcement: July 2026.** Stablecoin issuers, regulated funds, and AI agents operating in EU tokenized markets need more than dashboards — they need **verifiable, replayable proof**.

- ✅ On-chain anchored (Polygon + XRPL)
- ✅ ECDSA-signed responses
- ✅ MCP-compatible (3 servers, 48 tools)
- ✅ MiCA / DORA / AMLR coverage

---

## Pricing

| Tier | Calls/day | Price |
|------|-----------|-------|
| Free | 100 | $0 |
| Pro | 10,000 | $49/mo |
| Agent | Unlimited | $299/mo |

→ [feedoracle.io](https://feedoracle.io)

---

## License

MIT-0 — use freely in any agent or application.
