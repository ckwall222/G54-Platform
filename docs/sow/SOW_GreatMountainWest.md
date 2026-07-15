# Statement of Work
## Enterprise Resource Platform — SAP Replacement
### Prepared For: Great Mountain West (g54.com)
### Prepared By: Christopher Wall
### Document Version: 1.0 — Draft
### Date: July 10, 2026
### Document Status: Pending Client Review & Execution

---

## 1. Parties

| | |
|---|---|
| **Client** | Great Mountain West |
| **Client Website** | g54.com |
| **Client Contact** | [Client Name], [Title] |
| **Client Address** | [Address] |
| **Service Provider** | Christopher Wall |
| **Provider Contact** | Christopher Wall |
| **Provider Address** | [Address] |

---

## 2. Project Background & Overview

Great Mountain West currently operates on **SAP** as its primary enterprise resource planning platform. Sage 100 serves as an additional feature benchmark for financial functionality. Following an evaluation of Odoo as a potential replacement — which did not satisfy the depth of financial functionality required — Great Mountain West is commissioning a purpose-built, cloud-native enterprise platform that achieves full feature parity with SAP while delivering a modern, accessible user experience.

This platform will consolidate and replace the following operational domains:

- Financial accounting (GL, AR, AP, Banking) — SAP FI module parity
- Controlling — cost center accounting, profit center accounting, profitability analysis (SAP CO/CO-PA parity)
- Asset accounting — fixed asset register, depreciation schedules (SAP AA parity)
- Customer Relationship Management (CRM) — SAP SD parity
- Sales & Distribution — order management, advanced pricing, credit management
- eCommerce — customer-facing order entry and management
- Inventory and warehouse management — SAP MM/WM parity
- Material Requirements Planning (MRP) — automated procurement triggers
- Point of Sale (POS)
- Project and job management — SAP PS parity
- Quality management and inspection workflows — SAP QM parity
- Equipment and plant maintenance — SAP PM parity
- Accounts Receivable and Accounts Payable workflows
- Multi-entity and intercompany accounting
- EDI and electronic invoicing
- Configurable workflow and approval engine

The resulting system will be a **single, integrated, cloud-hosted platform** accessible via internet browser, designed to meet **PCI DSS** and **SOC 2 Type 2** compliance requirements from the ground up.

---

## 3. Project Objectives

1. Deliver a full-replacement ERP platform purpose-built for Great Mountain West's operational model with full SAP feature parity.
2. Eliminate dependency on SAP and any associated legacy integrations. Sage 100 functionality is treated as the minimum baseline; SAP functionality defines the full target feature set.
3. Provide a secure, compliance-ready platform with end-to-end data security.
4. Enable role-based access across all departments — Executive, Finance, Sales, Creative/Art, Production, Print, AR, AP, and more.
5. Build iteratively using Agile sprint methodology, delivering working software at each phase boundary.
6. Architect for scalability, backup integrity, and disaster recovery from day one.

---

## 4. Project Phases Overview

The project is structured into the following high-level phases:

| Phase | Name | Methodology | Pricing Model |
|---|---|---|---|
| **Phase 1** | Discovery, Architecture & Design | Flat-rate delivery | $5,000 |
| **Phase 2** | Core Platform Foundation | Sprint-based | TBD post-Phase 1 |
| **Phase 3** | Financial Suite (Accounting, AR, AP) | Sprint-based | TBD post-Phase 1 |
| **Phase 4** | CRM & Sales | Sprint-based | TBD post-Phase 1 |
| **Phase 5** | Inventory, POS & eCommerce | Sprint-based | TBD post-Phase 1 |
| **Phase 6** | Project & Job Management | Sprint-based | TBD post-Phase 1 |
| **Phase 7** | Reporting, Analytics & Dashboards | Sprint-based | TBD post-Phase 1 |
| **Phase 8** | Compliance, Security Audit & Launch | Sprint-based | TBD post-Phase 1 |

> **Note:** Phases 2–8 will be scoped, estimated, and priced as fixed deliverables following the completion and approval of Phase 1. Sprint pricing, cadence, and delivery timelines will be formalized in a Phase 2+ amendment to this SOW.

