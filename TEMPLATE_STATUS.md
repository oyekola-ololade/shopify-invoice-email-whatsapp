# Template Status & Verification

**Classification:** Configurable n8n template asset — not a verified production deployment.

The workflow export and documentation are inspectable template evidence. They do not prove a configured production Shopify/invoicing/messaging deployment, delivery guarantee, SLA, ROI, or client outcome.

## Verification gate
1. Parse/import into a clean current n8n instance.
2. Inspect order triggers, invoice data mapping, email/WhatsApp branches, idempotency, expressions, and Code nodes.
3. Replace placeholder Shopify domain/store IDs, credentials, invoice resources, messaging provider details, URLs, webhooks, and destinations.
4. Run paid/unpaid/cancelled/replayed order cases plus malformed-input and provider-failure cases.
5. Verify exactly one intended invoice/message side effect per authoritative order event and record configured test date/result.

## Security
Never commit store/payment tokens, customer PII, private webhooks, invoice data, or production credentials. Use a development store/sandbox and synthetic orders.

## Change record
- **2026-09-03:** Added repository verification/security/status control. Any placeholder store such as `your-store.myshopify.com` must be replaced before use. No runtime pass is implied.
