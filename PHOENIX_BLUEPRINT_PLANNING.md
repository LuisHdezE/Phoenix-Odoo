# Phoenix · Blueprint Planning Baseline

**Repository:** `LuisHdezE/Phoenix-Odoo`  
**Document status:** Planning proposal  
**Implementation status:** NOT STARTED  
**Configuration status:** NOT STARTED  
**Stop gate:** `READY_FOR_CONFIGURATION`  
**Human authority:** Luis Hernández  
**Planning date:** 2026-10-05

---

## 1. Purpose

This document applies the latest multi-agent Software Development Blueprint work to Phoenix without starting implementation.

Phoenix is an Odoo ERP laboratory whose final result must be a professional distribution-management system and, at the same time, a learning path completed by the human developer.

The central rule is:

> Blueprint and AI may analyze, plan, explain, review and audit. Luis writes the application and performs the configuration in order to learn Odoo.

No agent or assistant should silently convert Phoenix into an AI-generated implementation.

---

# 2. Blueprint baseline used by Phoenix

Phoenix adopts the current stable Blueprint governance plus the latest multi-agent proposals as a **planning methodology snapshot**.

Repository:

`LuisHdezE/SoftwareDevelopmentBlueprint`

Stable Blueprint:

- `VERSION = 0.5.4`

Development line:

- `DEVELOPMENT_VERSION = 0.5.5-dev`

Multi-agent proposal set considered for Phoenix:

- PR #50 — Agent role foundation: Analyst + Planner
- PR #51 — Architect + Database + Backend + Frontend
- PR #52 — QA + Security + Documentation + Auditor
- PR #53 — Orchestrator
- PR #54 — Agent protocol contracts / Task Packet / Handoff / orchestration state
- PR #56 — Agent workflow integration
- PR #57 — Fail-closed workflow validation
- PR #58 — Public Discoverability specialist
- PR #59 — Conditional specialist routing
- PR #60 — Public Discoverability fail-closed validation

These proposals remain proposals in the Blueprint repository. Phoenix uses their latest behavior conceptually but does not copy their files, schemas or workflows into this repository during the planning phase.

## Governance rules inherited

Phoenix adopts these rules:

1. human authority remains final;
2. no agent self-certifies work outside its role;
3. Orchestrator coordinates but is not a super-agent;
4. Analyst defines WHAT;
5. Planner decomposes work;
6. Architect defines technical boundaries;
7. Database, Backend and Frontend own their specialties;
8. QA and Security validate independently;
9. Documentation reflects actual state;
10. Auditor checks evidence and scope;
11. a PASS does not imply human approval;
12. exact baseline and exact candidate state matter;
13. fail closed when required evidence is missing;
14. use the smallest honest set of agents;
15. specialist agents are conditional by applicability.

---

# 3. Phoenix orchestration

## Task classification

Current planning task:

```text
NEW_PRODUCT
+ ERP_IMPLEMENTATION_PLANNING
+ ARCHITECTURE_DEFINITION
+ LEARNING_PROGRAM_DESIGN
```

No implementation task is authorized.

## Core agent participation

| Agent | Planning status | Purpose in Phoenix |
|---|---|---|
| Orchestrator | REQUIRED | sequence planning, gates and stop conditions |
| Analyst | REQUIRED | business processes, requirements, acceptance criteria |
| Planner | REQUIRED | roadmap and executable task graph |
| Architect | REQUIRED | Odoo boundaries, extension strategy, integration and deployment architecture |
| Database | REQUIRED | persistence impact, extension data and reporting needs |
| Backend | REQUIRED FOR PLANNING | define future Python/Odoo addon responsibilities |
| Frontend | REQUIRED FOR PLANNING | define use of standard views vs custom OWL/dashboard work |
| QA | REQUIRED | test strategy and learning checkpoints |
| Security | REQUIRED | roles, ACL, record rules, integrations and deployment trust boundaries |
| Documentation | REQUIRED | project memory and learner documentation |
| Auditor | REQUIRED | final planning audit before the stop gate |

## Conditional specialist

### Search & AI Discoverability

Current state:

```text
NOT_APPLICABLE
```

Reason:

Phoenix is currently an authenticated ERP application and not a public indexable storefront or marketing site.

If a public portfolio/landing surface is later added, that surface must be classified independently. A future `PUBLIC_INDEXABLE` surface would make the Search & AI Discoverability specialist REQUIRED before public release.

