# AuraVerify v3 — Architecture Diagram

The diagram below shows the end-to-end workflow for AuraVerify v3.

```
[Form Submission]
  Message + platform + email
        ↓
[Extract Company + Domain]
  Parsed from message text (n8n code node)
        ↓
[Tavily Web Enrichment]  ← NEW in v3
  Live search · scam reports · domain legitimacy check
        ↓
[Claude Sonnet 4.5 — AI Analysis]
  Message text + web enrichment data
  Scam signals, patterns, domain mismatches
        ↓
[Score + Verdict + Reasons]
  0–100 scam score with evidence-backed explanation
        ↓
[Gmail Delivery]
  Results sent instantly to user's inbox
```

## Tech Stack

| Step | Tool |
|------|------|
| Workflow automation | n8n |
| Company + domain extraction | n8n code node |
| Real-time web enrichment | Tavily API |
| AI scam analysis | Claude Sonnet 4.5 (Anthropic) |
| Result delivery | Gmail |

## What's New in v3

Previous versions analyzed the message text only. v3 adds a **real-time web enrichment layer**:

1. Extracts the company name and sender domain from the message
2. Runs a live Tavily search for scam reports and legitimacy signals
3. Passes enrichment findings to Claude alongside the original message
4. Claude cross-references claims against real-world data before scoring

This means AuraVerify no longer just reads what the sender said — it checks if it's real.