---

## 5. Phase 1 — Discovery, Architecture & Design

### 5.1 Scope

Phase 1 is a flat-rate discovery and design engagement. Its purpose is to produce the complete blueprint — functional, technical, and visual — that will govern all subsequent development phases.

This phase includes:

#### 5.1.1 Discovery & Requirements Workshops
- Structured interviews and working sessions with stakeholders across all departments
- Documentation of current Sage 100 workflows and data models
- Gap analysis between current state and desired future state
- Identification of third-party integrations (e.g., payment processors, shipping carriers, email, file storage)
- Compliance scoping session (PCI DSS, SOC 2 Type 2)

#### 5.1.2 Persona Development
Definition and documentation of all user personas, including:
- Business personas (Executive, Finance, Sales, Art/Design, Production, Print, AR, AP, Customer Service, Warehouse, IT Admin, Project Manager)
- System and platform personas (Super Admin, API Consumer, Payment Gateway, Audit Engine, Email Service, Reporting Engine, Backup Service)

#### 5.1.3 Full Epic & User Story Documentation
- Complete product backlog organized by module and persona
- Acceptance criteria for each user story
- Priority and dependency mapping
- Estimated story point ranges (for sprint planning reference)

#### 5.1.4 Feature Requirements Specification
- Functional requirements document (FRD) covering all modules
- Non-functional requirements (performance, security, availability, compliance)
- Data model and entity relationship diagrams
- Role-based access control (RBAC) matrix

#### 5.1.5 UX/UI Design & Wireframes
- Information architecture and site map
- Low-fidelity wireframes for all primary user flows
- High-fidelity mockups for key screens (Dashboard, Accounting, CRM, POS, Inventory, eCommerce storefront)
- Interactive prototype for client review and approval
- Design system foundations (typography, color, component library direction)

#### 5.1.6 Technical Architecture Design
- Platform and infrastructure selection (hosting, database, framework)
- Security architecture (authentication, authorization, encryption at rest and in transit)
- Backup and disaster recovery architecture
- CI/CD pipeline architecture
- PCI DSS and SOC 2 Type 2 control mapping
- Third-party service selection and integration design
- API architecture design

### 5.2 Deliverables

Upon completion of Phase 1, the following deliverables will be provided to Great Mountain West:

| # | Deliverable | Format |
|---|---|---|
| 1 | Discovery Workshop Summary & Current State Analysis | PDF / Notion |
| 2 | Persona Documentation (all business and system personas) | PDF / Notion |
| 3 | Complete Product Backlog (Epics, Stories, Acceptance Criteria) | PDF / Notion / Jira export |
| 4 | Functional Requirements Document (FRD) | PDF |
| 5 | Non-Functional Requirements & Compliance Mapping | PDF |
| 6 | Data Model & Entity Relationship Diagrams | PDF / Lucidchart |
| 7 | RBAC Matrix | PDF / Spreadsheet |
| 8 | UX Wireframes (all primary flows) | Figma |
| 9 | High-Fidelity UI Mockups (key screens) | Figma |
| 10 | Interactive Prototype | Figma (shareable link) |
| 11 | Technical Architecture Document | PDF |
| 12 | Phase 2–8 Refined Scope, Sprint Plan & Cost Estimate | PDF |

### 5.3 Investment

| | |
|---|---|
| **Phase 1 Total** | **$5,000.00 USD** |
| **Pricing Model** | Flat-rate delivery (not time-bound) |
| **Payment Terms** | 100% due at project start, prior to commencement |
| **Accepted Payment Methods** | ACH, Wire Transfer, Check, Zelle |

> Phase 1 commences upon receipt of signed SOW and payment in full.

### 5.4 Revisions

Phase 1 includes up to **two (2) rounds of revisions** on wireframes and mockups following initial delivery. Additional revision rounds may be requested at a rate of $175.00 per hour.

### 5.5 Client Responsibilities in Phase 1

To ensure timely delivery, Great Mountain West agrees to:

- Provide access to at least one designated stakeholder per department for discovery sessions
- Provide read-only access to Sage 100 data and report samples as needed
- Respond to document review requests within **5 business days**
- Consolidate internal feedback before submitting to the project team
- Provide existing brand assets (logo, style guide, brand colors) if a branded UI is desired

