# Phoenix · Learning Roadmap
## De cero en Odoo a una implementación ERP profesional

**Project:** Phoenix  
**Target:** Odoo 19 Community  
**Learner/Developer:** Luis Hernández  
**AI role:** Tutor, reviewer, debugger, analyst and auditor  
**Deployment target:** Oracle Cloud Infrastructure Always Free / Ampere A1  
**End result:** Phoenix running as a professional public demo with CRM, Sales, Purchases, Inventory, AR, AP, Treasury, Accounting, custom addons, API integration, security, tests, backups and documentation.

---

# 1. Philosophy

This is not a watch-only course.

Every learning block follows:

```text
WATCH
  ↓
READ
  ↓
EXPLAIN
  ↓
BUILD
  ↓
TEST
  ↓
REVIEW
  ↓
COMMIT
```

A module is not complete because the video ended.

It is complete when Luis can:

1. explain the concept;
2. reproduce it without copying blindly;
3. apply it to Phoenix;
4. test it;
5. diagnose a broken version;
6. commit the evidence.

---

# 2. AI tutoring contract

During this roadmap, AI should behave like a senior mentor.

## Preferred interaction

Luis:

> I am in Module 11. My computed field is not recalculating. Here is my code and the error.

AI:

- explains likely causes;
- points to relevant framework behavior;
- helps isolate the problem;
- reviews the fix written by Luis.

## Avoid by default

Luis:

> Implement the full credit-control addon.

AI should remind the learner constraint and instead break the task into learning steps unless Luis explicitly overrides that rule.

The goal is competence, not merely a green repository.

---

# 3. Recommended rhythm

This roadmap is self-paced.

A realistic range for someone already experienced in backend development is approximately:

```text
160–240 focused hours
```

The exact duration is intentionally not tied to calendar weeks.

Progress is gate-based, not time-based.

---

# 4. Canonical sources

## Official Odoo 19 Developer Documentation

- https://www.odoo.com/documentation/19.0/developer.html
- https://www.odoo.com/documentation/19.0/developer/tutorials.html
- https://www.odoo.com/documentation/19.0/developer/tutorials/server_framework_101.html
- https://www.odoo.com/documentation/19.0/developer/tutorials/discover_js_framework.html
- https://www.odoo.com/documentation/19.0/developer/howtos.html

## Official Odoo 19 Administration

- https://www.odoo.com/documentation/19.0/administration.html
- https://www.odoo.com/documentation/19.0/administration/on_premise/source.html
- https://www.odoo.com/documentation/19.0/administration/on_premise/packages.html

## Accounting

- https://www.odoo.com/documentation/19.0/applications/finance/accounting.html
- https://www.odoo.com/documentation/19.0/applications/finance/accounting/get_started.html

## OCA

- https://github.com/OCA/account-financial-reporting/tree/19.0

## Oracle Cloud

- https://docs.oracle.com/en-us/iaas/Content/FreeTier/freetier.htm
- https://docs.oracle.com/en-us/iaas/Content/FreeTier/freetier_topic-Always_Free_Resources.htm

The official documentation is authoritative when a YouTube video differs from the target version.

---

# 5. Curated YouTube spine

These videos form the audiovisual spine of the course.

## Development overview

**Odoo 19 Development Course (01) — Introduction: Agenda**  
Muhammad Nasser  
https://www.youtube.com/watch?v=cf6mG45bd4o

Use it as a map of technical topics, not as a substitute for the official tutorials.

## Development environment / Docker

**Odoo 19 + Docker + Ubuntu 24.04: Complete Development Installation**  
Devigo Explicaciones ERPs  
https://www.youtube.com/watch?v=MPxp5iHFSAg

## Views

**Odoo 19 course for beginner and intermediate developers: All about Views in Odoo**  
Time to coode  
https://www.youtube.com/watch?v=bLtiMOwHWos

## CRM

**Odoo CRM Tutorial | How To Use Odoo CRM (Step-by-Step)**  
Tutorials by Manizha & Ryan  
https://www.youtube.com/watch?v=iO_dgILDUr8

## Sales

**Odoo 19 Sales Overview | Odoo 19 Sales Guide**  
Cybrosys Technologies  
https://www.youtube.com/watch?v=5dCZvuLelMY

Optional deeper sales webinar:

https://www.youtube.com/watch?v=TVBs7izCRwI

## Purchase

