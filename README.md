# n8n Workflow Automation

![n8n](https://img.shields.io/badge/n8n-Self_Hosted-EA4B71?style=flat-square&logo=n8n&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-Compose-2496ED?style=flat-square&logo=docker&logoColor=white)
![Apollo](https://img.shields.io/badge/Apollo.io-Webhooks-5539CC?style=flat-square)
![Repo](https://img.shields.io/badge/Source-Private-orange?style=flat-square)

**My self-hosted n8n instance running custom automation workflows — primarily Apollo.io webhook pipelines for lead enrichment and outreach.**

---

## Why Self-Hosted

I needed automation that I fully control — no rate limits from Zapier, no per-task pricing, no vendor lock-in. Self-hosted n8n on Docker gives me unlimited executions and full control over my data and integrations.

## What I Built

### Apollo.io Webhook Pipeline
- **Catches Apollo.io webhook events** when new leads are enriched or sequences trigger
- Routes lead data through validation, deduplication, and enrichment steps
- Pushes qualified leads into my CRM (Ringora) and outreach queues
- Handles different lead types with branching logic (job leads vs. client leads)

### Lead Enrichment Workflows
- Incoming leads are validated, deduped against existing contacts, and enriched with additional data
- Automated tagging and scoring based on lead source and quality signals
- Failed enrichments are flagged and queued for manual review

### Notification Automations
- Workflow status alerts for monitoring pipeline health
- Error notifications when integrations fail or data quality drops
- Daily summary of leads processed and pipeline throughput

## Infrastructure

```
┌────────────────────────────────────────┐
│        Docker Compose Stack             │
│                                         │
│  ┌──────────────────────────────────┐  │
│  │           n8n Server              │  │
│  │    Workflow Engine + Web UI        │  │
│  └──────────────┬───────────────────┘  │
│                 │                       │
│  ┌──────────────┴───────────────────┐  │
│  │       Persistent Volume           │  │
│  │  Workflows │ Credentials │ Logs   │  │
│  └──────────────────────────────────┘  │
└────────────────────────────────────────┘
          │              │
          ▼              ▼
   ┌────────────┐  ┌──────────┐
   │ Apollo.io  │  │  Ringora │
   │ Webhooks   │  │  CRM     │
   └────────────┘  └──────────┘
```

## Tech Stack

`n8n (self-hosted)` · `Docker Compose` · `Apollo.io webhooks` · `REST APIs`

---

> *My workflow configurations. Reach out if you want to see the specific workflow designs.*