Social, Meta Ads and paid growth are not required for Phoenix.

---

# 4. Human-learning constraint

Phoenix has a special project constraint:

```text
IMPLEMENTER = HUMAN
AI ROLE = TUTOR + REVIEWER + ANALYST + AUDITOR
```

## AI may

- explain Odoo concepts;
- explain Python/Odoo APIs;
- explain error messages;
- help inspect documentation;
- propose pseudocode;
- review code written by Luis;
- review XML written by Luis;
- review models, permissions and tests;
- identify defects;
- explain how to debug;
- ask diagnostic questions;
- compare alternatives;
- audit a PR;
- suggest exercises;
- explain accounting effects.

## AI must not, by default

- implement whole Phoenix features for Luis;
- generate complete production modules and present them as finished work;
- silently write configuration files that bypass learning;
- perform the learning exercises on Luis's behalf;
- turn a lesson into an autonomous coding agent task.

Small illustrative snippets are acceptable when they teach a concept, but the learner must reproduce/adapt the concept himself.

---

# 5. Product definition

## Product

**Phoenix — ERP de Distribución sobre Odoo**

## Business profile

Phoenix models a small/medium distributor that:

- manages prospects and customers;
- sells products;
- purchases from suppliers;
- maintains warehouse inventory;
- supports sales on credit;
- tracks accounts receivable;
- tracks accounts payable;
- manages cash and banks;
- records double-entry accounting;
- evaluates supplier performance;
- enforces purchase approval levels;
- enforces customer credit controls;
- exposes/consumes integration APIs;
- presents management indicators.

---

# 6. Actors

Primary actors:

- Salesperson
- Sales Supervisor
- Buyer
- Purchase Supervisor
- Warehouse Operator
- Treasury User
- Accountant
- Manager
- Administrator
- External Integration Client
- External Data Provider

System actors:

- Odoo Scheduler
- PostgreSQL
- External API
- Backup process

---

# 7. Core end-to-end processes

## P-BIZ-01 Lead to Cash

```text
Lead / Opportunity
→ Quotation
→ Sales Order
→ Stock reservation
→ Delivery
→ Customer Invoice
→ Accounts Receivable
→ Customer Payment
→ Bank/Cash
→ Reconciliation
→ Accounting
```

## P-BIZ-02 Procure to Pay

```text
Need / Replenishment
→ RFQ
→ Purchase Order
→ Approval when required
→ Receipt
→ Vendor Bill
→ Accounts Payable
→ Supplier Payment
→ Reconciliation
→ Accounting
```

## P-BIZ-03 Credit Control

```text
Sales Order
→ compute exposure
→ validate credit limit / overdue rules
→ allow OR block
→ approval exception if authorized
→ trace decision
```

## P-BIZ-04 Supplier Evaluation

```text
Purchase history
+ delivery performance
+ price / quality signals
+ returns / exceptions
→ deterministic score
→ management view
```

## P-BIZ-05 Management Review

```text
Sales
+ margin
+ purchasing
+ inventory
+ AR
+ AP
+ cash/bank
→ dashboard
→ drill-down
```

---

# 8. Functional scope

## CRM

- leads/opportunities;
- stages;
- activities;
- expected revenue;
- salesperson assignment;
- conversion into quotation;
- pipeline reporting.

## Sales

- quotations;
- sales orders;
- customers;
- products;
- pricelists where justified;
- payment terms;
- delivery status;
- invoicing;
- sales reporting.

## Purchases

- suppliers;
- RFQs;
- purchase orders;
- receipts;
- vendor bills;
- purchase reporting;
- configurable approval thresholds.

## Inventory

- products;
- product categories;
- warehouse;
- locations;
- receipts;
- deliveries;
- internal movements where needed;
- inventory adjustments;
- reorder rules;
- stock availability;
- inventory valuation;
- low-stock monitoring.

## Accounts Receivable

- customer invoices;
- due dates;
- partial payments;
- open balance;
- overdue balance;
- aging;
- customer statement;
- reconciliation.

## Accounts Payable

- vendor bills;
- due dates;
- partial payments;
- open balance;
- overdue balance;
- aging;
- payment planning;
- reconciliation.

## Treasury

- cash journal;
- bank journals;
- receipts;
- payments;
- transfers where needed;
- reconciliation;
- cash visibility.

