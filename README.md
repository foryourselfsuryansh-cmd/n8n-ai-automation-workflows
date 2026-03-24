# n8n AI Automation Workflows — Powered by Claude

> **Open-source n8n workflow templates** that use **Anthropic's Claude** as the core reasoning and generation LLM. Built for developers and small businesses who want to automate lead generation, CRM, WhatsApp responses, and more — without writing backend code.

[![n8n](https://img.shields.io/badge/n8n-EA4B71?style=for-the-badge&logo=n8n&logoColor=white)](https://n8n.io)
[![Claude](https://img.shields.io/badge/Claude%20by%20Anthropic-D4A017?style=for-the-badge)](https://www.anthropic.com/claude)
[![Apify](https://img.shields.io/badge/Apify-00B232?style=for-the-badge&logo=apify&logoColor=white)](https://apify.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)

---

## Why Claude?

All AI agent workflows in this repo use **Claude (claude-3-5-sonnet / claude-3-haiku)** via the Anthropic API as the primary LLM for:

- **Reasoning & decision-making** inside multi-step agents
- **Personalized email & message copy generation**
- **Data summarization** from scraped leads
- **Natural language responses** in WhatsApp and customer support bots
- **Research & report writing** in the research agent workflow

Claude was chosen over other LLMs for its instruction-following ability, safety, and strong performance on business automation tasks.

---

## Workflows Included

### Lead Generation
- **`lead-generation/linkedin-scraper.json`** — Scrape leads from LinkedIn using Apify, enrich with Claude-generated summaries, save to Google Sheets
- **`lead-generation/email-finder.json`** — Find & verify emails from company domains, use Claude to score lead quality
- **`lead-generation/cold-outreach.json`** — Claude writes personalized cold emails for each lead based on their profile

### AI Agents (Claude-powered)
- **`ai-agents/research-agent.json`** — Multi-step agent: Claude reasons over search results and compiles structured reports
- **`ai-agents/support-bot.json`** — Gmail auto-responder: Claude reads incoming emails and drafts intelligent replies
- **`ai-agents/whatsapp-ai.json`** — WhatsApp bot: Claude generates context-aware replies via Twilio + n8n

### CRM & Sales Automation
- **`crm-automation/lead-pipeline.json`** — Auto-add scraped leads to Google Sheets CRM with Claude-generated lead notes
- **`crm-automation/followup-sequence.json`** — Automated multi-step follow-up emails with Claude-written copy

### Social Media
- **`social-media/instagram-automation.json`** — Instagram engagement automation via API
- **`social-media/content-scheduler.json`** — Claude generates and schedules social content

---

## Getting Started

### Prerequisites
- [n8n](https://n8n.io/) (self-hosted or cloud)
- **Anthropic API key** (Claude) — [Get one here](https://console.anthropic.com/)
- [Apify](https://apify.com/) account (free tier works)
- Google Sheets API access
- Twilio account (for WhatsApp workflows)

### How to Import a Workflow
1. Open your n8n instance
2. Go to **Workflows** > **Import from File**
3. Upload the `.json` file from the relevant folder
4. Add your **Anthropic API key** in n8n's credential manager under `Anthropic API`
5. Add other credentials (Apify, Gmail, Google Sheets) as needed
6. Activate the workflow

### Setting Up Claude in n8n
1. In n8n, go to **Credentials** > **New**
2. Search for `Anthropic`
3. Paste your Claude API key
4. All AI Agent nodes in these workflows will automatically use this credential

---

## Folder Structure

```
n8n-ai-automation-workflows/
├── lead-generation/
│   ├── linkedin-scraper.json
│   ├── email-finder.json
│   └── cold-outreach.json
├── ai-agents/
│   ├── research-agent.json
│   ├── support-bot.json
│   └── whatsapp-ai.json
├── crm-automation/
│   ├── lead-pipeline.json
│   └── followup-sequence.json
└── social-media/
    ├── instagram-automation.json
    └── content-scheduler.json
```

---

## Tech Stack

| Tool | Purpose |
|------|----------|
| **n8n** | Workflow automation engine |
| **Claude (Anthropic)** | Core LLM for reasoning, writing, and agent logic |
| **Apify** | Web scraping & data extraction |
| **Ollama** | Local LLM fallback (no API cost) |
| **Google Sheets** | CRM & data storage |
| **Gmail API** | Email automation |
| **Twilio** | WhatsApp messaging |

---

## Contributing

Pull requests are welcome! If you have a Claude-powered workflow to share:

1. Fork this repository
2. Add your workflow JSON in the relevant folder
3. Update this README with a description
4. Submit a PR

---

## Author

**Suryansh** — AI Automation Builder from Kanpur, India

- GitHub: [@foryourselfsuryansh-cmd](https://github.com/foryourselfsuryansh-cmd)
- Building open-source automation systems using n8n, Claude (Anthropic), Apify & LLMs
- These workflows are freely available to help developers and small businesses adopt AI automation

---

## License

MIT License — free to use in your own projects.

If this repo helped you, consider giving it a star!
