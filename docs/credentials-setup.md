# Credentials Setup Guide

Step-by-step instructions for getting every API key and credential required by the workflows in this repo.

---

## Quick Reference

| Service | Used In | Free Tier | Link |
|---------|---------|-----------|------|
| Anthropic (Claude) | All AI nodes | $5 free credits | [console.anthropic.com](https://console.anthropic.com) |
| Google Sheets | CRM, lead gen, research | Free | [console.cloud.google.com](https://console.cloud.google.com) |
| Gmail | Email outreach, support bot | Free | Same as above |
| Apify | LinkedIn scraper | $5/month free | [apify.com](https://apify.com) |
| Twilio | WhatsApp bot | Free sandbox | [twilio.com](https://twilio.com) |
| SerpAPI | Research agent | 100 free searches/month | [serpapi.com](https://serpapi.com) |

---

## 1. Anthropic API Key (Claude)

**Used in:** Every workflow with an AI node

### Steps
1. Visit [console.anthropic.com](https://console.anthropic.com)
2. Create an account (email or Google)
3. Navigate to **API Keys** → **Create Key**
4. Give it a name like `n8n-workflows`
5. Copy the key immediately (starts with `sk-ant-...`)

### In n8n
1. Go to **Settings → Credentials → New**
2. Search: `Anthropic`
3. Paste your key → **Save**

### Recommended Models
| Model | Speed | Cost | Best For |
|-------|-------|------|----------|
| `claude-3-5-sonnet-20241022` | Medium | $$$ | Complex reasoning, email writing |
| `claude-3-haiku-20240307` | Fast | $ | Lead scoring, CRM notes, bulk tasks |

> **Tip:** Use `claude-3-haiku` for workflows that run on every lead (saves 10x cost). Use `claude-3-5-sonnet` for high-quality output like sales emails.

---

## 2. Google Sheets & Gmail (OAuth2)

**Used in:** All CRM, lead gen, and email workflows

### Steps
1. Go to [console.cloud.google.com](https://console.cloud.google.com)
2. Create a new project (or select existing)
3. Go to **APIs & Services → Enable APIs**
4. Enable: **Google Sheets API** and **Gmail API**
5. Go to **APIs & Services → Credentials → Create Credentials → OAuth 2.0 Client ID**
6. Application type: **Web application**
7. Add redirect URI: `http://localhost:5678/rest/oauth2-credential/callback`
8. Download the credentials JSON

### In n8n
1. Go to **Credentials → New → Google Sheets OAuth2 API**
2. Paste your Client ID and Client Secret
3. Click **Connect My Account** → authorize with Google
4. Repeat for **Gmail OAuth2**

### Getting Your Google Sheet ID
The Sheet ID is the long string in the URL:
```
https://docs.google.com/spreadsheets/d/THIS_IS_YOUR_SHEET_ID/edit
```
Copy this and paste into the workflow's Google Sheets node.

---

## 3. Apify API Token

**Used in:** `lead-generation/linkedin-scraper.json`

### Steps
1. Sign up at [apify.com](https://apify.com) (free $5/month credits)
2. Go to **Settings → Integrations**
3. Copy your **Personal API Token**

### In n8n
1. **Credentials → New → Apify API**
2. Paste your token → **Save**

### Apify Actor for LinkedIn
The `linkedin-scraper.json` workflow uses Actor ID `2Sjf1ZROVCHXwBJzE` (LinkedIn Profile Scraper). Make sure you have this Actor available in your Apify account.

---

## 4. Twilio (WhatsApp)

**Used in:** `ai-agents/whatsapp-ai.json`

### Steps
1. Sign up at [twilio.com](https://twilio.com) (free trial: $15 credit)
2. From Console dashboard, copy:
   - **Account SID** (starts with `AC...`)
   - **Auth Token**
3. Enable WhatsApp Sandbox:
   - Go to **Messaging → Try it Out → Send a WhatsApp Message**
   - Follow instructions to join the sandbox with your phone
4. Set webhook URL to your n8n webhook URL (e.g. `https://yourdomain.com/webhook/whatsapp-webhook`)

### In n8n
1. **Credentials → New → Twilio API**
2. Enter Account SID and Auth Token → **Save**

> **Local testing:** Use [ngrok](https://ngrok.com) to expose your local n8n: `ngrok http 5678`. Use the HTTPS URL as your Twilio webhook.

---

## 5. SerpAPI

**Used in:** `ai-agents/research-agent.json`

### Steps
1. Sign up at [serpapi.com](https://serpapi.com) (100 free searches/month)
2. Go to **Dashboard → API Key**
3. Copy your key

### In n8n
The research agent workflow uses an HTTP Request node. Replace `YOUR_SERPAPI_KEY` in the node's Query Parameters with your actual key.

> **Alternative:** You can replace SerpAPI with any search API (Brave Search, Serper.dev) by modifying the HTTP Request node URL.

---

## Security Best Practices

- **Never commit real API keys** to GitHub — always use `YOUR_*_CREDENTIAL_ID` placeholders
- Store credentials in n8n's built-in credential manager (encrypted at rest)
- Rotate API keys every 90 days
- Use separate API keys for development vs. production
- Set spending limits on Anthropic and Apify to avoid surprise bills

---

*Back to [Setup Guide](setup-guide.md) | [Main README](../README.md)*
