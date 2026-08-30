# Shopify Order → Invoice, Email & WhatsApp

Generates an order invoice and notifies the customer by email and WhatsApp the moment a Shopify order lands.

![n8n](https://img.shields.io/badge/-n8n-333?style=flat-square) ![PDF generation service](https://img.shields.io/badge/-PDF%20generation%20service-333?style=flat-square) ![SendGrid](https://img.shields.io/badge/-SendGrid-333?style=flat-square) ![WhatsApp API](https://img.shields.io/badge/-WhatsApp%20API-333?style=flat-square) ![Airtable](https://img.shields.io/badge/-Airtable-333?style=flat-square) ![Slack](https://img.shields.io/badge/-Slack-333?style=flat-square)
![n8n](https://img.shields.io/badge/n8n-workflow-EA4B71?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-blue?style=flat-square)

---

**[Open the visual project page →](./index.html)**

## Table of Contents

- [Overview](#overview)
- [Architecture](#architecture)
- [Workflow](#workflow)
- [Tech Stack](#tech-stack)
- [Demo status](#demo-status)
- [Setup](#setup)
- [Repository Structure](#repository-structure)
- [Disclaimer](#disclaimer)

## Overview

**Trigger:** Webhook (Shopify order payload)

Generates an order invoice and notifies the customer by email and WhatsApp the moment a Shopify order lands.

### Key Features

- Automatic invoice generation
- Dual-channel order confirmation (email + WhatsApp)
- Order log with fulfillment status

## Architecture

The diagram below represents the sanitized template flow. External services, credentials, and environment-specific identifiers must be configured before execution.

```mermaid
flowchart TD
    A["Shopify order webhook"] --> B["Normalize order and line items"]
    B --> C["Request invoice PDF"]
    C --> D{"PDF generated?"}
    D -->|Yes| E["Email invoice"]
    D -->|Yes| F["Send WhatsApp confirmation"]
    D -->|Yes| G["Log order in Airtable"]
    D -->|No| H["Alert admin in Slack"]
```

## Workflow

1. Shopify order webhook receives the new order
2. Extract order ID, customer, total, and line items
3. Generate an invoice PDF via a PDF service
4. On success, email the invoice, send a WhatsApp confirmation, and log the order in Airtable
5. On failure, alert an admin in Slack

## Tech Stack

- n8n
- PDF generation service
- SendGrid
- WhatsApp API
- Airtable
- Slack

## Demo status

A configured live-run recording is not included yet. Credentials and service identifiers remain placeholders.


## Setup

1. Import `workflow/T16_Shopify_Invoice_Email_WhatsApp.json` into your n8n instance (**Workflows → Import from File**).
2. Replace every placeholder credential/URL in the workflow (e.g. `YOUR_..._API_KEY`, `YOUR_..._URL`) with your own service credentials.
3. Activate the workflow and point the relevant integration (webhook source, scheduled trigger, etc.) at the generated webhook URL.
4. Test with a sample payload before going live.

## Repository Structure

```text
.
├── index.html
├── README.md
├── LICENSE
├── .gitignore
└── workflow/
    └── T16_Shopify_Invoice_Email_WhatsApp.json
```


## Disclaimer

This workflow was built as a portfolio/template project to demonstrate n8n workflow automation and AI integration. API credentials and sensitive configuration have been removed before publication — replace all `YOUR_..._KEY` / `YOUR_..._URL` placeholders with your own before use.

---

Designed and engineered by

**Oyekola Ololade**

AI Systems & Integration Engineer

- LinkedIn: <http://linkedin.com/in/ololade-oyekola-5b1797397>
- Email: <oyekolaololade69@gmail.com>
