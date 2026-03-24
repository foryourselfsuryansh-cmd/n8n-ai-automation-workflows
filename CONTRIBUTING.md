# Contributing to n8n AI Automation Workflows

Thank you for your interest in contributing! This project welcomes Claude-powered n8n workflow contributions from the community.

---

## How to Contribute

### Option 1: Share a New Workflow

1. **Fork** this repository
2. **Create a branch**: `git checkout -b add/your-workflow-name`
3. **Add your workflow JSON** in the correct folder:
   - `lead-generation/` — LinkedIn scraping, email finding, cold outreach
   - `ai-agents/` — Claude-powered bots and agents
   - `crm-automation/` — CRM and sales pipeline workflows
   - `social-media/` — Social content and scheduling
4. **Export your workflow** from n8n: Workflows > Export > Download
5. **Sanitize credentials**: Replace all API keys/IDs with `YOUR_CREDENTIAL_ID` placeholders
6. **Update the README** in the relevant folder (or the root README) with a description of your workflow
7. **Submit a Pull Request**

### Option 2: Improve Existing Workflows

- Fix bugs in existing workflow JSON
- Add better error handling
- Optimize prompts sent to Claude
- Add comments/documentation inside the JSON `meta` field

### Option 3: Report Issues

- Use the [Bug Report template](.github/ISSUE_TEMPLATE/bug_report.md)
- Include your n8n version and which workflow is affected

---

## Workflow Standards

All contributed workflows must follow these standards:

### Required
- [ ] Uses **Claude (Anthropic)** as the AI/LLM node — not OpenAI-only workflows
- [ ] Has a `meta` field with `description`, `llm` (model name), and `author`
- [ ] All credential IDs replaced with `YOUR_*_CREDENTIAL_ID` placeholders
- [ ] Workflow name follows the format: `Feature Name (Claude)` or `Feature Name + Claude`

### Preferred
- [ ] Uses `claude-3-5-sonnet-20241022` or `claude-3-haiku-20240307` (latest stable models)
- [ ] Includes a Code node for data transformation
- [ ] Has error handling (IF node for null checks)
- [ ] Works on n8n self-hosted v1.0+

---

## Setting Up Your Development Environment

```bash
# 1. Clone your fork
git clone https://github.com/YOUR_USERNAME/n8n-ai-automation-workflows.git

# 2. Run n8n locally (Docker recommended)
docker run -it --rm \
  --name n8n \
  -p 5678:5678 \
  -v ~/.n8n:/home/node/.n8n \
  docker.n8n.io/n8nio/n8n

# 3. Open n8n at http://localhost:5678
# 4. Import the workflow JSON and test it
# 5. Export and clean credentials before submitting
```

---

## Credential Placeholders

When submitting a workflow, replace all sensitive values:

| Credential | Placeholder |
|-----------|-------------|
| Anthropic API Key | `YOUR_ANTHROPIC_CREDENTIAL_ID` |
| Google Sheets OAuth | `YOUR_GOOGLE_CREDENTIAL_ID` |
| Gmail OAuth | `YOUR_GMAIL_CREDENTIAL_ID` |
| Apify API | `YOUR_APIFY_CREDENTIAL_ID` |
| Twilio API | `YOUR_TWILIO_CREDENTIAL_ID` |

---

## Pull Request Checklist

Before submitting your PR:
- [ ] Workflow JSON is valid (no syntax errors)
- [ ] Credentials are sanitized
- [ ] `meta.description` is filled in
- [ ] Added a description in the README or folder README
- [ ] PR description explains what the workflow does

---

## Code of Conduct

- Be respectful and constructive in discussions
- No workflows that violate platform terms of service
- No spam or self-promotion in workflow descriptions

---

Questions? Open an issue or reach out via GitHub: [@foryourselfsuryansh-cmd](https://github.com/foryourselfsuryansh-cmd)