## Accounting

- chart of accounts;
- journals;
- journal entries;
- receivable/payable accounts;
- revenue;
- expenses;
- inventory accounting where supported by chosen configuration;
- taxes for the laboratory dataset;
- trial balance;
- general ledger;
- balance sheet;
- profit and loss;
- cash flow/reporting strategy.

## Management

- sales KPIs;
- purchasing KPIs;
- margin;
- AR/AP exposure;
- stock valuation;
- low stock;
- supplier score;
- operational alerts.

---

# 9. Standard vs configuration vs custom vs integration

Phoenix follows the rule:

```text
STANDARD FIRST
→ CONFIGURATION
→ EXTENSION
→ CUSTOM MODULE
→ EXTERNAL INTEGRATION
```

## Initial classification matrix

| Capability | Initial classification | Notes |
|---|---|---|
| Contacts | STD/CFG | reuse Odoo contacts |
| CRM pipeline | STD/CFG | configure stages and workflow |
| Quotations / Sales Orders | STD/CFG | standard sales flow |
| Purchase RFQ / PO | STD/CFG | standard purchasing flow |
| Inventory receipt/delivery | STD/CFG | standard stock flow |
| Reordering | STD/CFG | standard where sufficient |
| Customer invoices | STD/CFG | standard accounting/invoicing core |
| Vendor bills | STD/CFG | standard accounting/invoicing core |
| AR/AP balances | STD/CFG | standard accounting model |
| Payments | STD/CFG | standard |
| Journals / double entry | STD/CFG | standard |
| Financial reports | STD/CFG/OCA | validate Community capability; use OCA only where justified |
| Customer credit limit | CUS | Phoenix addon |
| Overdue-sale blocking | CUS | Phoenix addon |
| Credit exception approval | CUS | Phoenix addon |
| Purchase threshold approval | CUS | Phoenix addon |
| Supplier scoring | CUS | Phoenix addon |
| Management dashboard | STD/REP/CUS | use standard reporting first; OWL/custom only when justified |
| External data consumption | INT | Phoenix integration addon |
| External API exposure | INT/CUS | documented secure interface |
| Backups | DEVOPS | deployment responsibility |
| Uruguay fiscal certification | OUT | explicitly not claimed in v1 |

The matrix must be revalidated during the learner's configuration phase before any custom code is written.

---

# 10. Version decision

## Selected training baseline

```text
Odoo 19 Community
```

## Why Odoo 19 instead of Odoo 20

As of October 2026, Odoo 20 is the newest major release, published in September 2026.

Phoenix intentionally targets Odoo 19 because:

- it remains modern and relevant;
- its official developer documentation is mature;
- there is significantly more Odoo 19 training material available;
- OCA has active 19.0 repositories;
- `OCA/account-financial-reporting` has a 19.0 branch and maintained modules;
- the official Docker image supports Odoo 19 on `arm64/v8`, useful for Oracle Ampere A1;
- it reduces bleeding-edge migration noise while Luis is learning the framework.

Odoo 20 should be treated as a future upgrade exercise, not the learning baseline.

---

# 11. Edition and dependency policy

## Baseline

```text
Odoo Community
```

Reasons:

- free/open-source baseline;
- self-hostable;
- supports custom addons;
- suitable for GitHub portfolio work;
- compatible with Oracle Cloud deployment;
- avoids requiring a paid Enterprise subscription for the laboratory.

## OCA policy

OCA dependencies are allowed only after:

1. identifying a genuine gap;
2. validating Odoo 19 compatibility;
3. reviewing license;
4. reviewing maintenance/health;
5. documenting why Phoenix does not implement the feature itself;
6. pinning the dependency.

Candidate:

- `OCA/account-financial-reporting` 19.0 for reports absent or insufficient in the chosen Community setup.

OCA must not become a shortcut that prevents understanding the underlying Odoo model.

---

# 12. Planned addon boundaries

The exact addons will be created by Luis during the course.

Proposed target structure:

```text
custom_addons/
├── phoenix_credit_control
├── phoenix_purchase_approval
├── phoenix_supplier_score
├── phoenix_management_dashboard
└── phoenix_integration
```

## phoenix_credit_control

Responsibilities:

- customer credit limit;
- computed exposure;
- overdue condition;
- block/release sales order;
- approval exception;
- audit trail.

## phoenix_purchase_approval

Responsibilities:

- configurable approval thresholds;
- approval level;
- approval request/state;
- separation of requester/approver where required;
- audit trail.

## phoenix_supplier_score

Responsibilities:

- deterministic supplier metrics;
- scoring configuration;
- calculated score;
- explainable score breakdown.

## phoenix_management_dashboard

Responsibilities:

- management KPIs not sufficiently covered by standard views;
- drill-down to authoritative records;
- no duplicate source of truth.

This addon should only be created after standard Odoo reporting has been explored.

## phoenix_integration

Responsibilities:

- outbound/consumed external API;
- inbound interface/API where required;
- authentication;
- validation;
- retries/idempotency where applicable;
- integration logs without secret leakage.

---

# 13. Data planning

Phoenix should extend standard models rather than duplicate them.

Likely extension areas:

## Customer

Possible custom data:

- credit limit;
- risk classification;
- credit-block flag;
- credit override metadata.

## Purchase order / approval

Possible data:

- approval level;
- approval state;
- approved by;
- approved at;
- approval reason.

## Supplier metrics

Possible data:

- calculated delivery performance;
- price metric;
- quality/return metric;
- score;
- last calculation time.

## Integration

Possible data:

- external identifier when necessary;
- synchronization status;
- last synchronization timestamp;
- correlation key;
- non-sensitive error summary.

### Data rule

Do not persist values only because a screen wants to display them. Prefer computed values when authoritative source records already contain the required information.

---

# 14. Architecture plan

## Logical architecture

```text
Browser
   ↓
Odoo Web Client
   ↓
Odoo Server
   ├── Standard Apps
   ├── Phoenix Addons
   ├── OCA Addons (only approved)
   └── Integration Layer
   ↓
PostgreSQL
```

External integration:

```text
External Provider
      ↕
Phoenix Integration Addon
      ↕
Odoo Models / Services
```

## Framework boundaries

Odoo's architecture is framework-owned. Phoenix will not impose Clean Architecture mechanically.

Instead:

- standard Odoo model inheritance is preferred;
- business invariants should live at authoritative server-side boundaries;
- views remain declarative where possible;
- service abstractions may be introduced for integrations or complex logic;
- controllers are used only for justified HTTP/API surfaces;
- direct core modification is prohibited.

---

# 15. Interface strategy

Default priority:

1. standard Odoo list/form/search/kanban/pivot/graph views;
2. inherited standard views;
3. custom QWeb where needed;
4. OWL only for user experiences that standard views cannot express well.

This prevents Phoenix from becoming a frontend rewrite of Odoo.

Planned custom UI candidates:

- management dashboard;
- approval visual cues;
- credit-risk indicators.

---

# 16. API strategy

Phoenix must demonstrate both integration directions by project end.

## External API consumption

Candidate learning use case:

- retrieve an exchange rate or other external business datum;
- validate response;
- map to Odoo;
- log execution;
- handle provider failure safely.

The definitive provider will be chosen during the course.

## Phoenix API

Candidate operations:

- query products;
- query stock availability;
- query order status;
- create a controlled integration request.

API requirements:

- authentication;
- authorization;
- input validation;
- stable error contract;
- idempotency when writes can be retried;
- rate/abuse consideration;
- no secret leakage in logs;
- documentation.

---

# 17. Security plan

## Roles

- Salesperson
- Sales Supervisor
- Buyer
- Purchase Supervisor
- Warehouse Operator
- Treasury
- Accountant
- Manager
- Administrator
- Integration Principal

## Required learning areas

- groups;
- access control lists;
- record rules;
- field/view visibility vs true authorization;
- sudo and privilege escalation risks;
- secrets;
- CSRF/HTTP controller concerns;
- API authentication;
- auditability.

## Key rules

- UI hiding is not authorization;
- seller cannot approve own credit exception unless explicitly governed;
- purchase requester should not automatically be the high-value approver;
- non-financial users should not modify accounting entries;
- PostgreSQL must not be publicly exposed in production;
- production secrets must not be committed.

---

# 18. QA plan

Phoenix testing will cover:

## Functional

- Lead-to-Cash;
- Procure-to-Pay;
- AR/AP;
- payments;
- reconciliation;
- credit limits;
- purchase approval;
- supplier score;
- integrations.

## Technical

- Python model tests;
- Odoo transactional tests;
- access-right tests;
- record-rule tests;
- integration failure tests;
- regression tests.

