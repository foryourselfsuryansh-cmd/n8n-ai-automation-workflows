# Architecture Overview

This document describes the architecture and design patterns used across all n8n AI automation workflows in this repository.

## Core Design Principles

### 1. Claude AI as the Intelligence Layer
Every workflow in this repository integrates **Anthropic's Claude API** as the primary AI reasoning engine. Claude handles:
- Natural language understanding and generation
- Complex decision-making logic
- Content classification and routing
- Intelligent data extraction and transformation

### 2. n8n as the Orchestration Layer
[n8n](https://n8n.io) serves as the workflow automation backbone, providing:
- Visual workflow design and management
- 400+ native integrations
- Webhook triggers and event-driven execution
- Error handling and retry logic
- Self-hosted privacy and data control

## Workflow Categories

### AI Agents (`/ai-agents`)
Autonomous agents that use Claude's tool-use capabilities to:
- Search the web and synthesize information
- Make multi-step decisions
- Interact with external APIs dynamically

**Pattern:** Trigger → Claude Agent → Tool Calls → Response

### CRM Automation (`/crm-automation`)
Intelligent customer relationship workflows:
- Lead scoring using Claude sentiment analysis
- Automated follow-up email drafting
- Customer segmentation with AI classification

**Pattern:** CRM Webhook → Claude Analysis → Action Router → CRM Update

### Lead Generation (`/lead-generation`)
AI-powered prospecting pipelines:
- Multi-source data aggregation
- Claude-powered prospect qualification
- Personalized outreach generation

**Pattern:** Data Sources → Enrichment → Claude Qualification → Outreach

### Social Media (`/social-media`)
Content creation and management:
- Claude-generated platform-specific content
- Trend analysis and content scheduling
- Engagement monitoring and response drafting

**Pattern:** Trigger/Schedule → Claude Content Gen → Multi-Platform Publisher

## Claude API Integration Pattern

All workflows follow this standard integration approach:

```
HTTP Request Node
  URL: https://api.anthropic.com/v1/messages
  Method: POST
  Headers:
    x-api-key: {{ $env.ANTHROPIC_API_KEY }}
    anthropic-version: 2023-06-01
  Body:
    model: claude-opus-4-5 (or claude-sonnet-4-5)
    max_tokens: 1024-4096
    messages: [...conversation context...]
```

## Environment Variables

All workflows use n8n environment variables for credentials:

| Variable | Description |
|----------|-------------|
| `ANTHROPIC_API_KEY` | Claude API authentication |
| `OPENAI_API_KEY` | Fallback AI model (optional) |
| `AIRTABLE_TOKEN` | Airtable integration |
| `SLACK_WEBHOOK_URL` | Slack notifications |
| `SMTP_*` | Email sending configuration |

## Error Handling Strategy

Every production workflow implements:
1. **Try/Catch nodes** around API calls
2. **Retry logic** with exponential backoff
3. **Error notification** via Slack/email
4. **Fallback paths** when Claude API is unavailable

## Scalability Considerations

- Workflows are designed for self-hosted n8n instances
- Queue mode recommended for high-volume production use
- Rate limiting built into Claude API call nodes
- Batching patterns for bulk data processing

## Contributing New Workflows

See [CONTRIBUTING.md](../CONTRIBUTING.md) for guidelines on adding new workflows to this repository.