---

## 6. Phase 2–8 — Development (Overview)

Development phases will be executed using **Agile sprint methodology**, with each sprint delivering working, testable software. Sprint details will be formalized in a Phase 2+ SOW amendment following client approval of Phase 1 deliverables.

### 6.1 Sprint Model

- Sprint duration: 2 weeks
- Each sprint includes: planning, development, testing, client demo, retrospective
- All sprints will include automated test coverage
- A staging environment will be maintained throughout development
- Production deployments will follow sprint acceptance by the client

### 6.2 Module Development Roadmap (Preliminary)

#### Sprint Group A — Core Platform Foundation (Phase 2)
- Infrastructure provisioning (hosting, database, CI/CD, environments)
- Authentication system (SSO, MFA, session management)
- User and role management
- Configurable workflow and approval engine
- Audit logging and activity trails
- Email notification system
- Backup and recovery system
- Admin console

#### Sprint Group B — Financial Accounting Suite (Phase 3)
- General Ledger (chart of accounts, journal entries, period management) — SAP FI parity
- Bank reconciliation and cash management
- Accounts Receivable with credit management and exposure limits
- Accounts Payable with three-way match and payment runs
- Asset accounting — fixed asset register, depreciation schedules, asset lifecycle — SAP AA parity
- Tax management (sales tax, use tax, tax reporting)
- Multi-currency support and foreign currency revaluation
- Multi-entity and intercompany accounting with eliminations
- Financial reporting (P&L, Balance Sheet, Cash Flow, consolidations)
- EDI and electronic invoicing

#### Sprint Group C — Controlling & Profitability (Phase 3 continued)
- Cost center accounting — departmental cost tracking and allocation — SAP CO parity
- Profit center accounting — entity-level P&L — SAP CO parity
- Internal orders and budgeting
- Profitability analysis by customer, product, and channel — SAP CO-PA parity
- Product costing and standard cost management

#### Sprint Group D — CRM & Sales (Phase 4)
- Contact and account management
- Lead and opportunity pipeline
- Advanced pricing and contract management (pricing conditions, volume discounts, contract pricing)
- Quote/estimate generation
- Order entry and management
- Credit management with customer exposure limits
- Customer portal
- Sales reporting and forecasting
- Document flow — end-to-end traceability from quote through payment

#### Sprint Group E — Inventory, Warehouse & MRP (Phase 5)
- Product catalog management
- Inventory tracking and valuation (FIFO, LIFO, average cost)
- Batch/lot tracking and serial number management
- Advanced warehouse management (bin management, putaway strategies, picking optimization)
- Purchase orders and receiving
- Material Requirements Planning (MRP) — automated procurement triggers based on job schedule and stock levels
- Point of Sale terminal
- eCommerce storefront (customer-facing)
- Shopping cart and checkout
- Payment processing (PCI-compliant)
- Shipping and fulfillment

#### Sprint Group F — Project, Job & Quality Management (Phase 6)
- Job/project creation and tracking with WBS (Work Breakdown Structure) — SAP PS parity
- Task and milestone management
- Resource and time tracking
- Job costing and profitability (actual vs. estimate)
- Proofing and approval workflow (Art/Design use case)
- Production scheduling
- Quality management — inspection plans, quality notifications, defect tracking — SAP QM parity
- Equipment and plant maintenance — press maintenance scheduling, downtime tracking, work orders — SAP PM parity

#### Sprint Group G — Reporting & Analytics (Phase 7)
- Executive dashboard
- Department-level dashboards (Finance, Sales, Production, Operations)
- Custom report builder
- Scheduled report delivery
- Export (PDF, Excel, CSV)
- KPI and metric tracking
- Profitability analysis reporting

#### Sprint Group H — Compliance, Security & Launch (Phase 8)
- PCI DSS audit and remediation
- SOC 2 Type 2 control implementation and evidence collection
- Penetration testing
- Performance testing and optimization
- Disaster recovery drill
- SAP data migration assessment and execution
- Production launch
- User training and documentation
- Hypercare support period (30 days post-launch)