## Accounting assertions

For representative scenarios, verify both:

1. operational state;
2. resulting accounting state.

Example:

```text
invoice posted
!= only "invoice looks correct"

Must also validate:
receivable/payable entry
counterpart entry
payment
reconciliation
remaining balance
```

---

# 19. Deployment plan

Production-like demo target:

```text
Oracle Cloud Infrastructure
└── Ampere A1 ARM VM
    └── Ubuntu 24.04 LTS
        └── Docker / Compose
            ├── Odoo 19
            ├── PostgreSQL
            └── Nginx
```

Public edge:

```text
Internet
→ DNS
→ HTTPS
→ Nginx
→ Odoo
```

Database remains private to the host/container network.

## Why Oracle Ampere A1

Oracle Always Free documentation currently provides Ampere A1 resources equivalent to up to:

- 2 OCPUs;
- 12 GB memory;

within the Always Free tenancy limits.

Odoo's official Docker image supports:

- amd64;
- arm64/v8;
- ppc64le.

Therefore the planned Odoo 19 Docker deployment is compatible with Oracle A1 ARM architecture.

## Production requirements

The future deployment exercise must include:

- SSH key access;
- firewall;
- ports 80/443 public;
- PostgreSQL not public;
- HTTPS;
- persistent PostgreSQL volume;
- persistent Odoo filestore;
- secrets outside Git;
- database master password;
- `proxy_mode` review;
- backup;
- restore test;
- logs;
- restart policy;
- deployment runbook.

---

# 20. Learning-first delivery strategy

Phoenix will be built twice conceptually:

## First pass: functional understanding

Luis performs the process manually using standard Odoo.

Question:

> Can I operate the business flow and explain what Odoo is doing?

## Second pass: technical extension

Only after understanding the standard behavior does Luis extend it.

Question:

> What is genuinely missing, and where is the correct extension point?

This order prevents custom code from replacing features that Odoo already provides.

---

# 21. Future task graph

The implementation roadmap exists now only as a plan.

```text
L0 ERP/Odoo orientation
  ↓
L1 Local environment
  ↓
L2 Standard business configuration
  ↓
L3 Standard E2E flows
  ↓
L4 Odoo development fundamentals
  ↓
L5 Credit Control addon
  ↓
L6 Purchase Approval addon
  ↓
L7 Supplier Score addon
  ↓
L8 Reporting/Dashboard
  ↓
L9 Integrations/API
  ↓
L10 Security hardening
  ↓
L11 Automated tests
  ↓
L12 Production deployment
  ↓
L13 Oracle Cloud demo
  ↓
L14 Portfolio/Audit
```

The detailed learner roadmap is maintained separately in `PHOENIX_LEARNING_ROADMAP.md`.

---

# 22. Planning acceptance criteria

The planning phase is complete when all of the following are explicit:

- [x] product purpose;
- [x] business actors;
- [x] business processes;
- [x] functional modules;
- [x] AR/AP scope;
- [x] accounting scope;
- [x] standard/custom/integration strategy;
- [x] Odoo baseline version;
- [x] edition policy;
- [x] addon boundaries;
- [x] data extension strategy;
- [x] security roles;
- [x] QA strategy;
- [x] integration strategy;
- [x] deployment target;
- [x] Oracle Cloud target;
- [x] learner ownership rule;
- [x] roadmap to professional completion.

---

# 23. STOP GATE

## Gate

```text
READY_FOR_CONFIGURATION
```

Meaning:

- analysis is complete enough to begin learning/configuration;
- architecture direction is clear;
- no Odoo instance has been configured by Blueprint/AI;
- no Phoenix addon has been generated;
- no deployment has been performed;
- no implementation branch exists.

## Required behavior after this document

STOP.

The next action belongs to Luis as learner.

When Luis explicitly begins the course, AI may act as tutor/reviewer for the current lesson only.

AI must not skip ahead and implement future modules.

---

# 24. Human handoff

```yaml
handoff:
  project: Phoenix
  state: READY_FOR_CONFIGURATION
  implementation_started: false
  configuration_started: false
  learner: Luis
  ai_role:
    - tutor
    - reviewer
    - analyst
    - debugger
    - auditor
  ai_default_implementer: false
  next_action:
    owner: HUMAN
    action: Start PHOENIX_LEARNING_ROADMAP at Module 0
```
