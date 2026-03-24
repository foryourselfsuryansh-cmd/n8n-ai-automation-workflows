# Complete Setup Guide

This guide walks you through setting up n8n and configuring Claude (Anthropic API) to run any workflow in this repository from scratch.

---

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Install n8n](#install-n8n)
3. [Set Up Claude API](#set-up-claude-api)
4. [Configure Claude in n8n](#configure-claude-in-n8n)
5. [Import a Workflow](#import-a-workflow)
6. [Set Up Other Credentials](#set-up-other-credentials)
7. [Activate & Test](#activate--test)
8. [Troubleshooting](#troubleshooting)

---

## Prerequisites

Before starting, make sure you have:

- A computer running Windows, Mac, or Linux
- [Node.js](https://nodejs.org/) v18+ OR [Docker](https://www.docker.com/) installed
- An [Anthropic account](https://console.anthropic.com/) (free tier available)
- A Google account (for Google Sheets/Gmail workflows)

---

## Install n8n

### Option A: Docker (Recommended)

Docker is the easiest way to run n8n with persistent data.

```bash
# Pull and run n8n
docker run -it --rm \
  --name n8n \
  -p 5678:5678 \
  -v ~/.n8n:/home/node/.n8n \
  docker.n8n.io/n8nio/n8n
```

Then open **http://localhost:5678** in your browser.

### Option B: npm

```bash
npm install n8n -g
n8n start
```

### Option C: n8n Cloud

Sign up at [n8n.io/cloud](https://n8n.io/cloud) for a hosted version. No setup required.

---

## Set Up Claude API

1. Go to [console.anthropic.com](https://console.anthropic.com/)
2. Sign up or log in
3. Click **API Keys** in the left sidebar
4. Click **Create Key**
5. Name it (e.g. `n8n-automation`)
6. Copy the key — **you won't see it again!**
7. Save it somewhere safe (password manager recommended)

> **Free Tier:** Anthropic offers $5 free credits on sign-up. `claude-3-haiku` is the cheapest model (~$0.25 per million tokens). Most workflows in this repo cost less than $0.01 per run.

---

## Configure Claude in n8n

1. Open your n8n instance at **http://localhost:5678**
2. Click **Credentials** in the left sidebar
3. Click **Add Credential**
4. Search for **`Anthropic`**
5. Paste your API key in the **API Key** field
6. Click **Save**

Your Claude credential is now ready. All workflows in this repo that use `@n8n/n8n-nodes-langchain.lmChatAnthropic` will use this credential.

---

## Import a Workflow

1. Download the `.json` file from this repo (click the file > **Raw** > Save)
2. In n8n, go to **Workflows** in the left sidebar
3. Click **Add Workflow** > **Import from File**
4. Select the downloaded `.json` file
5. The workflow will open in the editor

---

## Set Up Other Credentials

Depending on the workflow, you may need:

### Google Sheets / Gmail
1. In n8n Credentials, click **Add Credential**
2. Search for **Google Sheets OAuth2 API** or **Gmail OAuth2**
3. Follow the OAuth flow — you'll be redirected to Google to authorize
4. Select your Google account and allow access

### Apify (for LinkedIn scraper)
1. Sign up at [apify.com](https://apify.com) (free tier available)
2. Go to **Settings > Integrations > API tokens**
3. Copy your API token
4. In n8n, add an **Apify** credential with this token

### Twilio (for WhatsApp workflows)
1. Sign up at [twilio.com](https://twilio.com)
2. Go to **Console > Account Info**
3. Copy **Account SID** and **Auth Token**
4. Enable WhatsApp Sandbox in **Messaging > Try it Out > Send a WhatsApp Message**
5. In n8n, add a **Twilio** credential with SID + Auth Token

---

## Activate & Test

1. After importing and setting credentials, review each node
2. Replace any remaining placeholder values (Google Sheet IDs, etc.)
3. Click **Test Workflow** to run it once manually
4. Check the output of each node in the execution panel
5. Once working, toggle the **Active** switch (top right) to enable automatic triggering

---

## Troubleshooting

### Claude node returns an error
- Check your Anthropic API key is valid at [console.anthropic.com](https://console.anthropic.com/)
- Ensure you have API credits remaining
- Try switching from `claude-3-5-sonnet` to `claude-3-haiku` (cheaper/faster)

### Workflow doesn't trigger automatically
- Make sure the **Active** toggle is ON (green)
- For webhook-based workflows, ensure the webhook URL is accessible from the internet (use [ngrok](https://ngrok.com) for local testing)

### Google Sheets credential fails
- Re-authorize the OAuth connection in n8n Credentials
- Make sure the Google Sheet ID is correct (it's the long string in the sheet URL)

### n8n node 'Anthropic' not found
- You need n8n version **1.0+** with LangChain nodes
- Run: `docker pull docker.n8n.io/n8nio/n8n:latest` to update

---

## Next Steps

- Read the [Credentials Setup Guide](credentials-setup.md) for detailed API key instructions
- Check [CONTRIBUTING.md](../CONTRIBUTING.md) to share your own workflows
- Open an [Issue](https://github.com/foryourselfsuryansh-cmd/n8n-ai-automation-workflows/issues) if you're stuck

---

*Made with ❤️ by [Suryansh](https://github.com/foryourselfsuryansh-cmd) — Kanpur, India*
