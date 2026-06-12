# 🧪 AuraVerify — Sample Test Inputs

Use these sample messages to test the AuraVerify workflow. Each includes the expected verdict and key red flags the tool should detect.

---

## Test 1 — Fake Recruiter (LinkedIn)
**Platform:** LinkedIn  
**Expected Verdict:** SCAM (85–100)

```
Hi [Name], I came across your profile and I think you'd be a perfect fit for a remote Data Analyst role paying $95–120K. The hiring manager wants to move fast — can you send me your resume and Social Security Number to verify your eligibility? We need to get you started by Monday.
```

**Red flags to detect:**
- Requests SSN (personal data harvesting)
- Urgency tactic ("move fast", "by Monday")
- Vague company name
- Off-platform data request

---

## Test 2 — Fake Job Offer (Email)
**Platform:** Email  
**Expected Verdict:** SCAM (90–100)

```
From: hiring@coinbase-careers.net
Subject: Job Offer – Remote Blockchain Analyst

Congratulations! You have been selected for a remote position at Coinbase. Salary: $150,000/year. To begin onboarding, please purchase $200 in gift cards to cover your equipment deposit and send the codes to this email. Your first check will reimburse you within 24 hours.
```

**Red flags to detect:**
- Spoofed domain (coinbase-careers.net vs coinbase.com)
- Gift card payment request (classic scam tactic)
- Unrealistic offer with no interview
- Upfront payment demand

---

## Test 3 — Borderline / Legit Recruiter (LinkedIn)
**Platform:** LinkedIn  
**Expected Verdict:** LOW RISK (0–30)

```
Hi Katia, I'm a recruiter at Booz Allen Hamilton and I came across your profile. We have an opening for a Systems Integration PM on a cleared program in Northern Virginia. Would you be open to a 15-minute call this week to discuss? Happy to share the full JD if you're interested.
```

**Red flags to detect:** None expected  
*Use this to verify AuraVerify doesn't over-flag legitimate outreach.*

---

## Test 4 — Resume Service Scam (SMS)
**Platform:** SMS  
**Expected Verdict:** SCAM (75–95)

```
Hi! I found your resume on Indeed. I'm a career coach and I can get you 3x more interviews guaranteed. My premium resume rewrite package is only $299 this week. Click here to pay: bit.ly/resumefix2026
```

**Red flags to detect:**
- Unsolicited outreach with payment pressure
- Shortened/suspicious URL
- Unrealistic guarantee ("3x more interviews")
- High-pressure discount tactic

---

## Notes for Testers

- Results are delivered via email — make sure to enter a valid email in the form
- Scam scores are 0–100; anything above 70 is flagged as likely scam
- The tool performs best on messages 50+ words with a company name or domain present
- Web enrichment works best when a company name or domain is clearly stated in the message
