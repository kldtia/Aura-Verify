🦅 AuraVerify — AI Recruiter Scam Detector


Free. No signup. Instant results.

Paste any suspicious recruiter message and AuraVerify will analyze it, look up the company in real time, and deliver a scored verdict straight to your inbox.




🔍 What It Does

Job seeker scams are everywhere — fake recruiters, spoofed domains, phishing disguised as outreach. AuraVerify was built to protect job seekers who don't have a cybersecurity background to fall back on.

Submit a suspicious message → AuraVerify analyzes the text, looks up the company live, and returns a scam score (0–100) with specific, evidence-backed reasons.


⚙️ How It Works

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

Show Image


🛠️ Tech Stack

ToolRolen8nWorkflow automation (no-code)Claude Sonnet 4.5 (Anthropic)AI scam analysis and reasoningTavilyReal-time web enrichment & company lookupGmailAutomated result delivery


🚀 Try It Live

👉 Test AuraVerify Now

No account required. Just paste your message, select the platform, and get results.


📁 Repo Structure

auraverify/
├── README.md
├── workflow/
│   └── auraverify_v3.json
├── samples/
│   └── test_inputs.md
└── docs/
    ├── AVlogo.png
    └── architecture.png


📥 How to Import the Workflow


Open your n8n instance
Go to Workflows → Import
Upload workflow/auraverify_v3.json
Add your credentials:

Anthropic API key (Claude Sonnet 4.5)
Tavily API key
Gmail OAuth



Activate the workflow — your form URL will appear in the trigger node



⚠️ Note: Credential test may show an error in n8n 2.13.x — this is a known bug. Save and run anyway; it works.




📊 Version History

VersionDateWhat Changedv1.0Aug 2025Initial launch with GPT-4o-miniv2.0Apr 2026Migrated to Claude Sonnet 4.5 — improved reasoning depthv3.0May 2026Added real-time Tavily web enrichment for company verification


👩🏾‍💻 Built By

Katia Dean

LinkedIn · Notion Project Page · GitHub 


📄 License

MIT License — free to use, adapt, and build on.
