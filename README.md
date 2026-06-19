# n8n Construction AI Agents

> 3 production-ready n8n workflow agents that automate OSHA safety compliance, subcontractor invoice reconciliation, and material procurement forecasting.

![status](https://img.shields.io/badge/status-production--ready-brightgreen)
![license](https://img.shields.io/badge/license-MIT-blue)
![built with](https://img.shields.io/badge/built%20with-n8n%20%2B%20GPT--4o-orange)

---

## 🎯 Problem Statement

Construction firms lose time and face legal risk from manual processes:
- Safety violations go unreported or are filed incorrectly
- Subcontractor invoices are paid without proper SOV verification
- Material shortages cause costly schedule delays

These agents automate all three compliance and operations workflows.

---

## ✨ Agents

### C-7: Site Safety Compliance & OSHA Reporting
**Trigger:** Schedule → runs daily

```
Daily Scheduler
      ↓
Fetch Inspection Reports (pending review)
      ↓
Split + Batch (1 inspection at a time)
      ↓
GPT-4o Analyzes Violations
(against 29 CFR 1926 Construction Standards)
      ↓
  OSHA Reportable?
   Yes           No
    ↓             ↓
File OSHA     Log Minor
Incident      Violation
Report
+ Alert PM
(Gmail)
```

✅ Classifies violations by severity (other/serious/willful/repeat)
✅ Auto-files OSHA 300/301 reports with correct citations
✅ Sends PM action items with estimated fine range

**n8n:** https://aravind5.app.n8n.cloud/workflow/yV1moFLC09gC4g6C

---

### C-8: Subcontractor Invoice Reconciliation & Payment
**Trigger:** Schedule → runs weekly

```
Weekly Scheduler
      ↓
Fetch Pending Subcontractor Invoices (ERP)
      ↓
Split + Batch (1 invoice at a time)
      ↓
Fetch Contract Schedule of Values (SOV)
      ↓
GPT-4o Reconciles Line Items
(SOV match, retainage, lien waiver, certified payroll)
      ↓
  Approved?
  Yes      No
   ↓        ↓
Create    Flag for
Payment   Manual Review
Voucher
+ Notify
Sub (Gmail)
```

✅ Verifies every line item against the contract SOV
✅ Calculates correct retainage automatically
✅ Flags missing compliance docs (lien waivers, certified payroll)

**n8n:** https://aravind5.app.n8n.cloud/workflow/lQhFarz4A38f2flj

---

### C-9: Material Procurement & Supply Forecasting
**Trigger:** Schedule → runs daily

```
Daily Scheduler
      ↓
Fetch Active Project Schedules
      ↓
Fetch Current Inventory Levels
      ↓
Split + Batch (1 project at a time)
      ↓
GPT-4o Cross-References Requirements vs Stock
(accounts for supplier lead times + activity dates)
      ↓
  Critical Shortage?
   Yes           No
    ↓             ↓
Create Bulk    Log Adequate
Purchase Orders  Supply
+ Alert PM     + Daily Summary
(Gmail)        to PM (Gmail)
```

✅ Compares material needs against live inventory daily
✅ Factors in supplier lead times vs activity start dates
✅ Auto-generates urgent POs before delays can occur

**n8n:** https://aravind5.app.n8n.cloud/workflow/aby1Dzm36hwcWkHM

---

## 🚀 Quick Start

### Prerequisites
- n8n cloud account (free tier works)
- OpenAI API key (GPT-4o)
- Gmail account for notifications

### Deploy
1. Import the relevant JSON file into your n8n instance
2. Replace placeholder URLs (`<__PLACEHOLDER_VALUE__...>`) with your API endpoints
3. Add credentials (see below)
4. Activate the workflow

### Credentials Required

| Agent | Credentials |
|-------|-------------|
| C-7   | OpenAI, Gmail, Safety Platform API, OSHA Reporting API |
| C-8   | OpenAI, Gmail, ERP System API |
| C-9   | OpenAI, Gmail, PM Platform API, Inventory API, Procurement API |

---

## 🧑‍💻 Author
**Aravind Kumar** · GitHub: [@data-geek-astronomy](https://github.com/data-geek-astronomy)

## 📄 License
MIT