---

## 7. Platform Requirements Summary

The platform must meet the following baseline requirements, to be fully detailed in Phase 1:

| Requirement | Detail |
|---|---|
| **Hosting** | Cloud-hosted, internet-accessible via browser |
| **Uptime Target** | 99.9% or greater |
| **Security Certifications** | PCI DSS Level 1 compliance, SOC 2 Type 2 certification path |
| **Authentication** | Multi-factor authentication (MFA), SSO support |
| **Data Backup** | Automated daily backups, point-in-time recovery, off-site redundancy |
| **Disaster Recovery** | Documented RTO and RPO targets |
| **Access Control** | Role-based access control (RBAC) with least-privilege model |
| **Audit Logging** | Full user activity audit trail |
| **Data Encryption** | Encryption in transit (TLS 1.2+) and at rest (AES-256) |
| **Notifications** | Email notification system (transactional and alert-based) |
| **Browser Support** | All modern browsers (Chrome, Firefox, Safari, Edge) |
| **Mobile** | Responsive web design (mobile-optimized); native app TBD in Phase 1 |

---

## 8. Assumptions

1. Great Mountain West will provide a dedicated internal point of contact for the duration of the project.
2. All stakeholder availability required for Phase 1 workshops will be provided within 4 weeks of project start.
3. Existing Sage 100 data export and migration is not included in this SOW unless explicitly added as a line item following Phase 1 assessment.
4. Third-party software licenses (payment gateway, email provider, hosting) are not included in this SOW and will be procured separately.
5. Domain name, SSL certificates, and DNS management for the new platform are the responsibility of the client unless otherwise agreed.
6. The client will designate a single feedback consolidator per department to prevent conflicting direction.
7. Phase 2–8 pricing is not guaranteed and will be subject to change based on Phase 1 findings.

---

## 9. Exclusions

The following are explicitly **not included** in this SOW unless added by written amendment:

- Data migration from Sage 100 to the new platform
- Legacy system decommissioning
- Hardware procurement
- Network or physical infrastructure
- Custom integrations not identified during Phase 1
- Mobile native applications (iOS/Android)
- Ongoing managed hosting or support (separate maintenance agreement)
- End-user training beyond the hypercare period

---

## 10. Intellectual Property

Upon full payment for each phase, Great Mountain West shall own all custom code, designs, and documentation produced specifically for this project. Service Provider retains rights to any pre-existing frameworks, libraries, tools, or methodologies used in delivery.

---

## 11. Confidentiality

Both parties agree to treat all proprietary business information, technical specifications, and data shared during this engagement as confidential. A mutual Non-Disclosure Agreement (NDA) should be executed prior to discovery workshops.

---

## 12. Payment Terms & Late Fees

- Phase 1: Payment due in full prior to project commencement.
- Invoices for subsequent phases are due within **15 days** of invoice date.
- Late payments are subject to a **1.5% monthly finance charge**.
- Work may be paused on accounts with invoices past 30 days outstanding.

---

## 13. Change Management

Changes to scope must be submitted in writing and approved by both parties via a **Change Order** before work begins. Change orders that increase scope will include a revised cost and timeline estimate.

---

## 14. Termination

Either party may terminate this agreement with **30 days written notice**. Upon termination, Great Mountain West shall pay for all work completed to date. Phase 1 payment is non-refundable once work has commenced.

---

## 15. Limitation of Liability

Service Provider's total liability shall not exceed the total fees paid under this SOW. Neither party shall be liable for indirect, incidental, or consequential damages.

---

## 16. Governing Law

This agreement shall be governed by the laws of the State of Utah.

---

## 17. Signatures

By signing below, both parties agree to the terms of this Statement of Work.

**Great Mountain West**

Signature: ___________________________

Printed Name: ___________________________

Title: ___________________________

Date: ___________________________

---

**Christopher Wall**

Signature: ___________________________

Printed Name: Christopher Wall

Title: Principal Developer

Date: ___________________________

---

*This document is confidential and intended solely for the use of Great Mountain West and Christopher Wall. Unauthorized distribution is prohibited.*
