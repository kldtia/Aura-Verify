# Aura-Verify

# 🦅 AuraVerify — AI Recruiter Scam Detector

> **Free. No signup. Instant results.**  
> Paste any suspicious recruiter message and AuraVerify will analyze it, look up the company in real time, and deliver a scored verdict straight to your inbox.

---

## 🔍 What It Does

Job seeker scams are everywhere — fake recruiters, spoofed domains, phishing disguised as outreach. AuraVerify was built to protect job seekers who don't have a cybersecurity background to fall back on.

Submit a suspicious message → AuraVerify analyzes the text, looks up the company live, and returns a **scam score (0–100)** with specific, evidence-backed reasons.

---

## ⚙️ How It Works

```
[Form Submission]
       ↓
[Extract Company + Domain]
       ↓
[Tavily Web Search — Live Company Lookup]
       ↓
[Claude Sonnet 4.5 — AI Scam Analysis]
       ↓
[Score + Verdict + Reasons]
       ↓
[Gmail — Email Delivery]
```

See docs/auraverify_v3_architecture_diagram.png for the full visual diagram.

---

## 🛠️ Tech Stack

| Tool | Role |
|------|------|
| **n8n** | Workflow automation (no-code) |
| **Claude Sonnet 4.5** (Anthropic) | AI scam analysis and reasoning |
| **Tavily** | Real-time web enrichment & company lookup |
| **Gmail** | Automated result delivery |

---

## 🚀 Try It Live

👉 [Test AuraVerify Now](https://kdean.app.n8n.cloud/form/b50b00ec-4b57-489a-832d-dec80ef92f05)

No account required. Just paste your message, select the platform, and get results.

---

## 📁 Repo Structure

```
auraverify/
├── README.md                    # You are here
├── workflow/
│   └── auraverify_v3.json       # n8n workflow export (import-ready)
├── samples/
│   └── test_inputs.md           # Sample scam messages for testing
└── docs/
    └── architecture.png         # System architecture diagram
```

---

## 📥 How to Import the Workflow

1. Open your **n8n** instance
2. Go to **Workflows → Import**
3. Upload ` `
4. Add your credentials:
   - Anthropic API key (Claude Sonnet 4.5)
   - Tavily API key
   - Gmail OAuth
5. Activate the workflow — your form URL will appear in the trigger node

> ⚠️ Note: Credential test may show an error in n8n 2.13.x — this is a known bug. Save and run anyway; it works.

---

## 📊 Version History

| Version | Date | What Changed |
|---------|------|--------------|
| v1.0 | Aug 2025 | Initial launch with GPT-4o-mini |
| v2.0 | Apr 2026 | Migrated to Claude Sonnet 4.5 — improved reasoning depth |
| v3.0 | May 2026 | Added real-time Tavily web enrichment for company verification |

---

## 👩🏾‍💻 Built By

**Katia Dean** 
[LinkedIn](https://www.linkedin.com/in/katiadean/) · [Notion Project Page](https://towering-twig-329.notion.site/Aura-Verify-33be50fba7ff80ddbbd1e4184b70d764)

*Built under Katia's Cylife AI*

---

## 📄 License

MIT License — free to use, adapt, and build on.
