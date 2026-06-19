# n8n AI Agents — Construction

3 production-ready n8n workflow agents for the construction domain, built with GPT-4o. Each agent handles complex, multi-step automation with AI decision-making, batch processing, conditional routing, and automated notifications.

---

## C-7: Site Safety Compliance & OSHA Reporting Agent
**Trigger:** Schedule (Daily)
**Workflow:** Fetch inspection reports → batch → GPT-4o analyze violations against 29 CFR 1926 → if OSHA reportable: file incident report + alert PM / else: log minor violation + notify PM
**Use Case:** Automates OSHA compliance by classifying violations, calculating fines, determining required forms (300/301/300A), and auto-filing incident reports with corrective action plans.
**n8n:** https://aravind5.app.n8n.cloud/workflow/yV1moFLC09gC4g6C
**Credentials:** OpenAI API Key · Gmail OAuth2 · Safety Platform API Bearer Token · OSHA Reporting API Bearer Token

---

## C-8: Subcontractor Invoice Reconciliation & Payment Agent
**Trigger:** Schedule (Weekly)
**Workflow:** Fetch pending invoices → batch → fetch contract SOV → GPT-4o reconcile line items + check compliance docs + calculate retainage → if approved: create ERP payment voucher + notify sub / else: flag + notify sub of discrepancies
**Use Case:** Eliminates manual invoice review. AI checks every line item against the Schedule of Values, validates lien waivers and certified payroll, and calculates correct retainage.
**n8n:** https://aravind5.app.n8n.cloud/workflow/lQhFarz4A38f2flj
**Credentials:** OpenAI API Key · Gmail OAuth2 · ERP System API Bearer Token

---

## C-9: Material Procurement & Supply Forecasting Agent
**Trigger:** Schedule (Daily)
**Workflow:** Fetch project schedules + inventory levels → split projects → batch → GPT-4o analyze material requirements vs stock + supplier lead times → if shortages: create bulk POs + alert PM / else: log adequate supply + send daily summary
**Use Case:** Prevents schedule delays by daily cross-referencing upcoming material needs against inventory, factoring in supplier lead times and auto-generating urgent purchase orders.
**n8n:** https://aravind5.app.n8n.cloud/workflow/aby1Dzm36hwcWkHM
**Credentials:** OpenAI API Key · Gmail OAuth2 · PM Platform API Bearer Token · Inventory System API Bearer Token · Procurement System API Bearer Token

---

## Tech Stack
- **Platform:** n8n (cloud or self-hosted)
- **AI:** OpenAI GPT-4o via `@n8n/n8n-nodes-langchain.agent` v3.1
- **Structured Output:** `@n8n/n8n-nodes-langchain.outputParserStructured` v1.3
- **Notifications:** Gmail v2.2
- **Patterns:** SplitInBatches + nextBatch, SplitOut, ifElse, switchCase

## Setup
1. Import each JSON into your n8n instance
2. Replace placeholder URLs (marked `<__PLACEHOLDER_VALUE__...>`) with your actual endpoints
3. Configure credentials listed per agent above
4. Activate the workflow
