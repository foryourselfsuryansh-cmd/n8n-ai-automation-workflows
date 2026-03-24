# Frequently Asked Questions (FAQ)

## General

**Q: What is this repository?**
A: A collection of production-ready n8n workflow templates that use Claude (Anthropic's AI) as the intelligence layer for business automation — covering AI agents, CRM, lead generation, and social media.

**Q: Do I need to pay for Claude API?**
A: Yes, the workflows require a Claude API key from [console.anthropic.com](https://console.anthropic.com). Anthropic offers a free tier to get started.

**Q: Which Claude model should I use?**
A: The workflows are configured for `claude-sonnet-4-5` (balance of speed/cost) or `claude-opus-4-5` (maximum capability). You can swap the model string in any workflow.

**Q: Do I need a cloud n8n instance?**
A: No. All workflows work on self-hosted n8n (Docker, VPS, local). Some also work on n8n.io cloud.

---

## Setup

**Q: How do I import a workflow?**
A:
1. Download the `.json` file from this repo
2. Open your n8n instance
3. Click **+** → **Import from file**
4. Select the downloaded JSON
5. Configure your credentials (see `docs/credentials-setup.md`)

**Q: Where do I set my API keys?**
A: In n8n, go to **Settings → Environment Variables** and add:
- `ANTHROPIC_API_KEY` — your Claude API key
- `SLACK_WEBHOOK_URL` — for Slack notifications (optional)
- `AIRTABLE_BASE_ID` — for Airtable workflows (optional)

**Q: The workflow shows credential errors. What do I do?**
A: After importing, click each node that shows a red credential error → select or create the appropriate credential. See `docs/credentials-setup.md` for detailed instructions.

---

## Workflows

**Q: Can I modify the Claude prompts?**
A: Absolutely. All system prompts are in the HTTP Request node's JSON body. Edit the `system` field to change Claude's behavior.

**Q: Why does the workflow use HTTP Request instead of n8n's Claude node?**
A: The HTTP Request approach gives more control over model selection, token limits, and API versioning without depending on n8n plugin updates.

**Q: How do I handle Claude API rate limits?**
A: Add a **Wait** node between batch operations (e.g., 1-2 seconds between calls). For high-volume use, implement a queue using n8n's queue mode.

**Q: Can I use these workflows with Ollama or local models?**
A: Yes! Change the URL from `https://api.anthropic.com/v1/messages` to your Ollama endpoint and update the payload format accordingly.

---

## Troubleshooting

**Q: I get a 401 error from the Claude API.**
A: Your `ANTHROPIC_API_KEY` is missing or invalid. Double-check it in n8n environment variables.

**Q: The workflow runs but returns empty results.**
A: Check that your input data has the expected fields. Use n8n's **Test** feature to inspect each node's output.

**Q: Workflow times out on large inputs.**
A: Increase the `timeout` value in the HTTP Request node options (default: 30000ms). For very large inputs, consider splitting into smaller chunks.

---

## Contributing

**Q: Can I submit my own workflows?**
A: Yes! See [CONTRIBUTING.md](../CONTRIBUTING.md) for guidelines. We welcome quality workflows that use Claude API.

**Q: How do I report a bug or request a feature?**
A: Open an [issue](https://github.com/foryourselfsuryansh-cmd/n8n-ai-automation-workflows/issues) using the appropriate template.