**Purchase In Odoo 19 | Purchase Module Overview**  
Cybrosys Technologies  
https://www.youtube.com/watch?v=D7KPS8yCej0

## Inventory

**Inventory In Odoo 19 | Odoo 19 Inventory Guide**  
Cybrosys Technologies  
https://www.youtube.com/watch?v=ZlvbYJEGJts

## Accounting end-to-end

**Odoo 19 Accounting Full Tutorial | Complete Accounting Workflow Step-by-Step**  
Katy Links Training  
https://www.youtube.com/watch?v=AgWVvBF-XzU

## Bank reconciliation

**Bank Reconciliation in Odoo 19 | Odoo Accounting**  
Pinky Shah  
https://www.youtube.com/watch?v=fsX_ijWIHys

---

# 6. PHASE A — ERP and Odoo foundations

---

## Module 0 — Understand Phoenix before touching Odoo

### Objective

Understand the company and processes Phoenix is intended to model.

### Study

Read:

- `PHOENIX_SPEC_MASTER.md`
- `PHOENIX_BLUEPRINT_PLANNING.md`

### Learn

Be able to explain:

- Lead-to-Cash;
- Procure-to-Pay;
- AR vs AP;
- inventory vs accounting;
- cash vs profit;
- operational document vs accounting document;
- standard feature vs customization.

### Exercise

On paper or Markdown, manually walk through:

1. one sale;
2. one purchase;
3. one customer payment;
4. one supplier payment.

### Gate

`BUSINESS_MODEL_UNDERSTOOD`

Do not install Odoo yet.

---

## Module 1 — Accounting essentials for an Odoo developer

### Objective

Understand enough accounting to reason about Phoenix correctly.

### Topics

- assets;
- liabilities;
- equity;
- income;
- expenses;
- debit/credit;
- chart of accounts;
- journal;
- journal entry;
- receivable;
- payable;
- accrual;
- payment;
- reconciliation;
- balance sheet;
- profit and loss;
- cash flow.

### Video

Watch the accounting full tutorial once for conceptual orientation:

https://www.youtube.com/watch?v=AgWVvBF-XzU

At this stage, do not reproduce configuration.

### Exercise

Given:

- purchase 100 units at 100;
- sell 50 units at 180;
- receive customer payment;
- pay supplier;

write the conceptual accounting effects.

### Gate

`ACCOUNTING_CONCEPTS_READY`

---

## Module 2 — Odoo architecture

### Objective

Understand what Odoo actually is before using it.

### Official study

Odoo 19 Server Framework 101:

- Chapter 1 — Architecture Overview
- Chapter 2 — A New Application

Key concepts:

- three-tier architecture;
- Python logic tier;
- PostgreSQL data tier;
- web presentation tier;
- addon/module;
- manifest;
- models;
- data files;
- views.

### Video

https://www.youtube.com/watch?v=cf6mG45bd4o

### Exercise

Draw from memory:

```text
Browser
→ Odoo Web Client
→ Odoo Python Server
→ ORM
→ PostgreSQL
```

Then add where Phoenix addons belong.

### Gate

`ODOO_ARCHITECTURE_UNDERSTOOD`

---

# 7. PHASE B — Environment and standard Odoo

Configuration begins here. This is the point at which the current planning-only phase stops and Luis begins hands-on work.

---

## Module 3 — Build the local Odoo 19 laboratory

### Objective

Create a reproducible local development environment yourself.

### Video

https://www.youtube.com/watch?v=MPxp5iHFSAg

### Official study

- Odoo source installation documentation
- Odoo package installation documentation
- Docker official Odoo image documentation

### Target local architecture

```text
Docker Compose
├── Odoo 19 Community
└── PostgreSQL
```

Later, custom addons will be mounted from the repository.

### Learner tasks

Luis creates:

- local compose setup;
- persistent PostgreSQL volume;
- persistent Odoo data/filestore;
- custom-addons mount;
- environment/secrets strategy;
- dev database.

### Learning requirement

Do not paste a finished compose file from AI.

Build it incrementally and explain every volume, environment variable and port.

### Gate

`LOCAL_ODOO_RUNNING`

Evidence:

- Odoo login;
- DB persists after restart;
- source/custom addon folder visible;
- no secret committed.

---

## Module 4 — Learn Odoo as a functional user

### Objective

Before extending Odoo, learn the standard product.

Install/enable only the apps needed for Phoenix.

