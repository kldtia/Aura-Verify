# AuraVerify v3.1 — Architecture Diagram

The diagram below shows the end-to-end workflow for AuraVerify v3.1, including what each step passes to the next.

```
[On form submission]
  Platform (Email · LinkedIn · Discord · SMS · Other) + Message + Email
        ↓
[Normalize Fields]  (Set node)
  → toEmail, platform, originalMessage
        ↓
[Extract Company & Domain]  (Code node — regex, no AI)
  → + companyName, senderDomain, domainIsFreeProvider
        ↓
[Has Company or Domain?]  (IF node)
   │ yes                                  │ no
   ↓                                      │
[Tavily Web Search]  (HTTP, Header Auth)  │
  "<company> employer recruiter           │
   reviews scam complaints" · top 3       │
   ↓                                      │
[Merge Enrichment Data]  (Code node) ◄────┘
  → + tavilyEnrichment (Tavily answer, top snippets,
      or "Web search skipped" when nothing to look up)
        ↓
[AI Agent + Claude Sonnet 5.5]
  Message + extracted fields + web enrichment
  → JSON: scamScore, verdict, reasons[3–6], platform, report
        ↓
[Parse & Format]  (Code node)
  Parses Claude's JSON, pulls enrichment from Merge Enrichment Data
  → HTML card: score bar, verdict badge, caution banner,
    reasons, 🔍 Web Enrichment section
        ↓
[Email Result]  (Gmail)
  Sent to toEmail · subject "AuraVerify: Scam Check Result"
```

## Tech Stack

| Step | Tool |
|------|------|
| Workflow automation | n8n |
| Company + domain extraction | n8n code node |
| Real-time web enrichment | Tavily API (Header Auth credential) |
| AI scam analysis | Claude Sonnet 5.5 (Anthropic) via n8n AI Agent |
| Result formatting | n8n code node (email-safe inline HTML) |
| Result delivery | Gmail |

## How Claude Decides

The system prompt sets a fixed reasoning order before any scoring:

1. Is the sender domain a verified company or known HR vendor (Checkr, ADP, Workday, Greenhouse…)? → legitimacy anchor
2. Does the sender domain match who they claim to be?
3. Is this post-offer onboarding (W-4, I-9, background check, payroll)? → not a red flag on its own
4. Only then: scan language and links for scam patterns
5. Legit domain + suspicious content → **Proceed with Caution**, not Scam

Messages under 15 words, gibberish, or anything not job-related return **Invalid**.

## What's New

**v3** added a real-time web enrichment layer: the company and sender domain are pulled from the message, Tavily searches for scam reports and legitimacy signals, and Claude cross-references those findings before scoring. AuraVerify no longer just reads what the sender said — it checks if it's real.

**v3.1** hardened it:

- Tavily API key lives in an n8n credential, not in the workflow file
- Tavily is skipped when no company or domain is found (no more misleading "unknown company" searches)
- The 🔍 Web Enrichment section now actually renders in result emails
- Single, clean email subject; one source of truth for the recipient address
- Platform list aligned between the form and Claude (Discord, Other)
- Successful and manual executions are not saved, so submitted messages aren't kept
