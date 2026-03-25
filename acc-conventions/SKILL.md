---
name: acc-conventions
description: ACC technology stack conventions and system integration reference
---

# ACC Technology Conventions

## Technology Stack

- **HubSpot** — CRM, CMS, payments, and workflow automation. The primary system of record for contacts, memberships, and transactions.
- **Mews** — Property management system (PMS) for ACC huts and lodges. Manages reservations, check-ins, and room inventory.
- **QuickBooks Online** — Accounting system. Financial records, invoicing, and reporting.
- **CData Connect** — Middleware for querying QuickBooks Online data via SQL. Used by IronClaw and other integrations to read QB data without direct API calls.
- **NATS** — Messaging system used in IronClaw for event-driven communication between services.
- **IronClaw** — ACC's internal integration platform. Connects HubSpot, Mews, QuickBooks, and other systems via NATS messaging.

## Conventions

### Section Names
Section names (ACC local chapters) must be normalized consistently across all systems. When syncing or comparing section names between HubSpot, Mews, and QuickBooks, always normalize to a canonical form before matching.

### API Tokens
Use `HUBSPOT_API_TOKEN` as the environment variable name for HubSpot API authentication across all projects and coded actions.

### Data Flow
The typical data flow for membership operations:
1. HubSpot (source of truth for membership status)
2. IronClaw (orchestration via NATS)
3. Mews (reservation/property access)
4. QuickBooks Online (financial records via CData Connect)