Explore:

- Contacts;
- CRM;
- Sales;
- Purchase;
- Inventory;
- Invoicing/Accounting capabilities available in Community.

### Rule

No Phoenix custom code yet.

### Gate

`STANDARD_APPS_DISCOVERED`

---

# 8. PHASE C — Functional ERP implementation

---

## Module 5 — CRM

### Video

https://www.youtube.com/watch?v=iO_dgILDUr8

### Learn

- lead/opportunity;
- pipeline;
- stages;
- activities;
- customer conversion;
- reporting.

### Phoenix exercise

Create demo sales opportunities and move them through the complete pipeline.

### Required explanation

Explain the relationship between:

```text
Opportunity
→ Customer
→ Quotation
```

### Gate

`CRM_FLOW_PASS`

---

## Module 6 — Sales

### Videos

Primary:

https://www.youtube.com/watch?v=5dCZvuLelMY

Deeper webinar:

https://www.youtube.com/watch?v=TVBs7izCRwI

### Learn

- products;
- quotation;
- sales order;
- customer;
- salesperson;
- price;
- payment term;
- delivery dependency;
- invoice dependency.

### Phoenix exercise

Run:

```text
Opportunity
→ Quotation
→ Sales Order
```

Stop before custom credit behavior.

### Gate

`SALES_STANDARD_PASS`

---

## Module 7 — Purchasing

### Video

https://www.youtube.com/watch?v=D7KPS8yCej0

### Learn

- supplier;
- RFQ;
- purchase order;
- vendor pricing;
- receipt;
- bill relationship.

### Phoenix exercise

Run a purchase manually from RFQ through receipt.

### Gate

`PURCHASE_STANDARD_PASS`

---

## Module 8 — Inventory

### Video

https://www.youtube.com/watch?v=ZlvbYJEGJts

### Learn

- warehouse;
- location;
- receipt;
- delivery;
- stock move;
- available vs forecast stock;
- replenishment;
- inventory adjustment;
- valuation concepts.

### Phoenix exercises

Perform:

1. initial stock;
2. receipt;
3. delivery;
4. partial delivery;
5. adjustment;
6. reorder scenario.

### Gate

`INVENTORY_STANDARD_PASS`

---

## Module 9 — Accounting, AR and AP

### Videos

Full workflow:

https://www.youtube.com/watch?v=AgWVvBF-XzU

Reconciliation:

https://www.youtube.com/watch?v=fsX_ijWIHys

### Official study

Odoo 19 Accounting documentation.

### Learn

- customer invoice;
- vendor bill;
- journal;
- receivable;
- payable;
- payment term;
- payment;
- partial payment;
- reconciliation;
- aging;
- financial statements.

### Phoenix exercises

#### AR

```text
Sale
→ Customer Invoice
→ AR
→ Partial Payment
→ Remaining AR
→ Final Payment
→ Reconciliation
```

#### AP

```text
Purchase
→ Vendor Bill
→ AP
→ Partial Payment
→ Remaining AP
→ Final Payment
→ Reconciliation
```

### OCA checkpoint

Only after exploring standard Community reporting, determine whether Phoenix needs:

`OCA/account-financial-reporting`

Do not install it merely because it appears in the plan.

### Gate

`FINANCE_STANDARD_PASS`

---

## Module 10 — Complete standard ERP simulation

### Objective

Run Phoenix without custom modules.

### Scenario

Create a fresh demo dataset and execute:

```text
Lead
→ Quotation
→ Sale
→ Delivery
→ Invoice
→ AR
→ Receipt
→ Reconciliation

Reorder / Need
→ RFQ
→ Purchase
→ Receipt
→ Vendor Bill
→ AP
→ Payment
→ Reconciliation
```

### Required output

Write a short report answering:

- what Odoo already solves;
- what Phoenix still needs;
- which original assumptions were wrong;
- which planned custom features remain justified.

### Gate

`STANDARD_GAP_ANALYSIS_APPROVED`

This gate is mandatory before custom development.

---

# 9. PHASE D — Odoo development fundamentals

---

## Module 11 — Create your first training addon

### Objective

Learn addon anatomy outside Phoenix custom logic.

### Official study

Server Framework 101:

- Chapters 2–7.

### Learn

- `__manifest__.py`;
- `__init__.py`;
- model;
- fields;
- XML data;
- action;
- menu;
- list/form/search;
- Many2one;
- One2many;
- Many2many.

