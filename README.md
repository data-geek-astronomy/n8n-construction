# n8n Construction AI Agents

> 3 production-ready n8n workflow agents that automate OSHA safety compliance, subcontractor invoice reconciliation, and material procurement forecasting.

![status](https://img.shields.io/badge/status-production--ready-brightgreen)
![license](https://img.shields.io/badge/license-MIT-blue)
![built with](https://img.shields.io/badge/built%20with-n8n%20%2B%20GPT--4o-orange)

---

## ✨ Agents

### C-7: Site Safety Compliance & OSHA Reporting
**Trigger:** Schedule → runs daily

> **Problem:** General contractors like Turner Construction and Bechtel manage hundreds of daily site inspections, but OSHA reporting is manual, error-prone, and often late — risking fines up to $15,625 per violation.
> **Built:** A daily batch agent that analyzes inspection reports against 29 CFR 1926 Construction Standards using GPT-4o, auto-files OSHA forms, and alerts project managers with corrective action plans.
> **Solved:** Eliminates missed OSHA filing deadlines and ensures every serious violation is reported, documented, and assigned a corrective action within 24 hours.

```
Daily Scheduler
      ↓
Fetch Inspection Reports
      ↓
Split + Batch
      ↓
GPT-4o Analyzes vs 29 CFR 1926
      ↓
  OSHA Reportable?
   Yes           No
    ↓             ↓
File OSHA     Log Minor
Report +      Violation
Alert PM
```

✅ Classifies violations by severity (other/serious/willful/repeat)
✅ Auto-files OSHA 300/301 reports with correct regulatory citations
✅ Sends PM corrective action plan with estimated fine range

**Use Cases:**
- **Turner Construction** — automate OSHA 300 log updates across 1,500+ active project sites
- **Bechtel** — flag fall protection and PPE violations for same-day corrective action
- **Procore-integrated GCs** — pull inspection data from Procore and auto-file to OSHA

**n8n:** https://aravind5.app.n8n.cloud/workflow/yV1moFLC09gC4g6C

---

### C-8: Subcontractor Invoice Reconciliation & Payment
**Trigger:** Schedule → runs weekly

> **Problem:** Construction finance teams at Skanska and Hensel Phelps manually verify hundreds of subcontractor invoices each month against Schedules of Values — a process that takes days and frequently overpays due to overbilling.
> **Built:** A weekly batch agent that fetches pending invoices, retrieves the contract SOV, and uses GPT-4o to reconcile every line item, validate compliance docs, and calculate retainage.
> **Solved:** Catches overbilling and missing compliance documents (lien waivers, certified payroll) before payment is issued — reducing payment disputes and protecting lien rights.

```
Weekly Scheduler
      ↓
Fetch Pending Invoices (ERP)
      ↓
Split + Batch
      ↓
Fetch Contract SOV
      ↓
GPT-4o Reconciles Line Items
+ Validates Compliance Docs
      ↓
  Approved?
  Yes      No
   ↓        ↓
Create    Flag for
Payment   Review +
Voucher   Notify Sub
+ Notify Sub
```

✅ Verifies every line item against the contract Schedule of Values
✅ Calculates correct retainage automatically
✅ Flags missing lien waivers and certified payroll before payment

**Use Cases:**
- **Skanska USA** — reconcile subcontractor invoices across $4B+ annual construction volume
- **Hensel Phelps** — catch certified payroll gaps on federally-funded projects (Davis-Bacon compliance)
- **Procore + Sage 300 CRE** — pull SOV from Procore and push approved vouchers to Sage ERP

**n8n:** https://aravind5.app.n8n.cloud/workflow/lQhFarz4A38f2flj

---

### C-9: Material Procurement & Supply Forecasting
**Trigger:** Schedule → runs daily

> **Problem:** Project managers at Whiting-Turner and DPR Construction frequently discover material shortages only when crews arrive on-site, causing idle time that costs $1,800–$3,000/hour per trade crew.
> **Built:** A daily agent that cross-references upcoming activity schedules against live inventory, factors in supplier lead times using GPT-4o, and auto-generates purchase orders for shortages before they cause delays.
> **Solved:** Surfaces material gaps 5–10 days before they become schedule delays, giving procurement teams time to source and deliver without stopping work.

```
Daily Scheduler
      ↓
Fetch Project Schedules + Inventory
      ↓
Split + Batch (per project)
      ↓
GPT-4o Cross-References Requirements
vs Stock + Lead Times
      ↓
  Critical Shortage?
   Yes           No
    ↓             ↓
Create Bulk    Send Daily
Purchase Orders  Summary
+ Alert PM     to PM
```

✅ Daily gap analysis: material needs vs live inventory
✅ Accounts for supplier lead times vs activity start dates
✅ Auto-generates urgent POs before delays occur

**Use Cases:**
- **Whiting-Turner** — prevent steel and concrete shortages on high-rise structural phases
- **DPR Construction** — daily MEP material checks for fast-track data center builds
- **Procore + Oracle NetSuite** — pull schedules from Procore, push POs to NetSuite automatically

**n8n:** https://aravind5.app.n8n.cloud/workflow/aby1Dzm36hwcWkHM

---

## 🚀 Quick Start

### Prerequisites
- n8n cloud account
- OpenAI API key (GPT-4o)
- Gmail OAuth2 credentials

### Deploy
1. Import the JSON file into your n8n instance
2. Replace `<__PLACEHOLDER_VALUE__...>` URLs with your actual API endpoints
3. Configure credentials per the table below
4. Activate the workflow

| Agent | Credentials |
|-------|-------------|
| C-7   | OpenAI · Gmail · Safety Platform API · OSHA Reporting API |
| C-8   | OpenAI · Gmail · ERP System API |
| C-9   | OpenAI · Gmail · PM Platform API · Inventory API · Procurement API |

---

## 🧑‍💻 Author
**Aravind Kumar** · GitHub: [@data-geek-astronomy](https://github.com/data-geek-astronomy)
Portfolio: Building AI agents for enterprise automation

## 📄 License
MIT
