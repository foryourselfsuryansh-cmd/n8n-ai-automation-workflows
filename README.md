# n8n AI Automation Workflows

> **Production-ready n8n workflow templates** for AI-powered business automation. Plug & play workflows for lead generation, CRM, email outreach, AI agents, and more.

[![n8n](https://img.shields.io/badge/n8n-EA4B71?style=for-the-badge&logo=n8n&logoColor=white)](https://n8n.io)
[![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai&logoColor=white)](https://openai.com)
[![Apify](https://img.shields.io/badge/Apify-00B232?style=for-the-badge&logo=apify&logoColor=white)](https://apify.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)

---

## Workflows Included

### Lead Generation
- **LinkedIn Lead Scraper** - Scrape leads from LinkedIn using Apify + save to Google Sheets
- **Email Finder + Enrichment** - Find emails from company domains and enrich with AI
- **Cold Outreach Automation** - Personalized email campaigns via Gmail with AI-written copy

### AI Agents
- **Multi-Step Research Agent** - AI agent that researches topics and compiles reports
- **Customer Support Bot** - AI-powered auto-reply system for Gmail/email
- **WhatsApp AI Responder** - Automated WhatsApp replies using OpenAI/Claude

### CRM & Sales
- **Lead to CRM Pipeline** - Auto-add scraped leads to Google Sheets CRM
- **Follow-up Sequence** - Automated multi-step follow-up email sequences
- **Deal Tracker** - Track deal status changes with automated notifications

### Social Media
- **Instagram Engagement Automation** - Auto-like, comment workflow via API
- **Content Scheduler** - Schedule and post content across platforms

---

## Getting Started

### Prerequisites

- [n8n](https://n8n.io) (self-hosted or cloud)
- [Apify](https://apify.com) account (free tier available)
- OpenAI / Claude API key
- Google Sheets API access

### How to Import Workflows

1. Open your n8n instance
2. Go to **Workflows** > **Import from File**
3. Upload the `.json` file from the relevant folder
4. Add your credentials in the credential manager
5. Activate the workflow

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
|------|---------|
| **n8n** | Workflow automation engine |
| **Apify** | Web scraping & data extraction |
| **OpenAI / Claude** | AI processing & generation |
| **Ollama** | Local LLM (no API cost) |
| **Google Sheets** | CRM & data storage |
| **Gmail API** | Email automation |
| **Twilio** | WhatsApp messaging |

---

## Contributing

Pull requests are welcome! If you have a useful workflow to share:

1. Fork this repository
2. Add your workflow JSON in the relevant folder
3. Update this README with a description
4. Submit a PR

---

## Author

**Suryansh** - AI Automation Builder from Kanpur, India

- GitHub: [@foryourselfsuryansh-cmd](https://github.com/foryourselfsuryansh-cmd)
- Building automation systems for businesses using n8n, Apify & LLMs

---

## License

MIT License - feel free to use these workflows in your own projects.

---

*If this repo helped you, drop a star!*