### Rule

Create a disposable learning addon first.

Do not learn module basics inside the business-critical credit-control addon.

### Gate

`ADDON_FUNDAMENTALS_PASS`

---

## Module 12 — ORM, business logic and constraints

### Official study

Server Framework 101:

- computed fields;
- onchange;
- actions;
- constraints;
- inheritance.

### Learn

- recordsets;
- `self`;
- create/write behavior;
- computed fields;
- dependencies;
- stored vs non-stored values;
- constraints;
- ORM searches;
- environment;
- context.

### Exercise

Add business rules to the disposable addon.

Break them intentionally and debug them.

### Gate

`ORM_PASS`

---

## Module 13 — Views, actions and UX

### Video

https://www.youtube.com/watch?v=bLtiMOwHWos

### Learn

- list;
- form;
- search;
- kanban;
- calendar;
- pivot;
- graph;
- actions;
- menus;
- view inheritance;
- domains;
- context.

### Phoenix preparation exercise

Without writing Phoenix logic, inspect the standard customer, sales order and purchase order views in developer mode.

Find likely inheritance points.

### Gate

`VIEW_INHERITANCE_READY`

---

## Module 14 — Security

### Learn

- users;
- groups;
- ACL;
- record rules;
- access errors;
- authorization vs UI hiding;
- `sudo()`;
- multi-company concerns.

### Official study

Odoo tutorial:

**Restrict access to data**

### Exercise

Create roles and restricted records in the disposable addon.

### Gate

`SECURITY_FUNDAMENTALS_PASS`

---

## Module 15 — Testing in Odoo

### Learn

- Odoo test structure;
- transactional tests;
- test data;
- business-rule tests;
- access-right tests;
- regression thinking.

### Official study

Odoo tutorial:

**Safeguard your code with unit tests**

### Rule

From this module forward, every Phoenix custom addon must have automated tests.

### Gate

`TESTING_FUNDAMENTALS_PASS`

---

# 10. PHASE E — Build Phoenix customizations

---

## Module 16 — Phoenix Credit Control

### Goal

Build the first real Phoenix addon yourself.

Target:

`phoenix_credit_control`

### Increment 1

Extend customer with credit policy data.

### Increment 2

Compute current exposure.

### Increment 3

Detect overdue conditions.

### Increment 4

Evaluate sales order before confirmation.

### Increment 5

Block when policy fails.

### Increment 6

Create authorized override workflow.

### Increment 7

Audit who approved, when and why.

### Required tests

- below limit;
- exactly at limit;
- above limit;
- overdue invoice;
- partial payment;
- authorized override;
- unauthorized override;
- changed order amount.

### Gate

`CREDIT_CONTROL_PASS`

---

## Module 17 — Phoenix Purchase Approval

Target:

`phoenix_purchase_approval`

### Learn/build

- configurable thresholds;
- approval levels;
- purchase-order inheritance;
- state transitions;
- groups;
- authorization;
- audit metadata.

### Required scenarios

- low-value automatic path;
- supervisor path;
- management path;
- unauthorized user;
- changed order after approval;
- cancellation/rejection.

### Gate

`PURCHASE_APPROVAL_PASS`

---

## Module 18 — Phoenix Supplier Score

Target:

`phoenix_supplier_score`

### Principle

Start deterministic and explainable.

### Candidate factors

- delivery punctuality;
- quantity fulfillment;
- price performance;
- return/rejection signal;
- purchase history.

### Learning objectives

- aggregate existing Odoo data;
- avoid duplicate truth;
- computed vs stored metrics;
- scheduled recalculation where justified;
- reporting.

### Gate

`SUPPLIER_SCORE_PASS`

---

# 11. PHASE F — Reporting and frontend depth

---

## Module 19 — Reporting and financial analysis

### Explore first

- pivot views;
- graph views;
- standard reports;
- OCA financial reports if approved.

### Learn

- QWeb report fundamentals;
- report actions;
- analysis views;
- SQL-view reporting only when justified.

### Phoenix output

Produce usable views/reports for:

- sales;
- purchases;
- AR;
- AP;
- stock;
- supplier score.

### Gate

`REPORTING_PASS`

---

## Module 20 — Management dashboard / OWL

Target:

`phoenix_management_dashboard`

### Official study

Odoo 19:

**Discover the web framework**

Topics:

