# 🏛️ Council Assist
### Enterprise Knowledge Agent for Local Government
**Microsoft Agents League Hackathon 2026 | Enterprise Agents Track**

[![Enterprise Agents](https://img.shields.io/badge/Track-Enterprise%20Agents-purple)](https://github.com/microsoft/agentsleague)
[![Work IQ](https://img.shields.io/badge/Microsoft%20IQ-Work%20IQ-blue)](https://learn.microsoft.com/microsoft-copilot-studio)
[![Copilot Studio](https://img.shields.io/badge/Built%20with-Copilot%20Studio-orange)](https://copilotstudio.microsoft.com)
[![Hack for Good](https://img.shields.io/badge/Award-Hack%20for%20Good-green)](https://github.com/microsoft/agentsleague)

---

## 🎬 Demo Video

> **[▶ Watch Council Assist in Action](YOUR_YOUTUBE_LINK_HERE)**

---

## 🎯 What It Does

Council Assist is an AI-powered enterprise knowledge agent built for local government officers using Microsoft Copilot Studio. It lives inside Microsoft Teams and helps officers instantly retrieve council policies, draft responses, and autonomously escalate high-risk cases — all from a single natural language message.

---

## 🏗️ Architecture

![Council Assist Architecture](docs/architecture.png)

| Layer | Component | Purpose |
|---|---|---|
| **User** | Microsoft Teams | Officer interaction via 1:1 chat |
| **Agent** | Microsoft Copilot Studio | Generative orchestration + GPT-4.1 |
| **IQ** | Work IQ + SharePoint | Semantic retrieval + citation engine |
| **IQ** | Work IQ User MCP | Microsoft 365 organisational context |
| **IQ** | Work IQ Copilot MCP | Copilot Search across M365 tenant |
| **Action** | Power Automate | HHSRS escalation workflow |
| **Security** | Microsoft Entra ID | Authentication + permission-aware access |

---

## 📋 The Problem

Council officers across the UK face three daily productivity failures:

- **Knowledge fragmentation** — Policies live across SharePoint, PDFs, and intranet pages. Finding the right document takes 20–45 minutes per query
- **Response inconsistency** — Officer responses to resident queries vary in accuracy and compliance, creating legal and reputational risk
- **Onboarding delays** — New officers take weeks to become productive because institutional knowledge is inaccessible

> In a team of 50 officers, 30 minutes lost per day equals **750 hours of lost time every single week.**

---

## ✅ The Solution

Council Assist brings the council's entire knowledge base into Microsoft Teams. Officers ask questions in plain English and receive:

- **Grounded, cited answers** drawn directly from SharePoint policy documents
- **Multi-step reasoning** across Housing, Planning, Environmental Services, Benefits, and HR
- **Autonomous escalation** — detecting HHSRS Category 1 hazards and firing Power Automate workflows automatically
- **Live Teams notifications** — Adaptive Cards posted to the Housing Escalations channel with full case details

---

## 🧠 Microsoft IQ Integration

Council Assist integrates **Work IQ** as the core intelligence layer — not as a toggle, but as the architectural foundation of every response.

### Work IQ — Knowledge Grounding
- Semantic retrieval engine pulls answers from the council's SharePoint knowledge base
- Citation engine returns the exact document name and version with every response
- Metadata date filtering ensures responses reference the most current policy version
- Permission-aware access — users only see documents they already have rights to

### Work IQ User MCP (Preview)
- Connected as a tool in Copilot Studio
- Provides Microsoft 365 user and organisational context to the agent

### Work IQ Copilot MCP (Preview)
- Connected as a tool in Copilot Studio
- Enables Copilot Search capabilities across the M365 tenant

### Evidence of Work IQ in Action
Every agent response includes:
- Named policy document (e.g. `HOU-POL-001 v4.0 — Housing Disrepair Complaint Procedure`)
- Specific section cited with reference number
- Two or more citations for complex cross-policy answers

---

## 🔧 Technical Stack

| Component | Technology |
|---|---|
| Agent builder | Microsoft Copilot Studio |
| Knowledge grounding | Microsoft Work IQ |
| Knowledge base | SharePoint Online — 14 policy documents |
| IQ tools | Work IQ User MCP + Work IQ Copilot MCP |
| Workflow automation | Power Automate — HHSRS Escalation Flow |
| Deployment channel | Microsoft Teams (1:1 chat) |
| Authentication | Microsoft Entra ID (delegated, user-level) |
| Orchestration model | GPT-4.1 with generative orchestration |

---

## 📚 Knowledge Base

14 policy documents across 5 service areas — all created for demonstration purposes using fictional **Westbridge Council** as the scenario organisation.

| Service Area | Documents |
|---|---|
| 🏠 Housing & Repairs | Disrepair Complaint Procedure v4, Void Property Inspection Policy v3, Housing Allocations Policy v2, Damp and Mould Response Policy v1 |
| 🏗️ Planning & Enforcement | Planning Application Guidance v5, Planning Enforcement Policy v3 |
| ♻️ Environmental Services | Noise Complaint Procedure v4, Bulky Waste Collection Policy v2 |
| 💷 Benefits & Council Tax | Housing Benefit Assessment Guide v6, Council Tax Reduction Scheme Guidance v3 |
| 👥 HR & Compliance | Grievance Policy v5, Flexible Working Request Policy v4, Sickness Absence Management Policy v6, Resident Query Response Templates v3 |

> **Note:** Westbridge Council is a fictional local authority used for demonstration purposes only. All documents are synthetic and contain no confidential or real council data.

---

## 🚀 Key Capabilities Demonstrated

### 1. Policy Retrieval with Citations
```
Officer: "What is the procedure when a resident reports a leaking roof causing damp?"

Council Assist: Returns a 7-step procedure citing:
- HOU-POL-001 v4.0 — Housing Disrepair Complaint Procedure [1]
- HOU-POL-004 v1.0 — Damp and Mould Response Policy [2]
```

### 2. Cross-Service Intelligence
```
Officer: "What are the Bradford Factor trigger points for sickness absence?"

Council Assist: Returns structured 4-tier table from:
- HR-POL-003 v6.0 — Sickness Absence Management Policy [1]
```

### 3. Autonomous HHSRS Escalation
```
Officer: "A resident at 5 Hammersmith Grove has severe mould in two bedrooms.
         A child under 2 lives there. Does this escalate?"

Council Assist: Identifies HHSRS Category 1 criteria
               Generates ESC reference: ESC-20260608-1204
               Posts Adaptive Card to Housing Escalations Teams channel
               Returns statutory Awaab's Law compliance timelines
```

---

## ⚡ Power Automate — HHSRS Escalation Flow

The escalation flow is triggered autonomously by the agent when HHSRS Category 1 criteria are detected:

1. **Trigger** — Agent calls the flow with ResidentAddress, IssueDescription, VulnerabilityIndicator
2. **Action** — Posts an Adaptive Card to the Housing Escalations Microsoft Teams channel
3. **Response** — Returns ESC reference number to the officer in Teams chat

The card displays: property address, issue reported, vulnerability indicator, P1 priority level, and required actions under Awaab's Law.

---

## 🔒 Security and Responsible AI

- **Authentication** — Microsoft Entra ID delegated permissions throughout
- **Permission-aware** — Responses respect existing SharePoint user permissions
- **Human-in-the-loop** — Escalation decisions presented to officer before execution
- **No hallucination** — System prompt instructs agent never to guess on policy
- **Fallback** — Out-of-scope queries return a clear redirect message
- **PII** — No resident personal data stored or repeated beyond what is necessary
- **Data residency** — No data leaves the Microsoft 365 tenant

---

## 🌍 Social Impact — Hack for Good

Council Assist serves the residents who depend on council services for housing, benefits, social care, and planning. Faster, more accurate officer responses mean:

- Vulnerable residents receive correct guidance sooner
- Housing hazards like damp and mould are escalated before they cause harm
- Officers spend time on people, not searching for documents

This is responsible AI improving democratic service delivery.

---

## 📁 Repository Structure

```
council-assist/
├── README.md                          — This file
├── docs/
│   ├── architecture.png               — Architecture diagram
│   ├── screenshots/
│   │   ├── teams-policy-retrieval.png — Scene 3 demo screenshot
│   │   ├── teams-bradford-factor.png  — Scene 4 demo screenshot
│   │   ├── teams-escalation.png       — Scene 5 escalation response
│   │   └── teams-adaptive-card.png    — Housing Escalations card
│   └── work-iq-integration.md        — Detailed Work IQ explanation
├── copilot-studio/
│   ├── agent-instructions.md          — Full system prompt
│   └── escalation-tool-config.md     — HHSRS Escalation Tool configuration
├── power-automate/
│   └── hhsrs-escalation-flow.md      — Flow description and screenshots
├── knowledge-base/
│   └── document-structure.md         — SharePoint folder structure
└── DISCLAIMER.md                      — Data and confidentiality notice
```

---

## 🛠️ How to Deploy

### Prerequisites
- Microsoft 365 Business or Enterprise tenant
- Copilot Studio access (free trial at aka.ms/TryCopilotStudio)
- SharePoint Online site
- Power Automate access

### Step 1 — Set Up SharePoint Knowledge Base
1. Create a SharePoint Communication Site
2. Create folders: Housing and Repairs, Planning and Enforcement, Environmental Services, Benefits and Council Tax, HR and Compliance
3. Upload your council policy documents to the relevant folders

### Step 2 — Create the Agent
1. Go to copilotstudio.microsoft.com
2. Click Create → New agent → Skip to configure
3. Paste the system prompt from `copilot-studio/agent-instructions.md`
4. Set Authentication to Authenticate with Microsoft

### Step 3 — Add Knowledge Source
1. Click Add knowledge → SharePoint
2. Paste your SharePoint site URL
3. Add the description from `copilot-studio/agent-instructions.md`
4. Wait for Ready status

### Step 4 — Add Work IQ MCP Tools
1. Go to Settings → Connections
2. Connect Work IQ User MCP
3. Connect Work IQ Copilot MCP
4. Add both as tools to the agent

### Step 5 — Add Power Automate Flow
1. Create the HHSRS Escalation Flow (see `power-automate/hhsrs-escalation-flow.md`)
2. Add as a tool to the agent with the description from the config file

### Step 6 — Deploy to Teams
1. Publish the agent
2. Go to Channels → Teams and Microsoft 365 Copilot
3. Click See agent in Teams → Add

---

## 📊 Judging Criteria Alignment

| Criterion | Weight | How Council Assist Addresses It |
|---|---|---|
| Accuracy & Relevance | 20% | Work IQ grounds every answer in real policy documents with named citations |
| Reasoning & Multi-step | 20% | 7-step procedure generation, HHSRS risk assessment, cross-policy synthesis |
| Reliability & Safety | 20% | Entra ID auth, fallback topics, human-in-loop escalation, never guesses on policy |
| Creativity & Originality | 15% | Only local government submission — authentic sector expertise and lived experience |
| UX & Presentation | 15% | Structured responses, Adaptive Cards, Teams integration, officer-friendly language |
| Community Vote | 10% | Share on LinkedIn and Discord #agentsleague |

---

## 👤 Developer

**Christopher Ekorhi**
Power Platform Developer | Local Government and Healthcare background
- Microsoft Agents League Hackathon 2026
- Enterprise Agents Track

---

## ⚠️ Disclaimer

This project was built for the Microsoft Agents League Hackathon 2026. All council policy documents are synthetic and created specifically for this demonstration. Westbridge Council is a fictional organisation. No real council data, resident data, or personally identifiable information has been used. No confidential information is included in this repository.

See [DISCLAIMER.md](DISCLAIMER.md) for full details.

---

*Built with Microsoft Copilot Studio + Work IQ + SharePoint + Power Automate + Microsoft Teams*
*Microsoft Agents League Hackathon 2026 | Enterprise Agents Track | Christopher Ekorhi*