- OWL components;
- services;
- dashboard architecture.

### Rule

Do not build a custom dashboard until you can state why standard pivot/graph/dashboard capabilities are insufficient.

### Dashboard candidates

- monthly sales;
- gross margin;
- AR;
- overdue AR;
- AP;
- upcoming payments;
- stock valuation;
- low stock;
- supplier performance.

### Gate

`MANAGEMENT_DASHBOARD_PASS`

---

# 12. PHASE G — Integrations and APIs

---

## Module 21 — Consume an external API

Target addon:

`phoenix_integration`

### Learn

- HTTP client behavior;
- timeouts;
- authentication;
- validation;
- retries;
- logging;
- scheduled actions;
- idempotency concepts.

### Phoenix exercise

Consume a selected business API, such as a currency-rate provider.

### Failure scenarios

- timeout;
- HTTP error;
- malformed payload;
- missing field;
- duplicate execution;
- stale data.

### Gate

`OUTBOUND_INTEGRATION_PASS`

---

## Module 22 — Expose a controlled Phoenix API

### Candidate read operations

- products;
- stock;
- order status.

### Candidate write operation

One deliberately limited operation to practice validation/idempotency.

### Learn

- Odoo controllers;
- routes;
- authentication strategy;
- authorization;
- JSON payloads;
- errors;
- correlation IDs;
- security.

### Required documentation

Document:

- endpoint;
- method;
- authentication;
- request;
- response;
- errors;
- idempotency behavior.

### Gate

`API_PASS`

---

# 13. PHASE H — Hardening

---

## Module 23 — Security review

Perform a dedicated review of:

- ACL;
- record rules;
- manager-only actions;
- credit overrides;
- purchase approvals;
- API auth;
- secrets;
- logging;
- attachments/data exposure;
- `sudo()`;
- CSRF/HTTP behavior;
- database access.

### Exercise

Try to break your own permission model using low-privilege test users.

### Gate

`SECURITY_PASS`

---

## Module 24 — End-to-end automated testing

Create tests for all mandatory project scenarios:

- cash sale;
- credit sale;
- exceeded credit;
- purchase;
- approval;
- replenishment;
- supplier scoring;
- AR;
- AP;
- partial payments;
- integration errors.

### Gate

`QA_PASS`

---

# 14. PHASE I — DevOps and deployment

---

## Module 25 — Production Docker architecture

### Video

Revisit:

https://www.youtube.com/watch?v=MPxp5iHFSAg

This time watch it as an operator, not a beginner.

### Target

```text
docker compose
├── odoo:19
├── postgres
└── nginx
```

### Learn

- immutable image vs persistent data;
- custom addons;
- volumes;
- secrets;
- networks;
- health/restart behavior;
- production configuration;
- backup implications.

### Important

The official Odoo image supports `arm64/v8`, so it is suitable for the Oracle Ampere target.

### Gate

`PRODUCTION_COMPOSE_READY`

---

## Module 26 — Oracle Cloud fundamentals

### Objective

Understand OCI before deploying Odoo.

### Official source

Oracle Always Free documentation.

Learn:

- tenancy;
- home region;
- compartment;
- VCN;
- subnet;
- security list / network security group;
- public IP;
- compute instance;
- boot/block volume;
- SSH key.

### Planned resource

```text
VM.Standard.A1.Flex
ARM64
up to Always Free resource limits
Ubuntu 24.04 LTS
```

Oracle currently documents Always Free A1 resources equivalent to up to 2 OCPUs and 12 GB memory for Always Free tenancies.

### Gate

`OCI_CONCEPTS_READY`

---

## Module 27 — Deploy Phoenix to Oracle Cloud

### Architecture

```text
Internet
  ↓
DNS
  ↓
OCI Public IP
  ↓
Nginx :443
  ↓
Odoo container
  ↓
PostgreSQL container
```

### Steps Luis performs

1. provision A1 VM;
2. configure SSH keys;
3. update Ubuntu;
4. install Docker/Compose;
5. configure firewall;
6. clone Phoenix;
7. create production secret values;
8. launch database;
9. launch Odoo;
10. launch Nginx;
11. configure DNS;
12. add TLS certificate;
13. validate proxy configuration;
14. validate restart behavior;
15. run smoke tests.

### Network rule

Public:

- SSH, restricted where possible;
- HTTP;
- HTTPS.

Not public:

- PostgreSQL;
- Odoo internal container port when reverse proxy is authoritative.

### Gate

`ORACLE_DEPLOY_PASS`

---

## Module 28 — Backups and restore

A backup that has never been restored is only a theory.

### Back up

- PostgreSQL;
- Odoo filestore;
- required configuration/version metadata.

### Target

Automated scheduled backup.

Optional future storage target:

OCI Object Storage where appropriate within account limits.

### Mandatory exercise

Restore Phoenix into a clean environment.

### Gate

`RESTORE_VERIFIED`

---

## Module 29 — Operations

### Learn

- logs;
- disk space;
- PostgreSQL health;
- Odoo process/container health;
- restart;
- update procedure;
- dependency pinning;
- rollback plan;
- database-neutralized/staging thinking.

### Deliverable

`RUNBOOK.md`

It must answer:

- how to deploy;
- how to restart;
- how to inspect logs;
- how to back up;
- how to restore;
- how to update;
- what to do after a failed deployment.

### Gate

`OPERATIONS_READY`

---

# 15. PHASE J — Professional completion

---

## Module 30 — Functional UAT

Use role-specific users.

Execute all E2E cases from the master SPEC.

For each:

```text
Requirement
→ User flow
→ Result
→ Accounting effect
→ Evidence
```

### Gate

`UAT_PASS`

---

## Module 31 — Documentation

Prepare:

- README;
- architecture;
- setup guide;
- addon catalog;
- security model;
- API documentation;
- deployment guide;
- backup/restore guide;
- UAT evidence;
- demo credentials policy;
- screenshots.

### Gate

`DOCUMENTED`

---

## Module 32 — Portfolio demo

Create a clean demo dataset.

Prepare a 10–15 minute demonstration:

1. CRM lead;
2. quotation;
3. credit control;
4. sale;
5. delivery;
6. customer invoice/AR;
7. payment;
8. purchase approval;
9. purchase/receipt;
10. AP/payment;
11. supplier score;
12. dashboard;
13. API;
14. accounting report.

### Job-interview objective

Be able to answer:

- What did standard Odoo solve?
- What did you customize?
- Why did you use inheritance?
- How did you secure it?
- How did you test it?
- How do AR/AP flow into accounting?
- How did you deploy it?
- How do you restore it?
- What would you change for Enterprise?
- How would you upgrade to Odoo 20?

### Gate

`PORTFOLIO_READY`

---

## Module 33 — Final Blueprint audit

Auditor compares:

```text
SPEC
vs
PLAN
vs
CONFIGURATION
vs
CODE
vs
TESTS
vs
DEPLOYMENT
vs
DOCUMENTATION
```

No feature is considered complete because a screen exists.

### Final verdict

Target:

```text
PHOENIX PROFESSIONAL LAB COMPLETE
```

---

# 16. Graduation criteria

Luis graduates from the Phoenix path when he can independently:

## Functional

- configure CRM/Sales/Purchase/Inventory;
- explain AR/AP;
- reconcile payments;
- read basic financial reports;
- understand integrated ERP flows.

## Development

- create addons;
- extend Odoo models;
- use ORM correctly;
- inherit views;
- build security rules;
- write business constraints;
- build reports;
- use OWL when needed;
- write controllers/integrations;
- write automated tests.

## Architecture

- decide standard vs custom;
- avoid core modifications;
- choose extension points;
- preserve authoritative data;
- manage dependencies.

## Operations

- run Odoo/PostgreSQL;
- deploy Docker;
- configure HTTPS;
- deploy to Oracle Cloud;
- back up and restore;
- diagnose logs.

## Professional consulting

- gather requirements;
- map processes;
- design standard-first solutions;
- document gaps;
- communicate trade-offs;
- demonstrate the result.

---

# 17. Course completion != permanent expertise

Phoenix is designed to move Luis from Odoo beginner to a strong professional implementation/development level with a substantial portfolio project.

Real expert-level judgment continues to grow through:

- production incidents;
- upgrades;
- migrations;
- multiple clients;
- localization work;
- high-volume datasets;
- performance tuning;
- complex multi-company implementations.

Phoenix provides the foundation and evidence required to enter that path with something real in hand.

---

# 18. First lesson

The course starts at:

```text
Module 0 — Understand Phoenix before touching Odoo
```

Do not jump directly to Docker.

The first deliverable is understanding the business system that will later be configured and extended.
