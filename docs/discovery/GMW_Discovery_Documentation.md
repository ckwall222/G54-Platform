# Great Mountain West — Enterprise Platform
## Phase 1 Discovery Documentation
### Personas, Epics, User Stories & Feature Requirements
### Version: 1.0 — Initial Draft
### Date: July 10, 2026

---

## Table of Contents

1. [Platform Working Title & Vision](#platform-vision)
2. [Personas — Business Users](#business-personas)
3. [Personas — System & Platform](#system-personas)
4. [Module Overview & Feature Inventory](#module-overview)
5. [Epics](#epics)
6. [User Stories by Module](#user-stories)
7. [Non-Functional Requirements](#non-functional-requirements)
8. [Compliance Requirements](#compliance-requirements)
9. [Integration Requirements](#integrations)
10. [RBAC Matrix (Draft)](#rbac-matrix)

---

## 1. Platform Working Title & Vision {#platform-vision}

**Working Title:** Apex (to be confirmed with client)

**Vision Statement:**
A single, cloud-hosted enterprise platform that unifies every operational touchpoint of Great Mountain West — from customer relationship and sales, through production and fulfillment, to financial close — replacing Sage 100 and eliminating the need for disconnected point solutions.

**Design Principles:**
- **Unified** — one login, one data model, no re-entry
- **Role-appropriate** — each user sees exactly what they need
- **Compliant by default** — PCI DSS and SOC 2 Type 2 from the ground up
- **Resilient** — automated backups, tested recovery, high availability
- **Auditable** — every action logged, every change traceable

---

## 2. Personas — Business Users {#business-personas}

---

### Persona: Executive
**Role Examples:** CEO, President, Owner, COO

**Goals:**
- Real-time visibility into overall business health (revenue, margin, cash position)
- Confidence that operations, compliance, and data security are under control
- Ability to make strategic decisions from accurate, current data without relying on staff to pull reports

**Pain Points (Current State):**
- Must request reports from Finance; no self-serve dashboard
- No single view across sales, production, and finance
- Uncertainty about data accuracy when reports are produced manually

**System Usage Pattern:**
- Daily: Dashboard review, KPI monitoring
- Weekly: Revenue, pipeline, and cash flow review
- Monthly: P&L, balance sheet, department performance

**Key Permissions Needed:**
- Read access to all modules
- Approve high-value transactions above defined thresholds
- Access to full audit log

**Success Criteria:**
- Can answer "How is the business performing this month?" in under 60 seconds without contacting anyone

---

### Persona: Finance Manager / Controller
**Role Examples:** Controller, CFO, Finance Director

**Goals:**
- Own and maintain the general ledger, chart of accounts, and financial reporting
- Ensure accurate period close, reconciliation, and tax compliance
- Manage and oversee AR and AP teams

**Pain Points (Current State):**
- Manual journal entry reconciliation in Sage 100 is time-consuming
- Difficulty generating ad-hoc financial reports without IT involvement
- AR/AP visibility requires navigating multiple views

**System Usage Pattern:**
- Daily: GL review, approvals, exception handling
- Weekly: Cash position, aging reports, variance analysis
- Monthly: Period close, financial statement generation, tax prep data

**Key Permissions Needed:**
- Full access to Accounting module (GL, AR, AP, Bank Rec)
- Approve journal entries above threshold
- Generate and export all financial reports
- User management for Finance team

**Success Criteria:**
- Monthly close completed 2 days faster than current baseline
- Self-serve financial report generation without IT

---

### Persona: Sales Representative
**Role Examples:** Account Executive, Inside Sales, Outside Sales

**Goals:**
- Manage a pipeline of prospects and customers
- Create and send quotes quickly
- Know the status of current orders and jobs

**Pain Points (Current State):**
- Quote creation is disjointed from inventory/pricing data
- No visibility into production status of active jobs
- Customer history scattered across multiple places

**System Usage Pattern:**
- Daily: CRM pipeline management, quote creation, order entry
- Ongoing: Customer communication, follow-up tracking

**Key Permissions Needed:**
- CRM (full CRUD on own accounts; read-only on others)
- Create quotes/estimates
- Enter orders (subject to credit limit checks)
- View (not edit) inventory and pricing
- View job status in Production

**Success Criteria:**
- Quote generated and sent in under 5 minutes
- No more calling production to get job status

---

### Persona: Sales Manager
**Role Examples:** VP of Sales, Sales Director, Sales Team Lead

**Goals:**
- Visibility into team pipeline and forecast accuracy
- Manage pricing approvals and discount authority
- Review sales performance by rep, by customer, by product

**Pain Points (Current State):**
- Pipeline visibility requires chasing reps for status updates
- No reliable sales forecast view

**System Usage Pattern:**
- Daily: Pipeline review, deal approval
- Weekly: Team performance reports
- Monthly: Forecasting, commission review

**Key Permissions Needed:**
- All Sales Rep permissions
- View all CRM records (not just own)
- Approve discounts above rep threshold
- Run team-level reports
- Manage sales team user accounts

**Success Criteria:**
- One-click access to team pipeline and forecast
- Approval workflows reduce quote-to-send cycle by 30%

---

### Persona: Art Director / Graphic Designer
**Role Examples:** Art Director, Senior Designer, Graphic Designer, Prepress Artist

**Goals:**
- Receive job specifications and assets from sales/project team
- Upload completed artwork and proofs for customer approval
- Track which jobs need art, which are in review, and which are approved

**Pain Points (Current State):**
- Job specs arrive by email; no structured handoff from sales
- Proof approval tracked via email thread — easy to lose
- No visibility into when production needs art by

**System Usage Pattern:**
- Daily: Job queue management, asset upload, proof management
- As needed: Revision tracking, approval confirmation

**Key Permissions Needed:**
- View job specifications for assigned jobs
- Upload and manage art assets
- Initiate customer proof workflow
- Receive proof approval/rejection notifications
- View production schedule for art deadlines

**Success Criteria:**
- Zero missed art deadlines due to miscommunication
- Proof approval cycle tracked in-system (not via email)

---

### Persona: Prepress Technician
**Role Examples:** Prepress Operator, File Prep Specialist

**Goals:**
- Receive approved artwork and prepare files for production
- Flag file issues (resolution, color profile, bleed, etc.) before going to press
- Hand off press-ready files to production on schedule

**Pain Points (Current State):**
- File handoffs via shared drives with no versioning
- Rework due to late-stage file issues not caught earlier

**System Usage Pattern:**
- Daily: File intake, preflight, and handoff
- As needed: Communication with art team on corrections

**Key Permissions Needed:**
- View and download art assets for assigned jobs
- Upload press-ready files
- Flag file issues with notes
- View production schedule

**Success Criteria:**
- File issues caught and resolved before production slot
- Clear file versioning and handoff record

---

### Persona: Print Production Manager
**Role Examples:** Production Manager, Shop Supervisor, Operations Manager

**Goals:**
- Schedule and dispatch jobs to presses and finishing equipment
- Monitor production throughput and capacity
- Identify bottlenecks before they cause missed ship dates

**Pain Points (Current State):**
- Production schedule managed in spreadsheets
- No real-time visibility into job progress on the floor
- Rescheduling is a manual, error-prone process

**System Usage Pattern:**
- Daily: Production scheduling, job dispatch, progress monitoring
- Continuous: Exception handling (machine downtime, rush jobs, re-runs)

**Key Permissions Needed:**
- Full access to production scheduling and job management
- Update job status (queued, in-press, finishing, complete)
- View inventory of materials and supplies
- Manage production team time tracking
- View/edit all active jobs

**Success Criteria:**
- Production schedule accessible in real time by all stakeholders
- Rush job insertion handled in under 2 minutes without spreadsheet

---

### Persona: Production Operator
**Role Examples:** Press Operator, Bindery Operator, Finishing Operator

**Goals:**
- Know what jobs are queued for their station
- Log job start, progress, and completion
- Report material usage and waste

**Pain Points (Current State):**
- Rely on paper traveler or verbal direction for job queue
- No easy way to log completion or flag issues from the floor

**System Usage Pattern:**
- During shift: Job queue view, status updates, material logging

**Key Permissions Needed:**
- View assigned job queue
- Update job status for own station
- Log material usage
- Flag job issues/exceptions
- View job specifications

**Success Criteria:**
- Job queue visible on shop floor terminal
- Status updates completed without leaving workstation

---

### Persona: Accounts Receivable Clerk
**Role Examples:** AR Specialist, Billing Clerk, Collections Coordinator

**Goals:**
- Generate and send invoices on time
- Apply and record incoming payments accurately
- Manage collections on overdue accounts

**Pain Points (Current State):**
- Invoice generation tied to manual steps in Sage 100
- Payment application requires navigating multiple screens
- Aging reports require manual export and formatting

**System Usage Pattern:**
- Daily: Invoice generation, payment entry, aging review
- Weekly: Collections follow-up, customer statements
- Monthly: AR close, aging analysis

**Key Permissions Needed:**
- Create, send, and manage invoices
- Apply payments to open invoices
- Generate customer statements
- View AR aging reports
- Issue credits (with approval workflow above threshold)
- View customer account history

**Success Criteria:**
- Invoice-to-send in under 2 minutes per invoice
- One-click customer statement generation
- Automated payment reminders reduce DSO by 5+ days

---

### Persona: Accounts Payable Clerk
**Role Examples:** AP Specialist, Vendor Payables Coordinator

**Goals:**
- Record vendor invoices accurately and on time
- Process approved payments by check, ACH, or credit card
- Manage vendor master data and terms

**Pain Points (Current State):**
- Invoice entry and approval routing is manual
- Check runs require multiple steps without a clear approval trail
- No automated early-pay discount capture

**System Usage Pattern:**
- Daily: Invoice entry, approval routing, payment processing
- Weekly: Check runs, AP aging review
- Monthly: AP close, vendor reconciliation

**Key Permissions Needed:**
- Enter and manage vendor invoices
- Route invoices for approval
- Process payment runs (ACH, check)
- View AP aging reports
- Manage vendor master records
- Three-way PO match (invoice against PO and receipt)

**Success Criteria:**
- Full approval trail on every invoice before payment
- Automated early-payment discount alerts

---

### Persona: Customer Service Representative
**Role Examples:** CSR, Account Support Specialist, Order Desk

**Goals:**
- Answer customer inquiries about order status, invoices, and account information
- Enter and edit orders on behalf of customers
- Resolve billing disputes or shipping issues quickly

**Pain Points (Current State):**
- Must navigate multiple systems to answer a single customer question
- No single customer history view

**System Usage Pattern:**
- Daily: Order status lookups, customer inquiries, order entry

**Key Permissions Needed:**
- View all customer account information
- Enter and edit orders (within role limits)
- View invoice and payment history
- Initiate returns or credits (with approval)
- View production/job status for customer jobs

**Success Criteria:**
- Customer inquiry resolved in one screen without transferring the call

---

### Persona: Warehouse / Inventory Manager
**Role Examples:** Warehouse Manager, Inventory Control, Receiving Supervisor

**Goals:**
- Maintain accurate inventory counts across all locations
- Manage receiving against purchase orders
- Fulfill outgoing orders efficiently

**Pain Points (Current State):**
- Cycle counts and physical inventory are disjointed from system records
- Receiving process is partially manual

**System Usage Pattern:**
- Daily: Receiving, pick/pack/ship, cycle counts
- Weekly: Reorder point review, discrepancy resolution

**Key Permissions Needed:**
- Full access to Inventory module
- Manage purchase orders and receiving
- Process outgoing shipments
- Initiate inventory adjustments (with audit log)
- View and manage all products and stock levels

**Success Criteria:**
- Inventory accuracy at 98%+ with system-enforced cycle count workflow
- Receiving completed without paper

---

### Persona: Project Manager
**Role Examples:** Client Services Manager, Account Manager (project-focused), Job Coordinator

**Goals:**
- Track jobs from order through delivery
- Coordinate between sales, art, production, and shipping
- Communicate project milestones to clients and internal team

**Pain Points (Current State):**
- No single view of a job's status across departments
- Milestone tracking done in emails or separate PM tools

**System Usage Pattern:**
- Daily: Job tracking, milestone updates, client communication
- Ongoing: Schedule management, resource coordination

**Key Permissions Needed:**
- View all job/project records
- Update milestones and task status
- Generate client-facing job status reports
- Communicate via in-system messaging or email
- View but not edit financial details of jobs (job costing)

**Success Criteria:**
- One-page project status view covers all departments
- Client proofing and approval tracked end-to-end

---

### Persona: IT Administrator
**Role Examples:** Internal IT, System Administrator, Network Admin

**Goals:**
- Manage system users, permissions, and access controls
- Monitor system health, backup integrity, and security events
- Coordinate with the platform provider on incidents and upgrades

**Pain Points (Current State):**
- User provisioning and deprovisioning is ad hoc
- No centralized audit log

**System Usage Pattern:**
- Daily: User provisioning, alert review
- Weekly: Backup verification, security scan review
- Monthly: Access review, compliance reporting

**Key Permissions Needed:**
- Full user management (create, modify, deactivate)
- View full system audit log
- Manage RBAC roles and permissions
- Monitor system health and uptime metrics
- Trigger and verify backups
- Manage SSO and MFA configuration
- View security alerts and event logs

**Success Criteria:**
- User provisioning/deprovisioning completed in under 5 minutes
- Audit log queryable and exportable for compliance review

---

## 3. Personas — System & Platform {#system-personas}

These are non-human actors that interact with the system. They must be modeled as first-class entities in the security and access architecture.

---

### System Persona: Super Administrator
**Actor Type:** Privileged human (internal team / service provider)

**Description:**
The highest-privilege account in the system. Used only for initial system configuration, emergency access, and platform-level operations. Must never be used for day-to-day tasks.

**Key Capabilities:**
- All platform configuration (environment, DNS, certificates)
- Tenant provisioning and management
- Override of all RBAC rules (with mandatory audit log entry)
- Emergency account recovery
- Platform-wide maintenance mode

**Controls Required:**
- MFA enforced at all times
- All actions logged and alerted
- Break-glass access with notification to designated oversight contact
- Session time limit (30 minutes)

---

### System Persona: API Consumer (External Integration)
**Actor Type:** Automated system (third-party services)

**Description:**
Represents any external system authenticating to the platform API — including payment processors, shipping carriers, email service providers, or future integrations.

**Key Capabilities:**
- Scoped to specific endpoints only (principle of least privilege)
- Read and/or write access per approved integration spec
- No UI access

**Controls Required:**
- API key or OAuth 2.0 client credentials authentication
- IP allowlist per integration
- Rate limiting enforced
- All API calls logged
- Keys rotatable without service disruption
- Automatic key expiration and renewal workflow

---

### System Persona: Payment Gateway
**Actor Type:** PCI-scoped automated system

**Description:**
The integration between the platform and the payment processor (e.g., Stripe, Braintree). Handles tokenization, charge, refund, and dispute events. This persona defines the PCI DSS cardholder data environment (CDE) boundary.

**Key Capabilities:**
- Tokenize payment methods (no raw card data stored in platform)
- Process charges, refunds, and voids
- Receive and record webhook events (payment succeeded, failed, disputed)
- Sync subscription or recurring billing status

**Controls Required:**
- No card data persisted in platform database
- All communication over TLS 1.2+
- Webhook signature verification required
- PCI DSS SAQ-A or SAQ-A-EP compliance scope
- Restricted to payment endpoints only

---

### System Persona: Email Notification Service
**Actor Type:** Automated system (internal)

**Description:**
The platform's outbound email engine. Sends transactional emails (invoices, quotes, order confirmations, proof approvals, payment receipts, system alerts) and internal notifications.

**Key Capabilities:**
- Template-based email composition
- Triggered by system events (invoice created, payment received, proof returned, etc.)
- Delivery status tracking (sent, delivered, bounced, opened)
- Unsubscribe management for non-transactional emails

**Controls Required:**
- DKIM, SPF, and DMARC configuration required
- No sensitive financial data in email body (link to secure portal instead)
- Delivery logs retained for 90 days
- Bounce and complaint handling per CAN-SPAM / GDPR

---

### System Persona: Reporting Engine
**Actor Type:** Automated system (internal)

**Description:**
Background service responsible for generating scheduled reports, processing large dataset exports, and pre-computing dashboard aggregations.

**Key Capabilities:**
- Generate PDF, Excel, and CSV exports
- Schedule and deliver reports via email or secure download
- Pre-compute KPIs and dashboard metrics on a defined schedule
- Handle large-dataset queries without impacting application performance

**Controls Required:**
- Runs in isolated execution context (cannot modify data)
- Report output stored in temporary secure storage with expiring access links
- Scheduled jobs logged with execution time and record count
- Failure alerts routed to IT Admin persona

---

### System Persona: Backup Service
**Actor Type:** Automated system (infrastructure)

**Description:**
Automated backup agent that captures database snapshots, file storage, and configuration on a defined schedule. Ensures data can be recovered to any point within the retention window.

**Key Capabilities:**
- Automated daily full database backup
- Continuous or hourly transaction log backup (for point-in-time recovery)
- File storage backup (uploaded assets, attachments, documents)
- Backup encryption at rest
- Off-site or geo-redundant storage
- Restoration testing on defined schedule

**Controls Required:**
- Backup success/failure alerts to IT Admin
- Monthly restore drill with documented RTO/RPO results
- Backup access restricted to Backup Service credentials only
- Retention: daily for 30 days, weekly for 90 days, monthly for 1 year

---

### System Persona: Audit Engine
**Actor Type:** Automated system (internal compliance)

**Description:**
Immutable audit trail service. Every user action, system action, data change, and authentication event is written to the audit log by this service.

**Key Capabilities:**
- Write-only from application layer (no update or delete)
- Log: who, what, when, from where (IP), what changed (before/after)
- Query interface for IT Admin and Super Admin
- Export for compliance reviews
- Alert on anomalous patterns (e.g., bulk data export, off-hours privileged access)

**Controls Required:**
- Audit log stored separately from application database
- Tamper-evident (append-only with cryptographic chaining preferred)
- Retention: minimum 1 year hot, 3 years cold archive (SOC 2 requirement)
- Access to audit log read interface restricted to IT Admin and Super Admin

---

### System Persona: CI/CD Pipeline
**Actor Type:** Automated system (infrastructure)

**Description:**
The continuous integration and continuous deployment system. Builds, tests, and deploys application code to staging and production environments.

**Key Capabilities:**
- Automated build on code commit
- Run automated test suite (unit, integration, end-to-end)
- Deploy to staging for QA
- Promote to production on approval
- Rollback on failed health check

**Controls Required:**
- No production credentials in source code (secrets management via vault)
- Production deployment requires human approval gate
- Deployment events logged to audit trail
- Access to production deployment restricted by role

---

### System Persona: Session Manager
**Actor Type:** Automated system (internal security)

**Description:**
Manages user authentication sessions, token issuance, and session invalidation.

**Key Capabilities:**
- Issue short-lived access tokens (JWT or equivalent)
- Maintain refresh token rotation
- Force session termination on password change, permission change, or security event
- Enforce MFA challenge on new device or suspicious login

**Controls Required:**
- Session tokens expire after [15/30] minutes of inactivity (configurable by admin)
- Concurrent session limit per user (configurable)
- Failed login attempt lockout (configurable threshold)
- Session events logged (login, logout, timeout, force-terminate)

---

## 4. Module Overview & Feature Inventory {#module-overview}

| Module | Primary Personas | Core Features |
|---|---|---|
| **Authentication & User Management** | IT Admin, Super Admin | SSO, MFA, RBAC, user provisioning |
| **Executive Dashboard** | Executive | KPI cards, revenue chart, cash position |
| **CRM** | Sales Rep, Sales Manager, CSR | Contacts, accounts, pipeline, activities |
| **Quoting & Estimates** | Sales Rep, Sales Manager | Quote builder, approval, send to customer |
| **Order Management** | Sales Rep, CSR, Production | Order entry, status tracking, job linkage |
| **General Ledger** | Finance Manager | COA, journal entries, period management |
| **Accounts Receivable** | AR Clerk, Finance Manager | Invoicing, payment application, aging |
| **Accounts Payable** | AP Clerk, Finance Manager | Vendor invoices, approval, payment runs |
| **Banking & Reconciliation** | Finance Manager, AR Clerk | Bank feeds, reconciliation, cash management |
| **Financial Reporting** | Finance Manager, Executive | P&L, Balance Sheet, Cash Flow, custom reports |
| **Tax Management** | Finance Manager | Tax codes, calculations, reporting |
| **Inventory Management** | Warehouse Manager, Purchasing | Products, stock levels, locations, adjustments |
| **Purchasing** | Warehouse Manager, AP Clerk | POs, vendor management, receiving, 3-way match |
| **Point of Sale** | Sales Rep, CSR | POS terminal, payment capture, receipts |
| **eCommerce Storefront** | Customers (external), CSR | Product catalog, cart, checkout, account portal |
| **Project & Job Management** | Project Manager, Production Mgr | Job creation, milestones, tasks, resource tracking |
| **Art & Proof Management** | Art Director, Designer, Prepress | Asset upload, proof workflow, approval |
| **Production Scheduling** | Production Manager, Operator | Schedule board, job queue, station dispatch |
| **Time Tracking** | Production Operator, Project Mgr | Time entries against jobs, labor costing |
| **Reporting & Analytics** | All | Report builder, scheduled delivery, exports |
| **Notifications & Alerts** | All | Email, in-app, configurable triggers |
| **Audit Log** | IT Admin, Super Admin | Full event history, search, export |
| **Backup & Recovery** | IT Admin, Super Admin | Backup status, restore initiation |
| **System Administration** | IT Admin, Super Admin | Config, health monitoring, security settings |

---

## 5. Epics {#epics}

### EPIC-01: User Identity & Access Management
Provide secure, role-appropriate access to all platform features. Every user is authenticated, every action is authorized, and every session is auditable.

### EPIC-02: Executive Intelligence Dashboard
Give leadership a real-time, single-pane-of-glass view of business health without requiring any manual report requests.

### EPIC-03: Customer Relationship Management (CRM)
Manage the full customer lifecycle from prospect to retained account, including contacts, activities, pipeline, and communication history.

### EPIC-04: Quoting & Order Management
Enable sales to quickly generate accurate quotes, gain approvals, and convert to orders — with full linkage through production and billing.

### EPIC-05: General Ledger & Financial Foundation
Maintain an accurate, auditable general ledger that supports month-end close, multi-department accounting, and financial reporting.

### EPIC-06: Accounts Receivable
Automate the invoice-to-cash cycle, reduce DSO, and give AR full visibility into customer balances and aging.

### EPIC-07: Accounts Payable
Manage the vendor invoice lifecycle from receipt through payment with approval controls, audit trails, and on-time payment reporting.

### EPIC-08: Banking & Cash Management
Connect bank accounts to the platform for automated transaction import, reconciliation, and real-time cash position visibility.

### EPIC-09: Financial Reporting & Tax
Deliver on-demand and scheduled financial statements, enable regulatory tax compliance, and support audit preparation.

### EPIC-10: Inventory & Warehouse Management
Maintain accurate, real-time inventory across all storage locations with receiving, fulfillment, and cycle count workflows.

### EPIC-11: Purchasing & Vendor Management
Manage vendor relationships, automate purchase orders, and enforce three-way match before payment.

### EPIC-12: Point of Sale
Provide a fast, PCI-compliant point-of-sale terminal for counter and walk-in transactions.

### EPIC-13: eCommerce Storefront
Deliver a public-facing, branded online store for self-service ordering, account management, and proof approval.

### EPIC-14: Project & Job Management
Track every customer job from sales order through production, shipping, and billing — with full visibility across all departments.

### EPIC-15: Art & Proof Management
Formalize the art intake, proofing, and approval workflow so nothing goes to press without documented customer approval.

### EPIC-16: Production Scheduling & Dispatch
Give Production Management a real-time, drag-and-drop production schedule tied to live job data.

### EPIC-17: Time Tracking & Labor Costing
Capture employee time against jobs and calculate actual labor cost versus estimate.

### EPIC-18: Reporting, Analytics & Custom Reports
Give every role a self-service reporting tool that produces accurate, exportable reports without IT involvement.

### EPIC-19: Platform Security & Compliance
Achieve and maintain PCI DSS and SOC 2 Type 2 compliance, with ongoing monitoring, alerts, and audit evidence collection.

### EPIC-20: Backup, Recovery & Business Continuity
Ensure no data is ever lost and the platform can be restored within defined RTO/RPO targets.

### EPIC-21: Notification & Communication Engine
Deliver timely, relevant notifications to every persona via email and in-app alerts triggered by system events.

### EPIC-22: System Administration & Platform Health
Give IT Admin full control over the platform — users, configuration, monitoring, and maintenance — without requiring vendor intervention for routine tasks.

---

## 6. User Stories by Module {#user-stories}

> **Story Format:** As a [persona], I want to [action], so that [outcome].
> **Acceptance Criteria** are prefixed with AC.

---

### Module: User Identity & Access Management (EPIC-01)

---

**US-001**
As an IT Administrator, I want to create a new user account with an assigned role, so that new employees can access the system with appropriate permissions from their first day.

AC-001-1: Admin can create a user by providing name, email, department, and role.
AC-001-2: System sends an email invitation with a secure, time-limited activation link.
AC-001-3: New user is prompted to set a password and enroll in MFA before first login.
AC-001-4: User creation event is recorded in the audit log.

---

**US-002**
As an IT Administrator, I want to deactivate a user account immediately, so that a departing employee loses access the moment I action it.

AC-002-1: Deactivation takes effect within 60 seconds.
AC-002-2: All active sessions for the deactivated user are immediately terminated.
AC-002-3: Deactivated users cannot log in or use API tokens.
AC-002-4: Deactivation event and timestamp are recorded in the audit log.

---

**US-003**
As a user, I want to log in with my email and password plus a second factor (authenticator app or SMS), so that my account is protected even if my password is compromised.

AC-003-1: Login requires both password and MFA token.
AC-003-2: MFA supports TOTP authenticator apps (e.g., Google Authenticator, Authy).
AC-003-3: Failed MFA attempts are logged; account locks after [5] consecutive failures.
AC-003-4: User can register multiple MFA devices and set a backup code.

---

**US-004**
As an IT Administrator, I want to define custom roles with granular permissions, so that I can enforce least-privilege access for every job function.

AC-004-1: Admin can create named roles with toggleable permissions per module.
AC-004-2: Permissions are additive; users can have multiple roles.
AC-004-3: Role changes take effect on next login or within [15] minutes.
AC-004-4: Role changes are recorded in the audit log with before/after state.

---

**US-005**
As a Super Administrator, I want to review a log of all user actions taken in the system, so that I can investigate security incidents or compliance questions.

AC-005-1: Audit log records: user, action type, timestamp, IP address, affected record(s), before/after values.
AC-005-2: Log is searchable by user, date range, action type, and module.
AC-005-3: Log is exportable to CSV or PDF.
AC-005-4: Log entries cannot be modified or deleted by any user including Super Admin.

---

**US-006**
As a user, I want to reset my password via a secure link sent to my email, so that I can regain access without contacting IT for every lockout.

AC-006-1: Password reset link expires after 15 minutes.
AC-006-2: Reset link is single-use only.
AC-006-3: Previous password cannot be reused (enforce last 5 passwords).
AC-006-4: Password reset event is logged with timestamp and IP address.

---

**US-007**
As an IT Administrator, I want to configure SSO with our identity provider (e.g., Microsoft Azure AD or Google Workspace), so that users log in once for all systems.

AC-007-1: SSO supports SAML 2.0 or OAuth 2.0 / OIDC.
AC-007-2: Users provisioned via SSO inherit role from identity provider group mapping.
AC-007-3: SSO login events are logged in the platform audit trail.
AC-007-4: MFA enforcement can be delegated to identity provider or enforced at platform level.

---

### Module: Executive Dashboard (EPIC-02)

---

**US-010**
As an Executive, I want to see a real-time dashboard of revenue, gross margin, and cash position for the current month and YTD, so that I can quickly assess business health.

AC-010-1: Dashboard loads in under 3 seconds.
AC-010-2: Metrics include: MTD Revenue, YTD Revenue, Gross Margin %, Cash Balance, Open Receivables, Open Payables.
AC-010-3: Each metric is clickable to drill into the underlying transactions.
AC-010-4: Dashboard data refreshes automatically (no manual refresh required).

---

**US-011**
As an Executive, I want to see a sales pipeline summary showing open deals by stage and total pipeline value, so that I can assess future revenue expectations.

AC-011-1: Pipeline view shows deal count and total value by stage.
AC-011-2: Pipeline is filterable by sales rep and date range.
AC-011-3: Clicking a stage shows the underlying CRM opportunities.

---

**US-012**
As an Executive, I want to see a production throughput summary (jobs in queue, in production, completed this week), so that I can assess operational health without calling the production manager.

AC-012-1: Dashboard card shows: jobs awaiting art, jobs in production, jobs shipped, jobs overdue.
AC-012-2: Overdue jobs are highlighted in a distinct color.
AC-012-3: Clicking any status opens the filtered production board.

---

### Module: CRM (EPIC-03)

---

**US-020**
As a Sales Representative, I want to create a new customer contact with company, phone, and email, so that I can start tracking the relationship in the system.

AC-020-1: Contact form requires: first name, last name, company, email.
AC-020-2: Duplicate detection warns if email or company name already exists.
AC-020-3: Contact is visible to all Sales Reps and Sales Manager after creation.
AC-020-4: Creation event logged with creating user and timestamp.

---

**US-021**
As a Sales Representative, I want to log a call, meeting, or email activity against a contact, so that the full communication history is in one place.

AC-021-1: Activity types: call, email, meeting, note, task.
AC-021-2: Activity requires: type, date, duration (optional), summary.
AC-021-3: Activities are displayed chronologically on the contact timeline.
AC-021-4: Activities linked to related opportunity if applicable.

---

**US-022**
As a Sales Representative, I want to create an opportunity (deal) linked to a contact or account, so that I can track potential revenue through my pipeline.

AC-022-1: Opportunity requires: name, account, estimated value, expected close date, stage.
AC-022-2: Stage options are configurable by Sales Manager.
AC-022-3: Opportunity appears in the pipeline view immediately on creation.
AC-022-4: Opportunity can be linked to a quote when one is created.

---

**US-023**
As a Sales Manager, I want to view a consolidated pipeline for all reps showing deals by stage and expected close date, so that I can forecast revenue and coach my team.

AC-023-1: Pipeline view filterable by rep, stage, date range, and deal value.
AC-023-2: Kanban and list view options available.
AC-023-3: Total value displayed for each stage column.
AC-023-4: Drill-down to individual deal from pipeline view.

---

**US-024**
As a Customer Service Representative, I want to view a full account history for a customer (orders, invoices, payments, communications), so that I can answer inquiries in a single screen.

AC-024-1: Account view shows: contact info, open orders, invoice history, payment history, communication history, active jobs.
AC-024-2: Each record type is linkable to the source record in its module.
AC-024-3: View available to CSR role without edit access to financial records.

---

### Module: Quoting & Order Management (EPIC-04)

---

**US-030**
As a Sales Representative, I want to generate a quote for a customer that includes products, quantities, and pricing, so that I can quickly send a professional estimate.

AC-030-1: Quote builder pulls products from the product catalog with list pricing.
AC-030-2: Rep can override price within their authorized discount limit.
AC-030-3: Discounts above rep limit require Sales Manager approval before sending.
AC-030-4: Quote includes: customer details, line items, subtotal, tax, total, expiration date.
AC-030-5: Quote is generated as a branded PDF and can be emailed directly from the system.

---

**US-031**
As a Sales Representative, I want to convert an approved quote to a sales order with one click, so that there is no re-entry of data between quoting and order entry.

AC-031-1: "Convert to Order" button appears on accepted/approved quotes.
AC-031-2: All line items, pricing, and customer details carry over from quote to order.
AC-031-3: Order number is generated automatically and linked back to the source quote.
AC-031-4: Order triggers job creation notification to Production Manager.

---

**US-032**
As a Customer Service Representative, I want to view the status of any order (entered, in production, shipped, invoiced), so that I can answer customer status inquiries without calling production.

AC-032-1: Order detail view shows current status, status history, and timestamps.
AC-032-2: Status is updated in real time as production updates job progress.
AC-032-3: Expected ship date visible on order record.

---

**US-033**
As a Sales Manager, I want to approve or reject a quote where the discount exceeds the rep's authority, so that margin is protected before quotes go to customers.

AC-033-1: Quotes pending approval are shown in a Sales Manager approval queue.
AC-033-2: Manager can approve, reject, or modify the discount before approval.
AC-033-3: Rep is notified by email and in-app when quote is approved or rejected.
AC-033-4: Approval action and approver name are recorded on the quote record.

---

### Module: Accounts Receivable (EPIC-06)

---

**US-050**
As an AR Clerk, I want to generate an invoice from a completed sales order, so that billing is accurate and tied directly to what was sold.

AC-050-1: Invoice can be auto-generated from a shipped/completed order.
AC-050-2: Invoice inherits all line items, pricing, and customer details from the order.
AC-050-3: Invoice includes: invoice number, invoice date, due date, payment terms, line items, tax, total due.
AC-050-4: Invoice is saved as a draft until reviewed and sent.

---

**US-051**
As an AR Clerk, I want to email an invoice to the customer directly from the system, so that there is no manual step of downloading and attaching to an email.

AC-051-1: "Send Invoice" action generates a branded email with the invoice attached as PDF.
AC-051-2: Email includes a secure payment link (if payment portal is enabled).
AC-051-3: Send event recorded with timestamp and recipient address.
AC-051-4: Customer receives email from a company-configured sending address.

---

**US-052**
As an AR Clerk, I want to apply a payment received (check, ACH, credit card) to one or more open invoices, so that the customer's balance is updated immediately.

AC-052-1: Payment entry requires: payment date, amount, method (check/ACH/CC), reference number.
AC-052-2: Payment can be applied to one or multiple open invoices.
AC-052-3: Partial payment supported; remaining balance stays on invoice.
AC-052-4: Payment applied event posts to GL automatically.

---

**US-053**
As an AR Clerk, I want to view an aging report grouped by customer and aging bucket (current, 1–30, 31–60, 61–90, 90+), so that I can prioritize collections.

AC-053-1: Report as-of date is selectable.
AC-053-2: Report shows balance by aging bucket per customer.
AC-053-3: Report exportable to PDF and Excel.
AC-053-4: Drill-down from aging summary to open invoice detail.

---

**US-054**
As an AR Clerk, I want the system to automatically send payment reminder emails to customers with overdue invoices, so that I spend less time on manual follow-up.

AC-054-1: Reminder rules are configurable: days past due threshold, email template, frequency.
AC-054-2: Reminders are sent on a scheduled basis without manual initiation.
AC-054-3: Reminder events are logged on the customer account and invoice record.
AC-054-4: Customers can be excluded from automated reminders individually.

---

### Module: Accounts Payable (EPIC-07)

---

**US-060**
As an AP Clerk, I want to enter a vendor invoice against an existing purchase order, so that the three-way match (PO, receipt, invoice) can be validated before payment.

AC-060-1: Invoice entry links to open PO by PO number.
AC-060-2: System checks invoice line items against PO and receipt quantities; flags discrepancies.
AC-060-3: Invoice cannot be approved for payment if match fails without override and justification.
AC-060-4: All three documents (PO, receipt, invoice) are accessible from the invoice record.

---

**US-061**
As a Finance Manager, I want to approve vendor invoices above a defined threshold before they are paid, so that spending is controlled.

AC-061-1: Invoices above [configurable threshold] are routed to Finance Manager approval queue.
AC-061-2: Finance Manager receives email notification and in-app alert for pending approvals.
AC-061-3: Approval or rejection recorded with approver name, timestamp, and optional note.
AC-061-4: Rejected invoices are returned to AP Clerk with reason.

---

**US-062**
As an AP Clerk, I want to generate a payment run for all approved invoices due within a date range, so that I can pay vendors on time efficiently.

AC-062-1: Payment run selection filters by due date range, vendor, and payment method.
AC-062-2: Run shows total payment amount before execution.
AC-062-3: Payment run requires Finance Manager approval before processing.
AC-062-4: Payments post to GL and update invoice status automatically.

---

**US-063**
As an AP Clerk, I want to view the AP aging report showing what is owed to each vendor by aging bucket, so that I can proactively manage cash outflow.

AC-063-1: Report shows vendor name, invoice count, and balance by aging bucket.
AC-063-2: Report as-of date is selectable.
AC-063-3: Report exportable to PDF and Excel.

---

### Module: Inventory Management (EPIC-10)

---

**US-080**
As a Warehouse Manager, I want to receive goods against a purchase order, so that inventory is updated immediately and the PO is closed out accurately.

AC-080-1: Receiving screen shows open PO line items with expected quantities.
AC-080-2: Received quantity entered per line; partial receipt supported.
AC-080-3: Receipt creates an inventory transaction updating on-hand quantity.
AC-080-4: Receipt record is linked to PO and available for three-way match.

---

**US-081**
As a Warehouse Manager, I want to view current stock levels for all products across all storage locations, so that I know what is available without a physical count.

AC-081-1: Inventory view shows product, location, on-hand quantity, committed quantity, available quantity.
AC-081-2: View is filterable by product category, location, and below-reorder-point.
AC-081-3: Stock level is updated in real time as transactions are recorded.

---

**US-082**
As a Warehouse Manager, I want to conduct a cycle count for a product category and reconcile variances, so that system inventory stays accurate without a full physical count.

AC-082-1: Cycle count creates a count sheet for selected products.
AC-082-2: Counted quantities entered against expected quantities.
AC-082-3: Variances displayed before posting; Finance Manager notified of variances above threshold.
AC-082-4: Count post creates adjustment transactions with audit trail.

---

**US-083**
As a Warehouse Manager, I want to receive an alert when a product's on-hand quantity falls below its reorder point, so that I can create a purchase order before we run out.

AC-083-1: Reorder point is configurable per product.
AC-083-2: Alert is sent to Warehouse Manager via email and in-app notification.
AC-083-3: Alert includes: product name, current quantity, reorder point, preferred vendor.
AC-083-4: One-click action to create a draft PO from the alert.

---

### Module: Project & Job Management (EPIC-14)

---

**US-100**
As a Project Manager, I want to view the complete status of a customer job in a single screen — including sales, art, production, and shipping — so that I can answer client inquiries without reaching out to multiple departments.

AC-100-1: Job detail view shows: customer, order details, art status, production status, ship date, invoice status.
AC-100-2: Status for each stage is updated in real time by the responsible department.
AC-100-3: View accessible to Project Manager, Sales Rep, and CSR (read-only).

---

**US-101**
As a Production Manager, I want to see a production schedule board showing all active jobs, their status, and assigned equipment/station, so that I can manage throughput and avoid bottlenecks.

AC-101-1: Schedule board shows jobs as cards organized by status column (queued, in-press, finishing, complete).
AC-101-2: Job cards show: job number, customer name, due date, quantity, and press assignment.
AC-101-3: Cards are drag-and-droppable to reorder queue or change status.
AC-101-4: Overdue jobs are visually highlighted.

---

**US-102**
As an Art Director, I want to upload finished artwork for a job and send a digital proof to the customer for approval, so that we have documented approval before going to press.

AC-102-1: Art upload accepts common file types (PDF, AI, EPS, TIFF, PNG, JPG).
AC-102-2: System generates a proof notification email to the customer with a secure review link.
AC-102-3: Customer can approve or reject the proof with a comment from the link (no login required for customer).
AC-102-4: Approval or rejection is recorded with customer name (from link), timestamp, and any comments.
AC-102-5: Art team and Project Manager receive notification upon customer response.

---

**US-103**
As a Production Operator, I want to view my job queue for my workstation and update job status as I complete each stage, so that the rest of the organization knows the real-time production status.

AC-103-1: Operator sees only jobs assigned to their workstation.
AC-103-2: Operator can update status: started, paused, completed, scrapped.
AC-103-3: Status update is immediately visible to Production Manager and Project Manager.
AC-103-4: Operator can flag an issue with a note without completing the job.

---

### Module: eCommerce Storefront (EPIC-13)

---

**US-110**
As a customer (external), I want to browse the product catalog and add items to a cart without creating an account, so that I can quickly evaluate products before committing.

AC-110-1: Public catalog is accessible without login.
AC-110-2: Products display: name, description, price, available options, imagery.
AC-110-3: Out-of-stock products are clearly labeled.
AC-110-4: Cart persists across browser sessions (cookie-based).

---

**US-111**
As a customer, I want to check out and pay with a credit or debit card, so that I can complete my purchase online without calling or emailing.

AC-111-1: Checkout collects: billing info, shipping address, payment card (via PCI-compliant hosted fields).
AC-111-2: No card data is stored in the platform database; tokenization handled by payment gateway.
AC-111-3: Order confirmation email sent immediately on successful payment.
AC-111-4: Order is created in the platform's Order Management module automatically.

---

**US-112**
As a registered customer, I want to log in to a self-service portal and view my order history and invoice status, so that I can track my account without calling.

AC-112-1: Customer portal shows: open orders, order history, invoices, payments, proofs awaiting approval.
AC-112-2: Invoice PDF downloadable from portal.
AC-112-3: Online payment of open invoices supported from portal.

---

### Module: Point of Sale (EPIC-12)

---

**US-120**
As a Sales Representative, I want to enter a walk-in or counter sale and accept payment on the spot, so that in-person transactions are handled as quickly as e-commerce orders.

AC-120-1: POS interface is simplified for speed: product search, quantity, price, payment.
AC-120-2: Accepts credit/debit card (PCI-compliant terminal integration), cash, and check.
AC-120-3: Receipt printed or emailed immediately after payment.
AC-120-4: POS transaction creates an order and invoice in the system automatically.

---

### Module: Financial Reporting (EPIC-09)

---

**US-130**
As a Finance Manager, I want to generate a Profit & Loss statement for any date range and compare it to budget or prior period, so that I can identify variances without manual spreadsheet work.

AC-130-1: P&L report is date-range selectable (MTD, QTD, YTD, or custom).
AC-130-2: Comparison column: prior period, prior year, or budget (if budget module active).
AC-130-3: Variance column shows amount and percentage difference.
AC-130-4: Report exportable to PDF and Excel.
AC-130-5: Report can be scheduled for automatic delivery to designated email list.

---

**US-131**
As a Finance Manager, I want to generate a Balance Sheet as of any date, so that I have an accurate snapshot of assets, liabilities, and equity.

AC-131-1: Balance sheet as-of date is user-selectable.
AC-131-2: Standard GAAP structure: assets, liabilities, equity.
AC-131-3: Drill-down from any balance to underlying transactions.
AC-131-4: Exportable to PDF and Excel.

---

**US-132**
As a Finance Manager, I want to perform bank reconciliation by importing a bank statement and matching transactions to GL entries, so that bank and book balances are confirmed each month.

AC-132-1: Bank statement importable via CSV or OFX file, or via bank feed API (if supported).
AC-132-2: System auto-matches transactions where amount and date align.
AC-132-3: Unmatched transactions listed for manual review.
AC-132-4: Reconciliation report generated and locked on completion.

---

### Module: Platform Security & Compliance (EPIC-19)

---

**US-140**
As a Super Administrator, I want all user actions logged in a tamper-evident audit trail, so that I can demonstrate compliance and investigate incidents.

AC-140-1: Every data create, update, delete, and view operation is logged.
AC-140-2: Every authentication event (success, failure, MFA, logout) is logged.
AC-140-3: Audit log is stored independently from the application database.
AC-140-4: Audit entries cannot be deleted or modified by any account.
AC-140-5: Log includes: timestamp, user ID, user display name, IP address, user agent, action type, affected record ID and type, before/after values (for changes).

---

**US-141**
As an IT Administrator, I want to verify that automated backups ran successfully each day and test a restore, so that I can be confident data is recoverable.

AC-141-1: Daily backup success/failure status is displayed on the Admin dashboard.
AC-141-2: Admin receives email alert on backup failure within 15 minutes.
AC-141-3: Admin can initiate a restore to a staging environment from any backup point.
AC-141-4: Restore completion is logged with timestamp, backup point used, and initiating user.

---

**US-142**
As a Super Administrator, I want to receive an alert if an account attempts to log in from an unfamiliar location or device, so that I can respond to potential account compromise.

AC-142-1: Anomalous login detection is configurable (new device, new geography, off-hours).
AC-142-2: Alert sent to IT Admin and optionally to the affected user.
AC-142-3: Alert includes: login timestamp, IP address, approximate location, device information.
AC-142-4: Admin can force terminate the suspicious session from the alert notification.

---

## 7. Non-Functional Requirements {#non-functional-requirements}

| Category | Requirement |
|---|---|
| **Performance** | Page load time ≤ 2 seconds for 95th percentile under normal load |
| **Performance** | Report generation ≤ 10 seconds for standard reports |
| **Availability** | 99.9% uptime (≤ 8.7 hours downtime per year) |
| **Availability** | Planned maintenance windows communicated 72 hours in advance |
| **Scalability** | Platform supports concurrent users without performance degradation (target: [X] concurrent) |
| **Security** | TLS 1.2+ enforced for all client-server communication |
| **Security** | AES-256 encryption for all data at rest |
| **Security** | Passwords stored using bcrypt or Argon2 (never plaintext or reversible) |
| **Security** | Automated vulnerability scanning on every code deployment |
| **Data Retention** | Financial data retained for 7 years minimum |
| **Data Retention** | Audit log retained for 3 years minimum |
| **Backup** | Recovery Point Objective (RPO): ≤ 1 hour |
| **Backup** | Recovery Time Objective (RTO): ≤ 4 hours |
| **Browser Support** | Chrome 120+, Firefox 120+, Safari 17+, Edge 120+ |
| **Accessibility** | WCAG 2.1 AA compliance target |
| **Internationalization** | US English primary; currency and date format configurable |

---

## 8. Compliance Requirements {#compliance-requirements}

### PCI DSS (Payment Card Industry Data Security Standard)

| Control Area | Requirement |
|---|---|
| Cardholder Data | No raw card data stored in platform database; tokenization via certified payment gateway |
| Network Security | Firewall configuration protecting cardholder data environment |
| Access Control | Least privilege access to any system in payment data path |
| Encryption | Card data transmitted only over TLS 1.2+ |
| Monitoring | All access to cardholder data environment logged and monitored |
| Vulnerability Management | Regular vulnerability scans; penetration test prior to launch |
| Policy | Written information security policy covering cardholder data |

### SOC 2 Type 2 (Trust Services Criteria)

| Trust Criteria | Key Controls |
|---|---|
| **Security** | Logical access controls, MFA, encryption, vulnerability management, penetration testing |
| **Availability** | Uptime monitoring, incident response, DR testing, SLA |
| **Processing Integrity** | Input validation, error handling, change management, audit trail |
| **Confidentiality** | Data classification, encryption, NDA with vendors, access controls |
| **Privacy** | Data collection minimization, retention policy, subject rights (if applicable) |

> SOC 2 Type 2 certification requires a minimum 6-month observation period. The audit period will be defined in Phase 8 planning and will begin during active production operation.

---

## 9. Integration Requirements (Preliminary) {#integrations}

| Integration | Purpose | Direction | Priority |
|---|---|---|---|
| Payment Gateway (Stripe / Braintree) | Payment processing for eCommerce, POS, AR | Bi-directional | P0 |
| Email Service (SendGrid / Postmark / SES) | Transactional email delivery | Outbound | P0 |
| Bank Feed API | Automated bank transaction import for reconciliation | Inbound | P1 |
| Shipping Carrier (UPS / FedEx / USPS) | Rate quoting and label generation | Bi-directional | P1 |
| Sales Tax API (TaxJar / Avalara) | Automated tax calculation and filing | Bi-directional | P1 |
| Identity Provider (Azure AD / Google) | SSO for internal users | Bi-directional | P1 |
| Cloud File Storage (S3 / Azure Blob) | Art file and document storage | Bi-directional | P0 |
| Sage 100 (Legacy) | Data export/migration (Phase 1 assessment required) | One-time import | P2 |
| Accounting / Tax Software | Export for CPA/tax preparer | Outbound | P2 |

---

## 10. RBAC Matrix — Draft {#rbac-matrix}

> **Legend:** F = Full Access | R = Read Only | C = Create Only | A = Approve Only | — = No Access

| Module | Super Admin | IT Admin | Executive | Finance Mgr | Sales Mgr | Sales Rep | CSR | AR Clerk | AP Clerk | Art Director | Designer | Prepress | Prod Manager | Prod Operator | Warehouse Mgr | Project Mgr |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| User Management | F | F | — | — | R | — | — | — | — | — | — | — | — | — | — | — |
| Audit Log | F | R | — | — | — | — | — | — | — | — | — | — | — | — | — | — |
| System Config | F | F | — | — | — | — | — | — | — | — | — | — | — | — | — | — |
| Exec Dashboard | F | — | F | R | R | — | — | — | — | — | — | — | — | — | — | — |
| CRM | F | — | R | R | F | F | R | — | — | — | — | — | — | — | — | R |
| Quoting | F | — | R | R | F | F | R | — | — | — | — | — | — | — | — | R |
| Orders | F | — | R | R | F | F | F | R | — | — | — | — | R | R | — | F |
| GL / Journal Entries | F | — | R | F | — | — | — | — | — | — | — | — | — | — | — | — |
| Accounts Receivable | F | — | R | F | — | — | R | F | — | — | — | — | — | — | — | — |
| Accounts Payable | F | — | R | F | — | — | — | — | F | — | — | — | — | — | — | — |
| Banking & Recon | F | — | R | F | — | — | — | R | — | — | — | — | — | — | — | — |
| Financial Reports | F | — | R | F | R | — | — | R | R | — | — | — | — | — | — | — |
| Inventory | F | — | R | R | R | R | R | — | — | — | — | — | R | — | F | R |
| Purchasing / POs | F | — | R | A | — | — | — | — | F | — | — | — | R | — | F | — |
| Point of Sale | F | — | R | R | F | F | F | — | — | — | — | — | — | — | — | — |
| eCommerce Mgmt | F | — | R | — | F | — | R | — | — | — | — | — | — | — | — | — |
| Job Management | F | — | R | R | R | R | R | R | — | R | R | R | F | R | — | F |
| Art / Proofing | F | — | R | — | — | — | — | — | — | F | F | F | R | — | — | R |
| Production Schedule | F | — | R | — | — | — | — | — | — | R | R | R | F | R | — | R |
| Time Tracking | F | — | R | R | R | — | — | — | — | — | — | F | F | F | — | R |
| Reports & Analytics | F | R | F | F | F | R | R | R | R | — | — | — | R | — | R | R |
| Backup & Recovery | F | F | — | — | — | — | — | — | — | — | — | — | — | — | — | — |
| Notifications Config | F | F | — | — | — | — | — | — | — | — | — | — | — | — | — | — |

---

---

## 11. SAP Feature Parity — Additional Epics & User Stories {#sap-parity}

> **Scope Clarification (July 2026):** Great Mountain West is replacing **SAP** as its primary ERP. Sage 100 defines the minimum feature baseline. SAP defines the full target feature set. All SAP module equivalents listed below must be represented in the platform.

---

### SAP Module Mapping

| SAP Module | Description | Platform Equivalent |
|---|---|---|
| FI — Financial Accounting | GL, AR, AP, Bank Accounting, Asset Accounting | Accounting Suite (existing + Asset Accounting) |
| CO — Controlling | Cost Center, Profit Center, Internal Orders | Controlling & Profitability module (new) |
| CO-PA — Profitability Analysis | Margin analysis by customer/product/channel | Profitability Analysis module (new) |
| AA — Asset Accounting | Fixed asset register, depreciation | Asset Accounting module (new) |
| SD — Sales & Distribution | Pricing, credit management, document flow | CRM & Sales (expanded) |
| MM — Materials Management | Purchasing, receiving, inventory, MRP | Inventory & MRP (expanded) |
| WM — Warehouse Management | Bin management, putaway, picking | Advanced Warehouse module (new) |
| PP — Production Planning | MRP, shop floor control, capacity planning | MRP + Production (new) |
| PS — Project System | WBS, project costing, milestones | Job Management (expanded) |
| QM — Quality Management | Inspection plans, defect tracking, notifications | Quality Management module (new) |
| PM — Plant Maintenance | Equipment maintenance, work orders, downtime | Equipment Maintenance module (new) |
| FI-AA — Fixed Assets | Asset lifecycle, depreciation methods | Asset Accounting module (new) |

---

### Additional Personas

---

#### Persona: Controller / CFO
**Role Examples:** Controller, CFO, VP Finance

**Goals:**
- Full visibility into cost center and profit center performance
- Manage intercompany transactions and consolidations
- Analyze profitability by customer, product line, and channel
- Maintain fixed asset register and depreciation schedules

**Key Permissions Needed:**
- Full access to Controlling, CO-PA, and Asset Accounting modules
- All Finance Manager permissions
- Intercompany transaction management
- Consolidation reporting

---

#### Persona: Cost Accountant
**Role Examples:** Cost Accountant, Management Accountant

**Goals:**
- Maintain standard costs and analyze variances
- Allocate costs across cost centers
- Produce job costing reports (actual vs. standard vs. estimate)
- Support month-end controlling close

**Key Permissions Needed:**
- Full access to Controlling module
- Read access to Production and Inventory
- Cost center allocation management

---

#### Persona: Equipment / Maintenance Manager
**Role Examples:** Facilities Manager, Maintenance Supervisor, Press Room Manager

**Goals:**
- Schedule and track maintenance for all press and finishing equipment
- Record downtime and calculate press utilization
- Manage maintenance work orders and parts inventory

**Key Permissions Needed:**
- Full access to Equipment Maintenance module
- Read access to Production Schedule
- View inventory of maintenance parts and supplies

---

### Additional Epics (EPIC-23 through EPIC-35)

**EPIC-23: Asset Accounting & Fixed Asset Management**
Maintain a complete fixed asset register covering all press equipment, finishing equipment, vehicles, and property. Calculate and post depreciation automatically on defined schedules. Support asset additions, disposals, transfers, and revaluations. SAP FI-AA parity.

**EPIC-24: Cost Center & Profit Center Accounting**
Track costs by department and cost center. Allocate shared costs using configurable distribution rules. Produce cost center P&L reports and variance analysis. SAP CO parity.

**EPIC-25: Profitability Analysis (CO-PA)**
Analyze gross and net margin by customer, product, product category, sales channel, and region. Support actual and plan/budget comparison. Drill from summary to transaction level. SAP CO-PA parity.

**EPIC-26: Internal Orders & Budget Management**
Create internal orders for capital projects, marketing spend, or one-time cost tracking. Assign budgets, track actuals, and report variances. Close and settle orders to cost centers or assets.

**EPIC-27: Material Requirements Planning (MRP)**
Calculate material requirements based on job schedule and open orders. Generate planned purchase orders automatically. Manage MRP runs by planning horizon and material group. Identify shortages before production starts. SAP PP/MRP parity.

**EPIC-28: Advanced Pricing & Contract Management**
Support complex pricing conditions: base price, volume discounts, customer-specific pricing, contract pricing, surcharges, and freight. Maintain customer price agreements and contracts with validity periods. SAP SD pricing condition parity.

**EPIC-29: Credit Management**
Define customer credit limits. Calculate real-time credit exposure including open orders, open invoices, and deliveries. Block or warn on orders that breach credit limits. Escalation workflow for credit hold override.

**EPIC-30: Quality Management**
Define inspection plans for incoming materials and finished goods. Record inspection results and defects. Manage quality notifications and corrective actions. Integration with production and receiving workflows. SAP QM parity.

**EPIC-31: Equipment & Plant Maintenance**
Maintain an equipment master for all presses and finishing equipment. Schedule preventive maintenance. Record corrective maintenance work orders with labor, parts, and downtime. Track press utilization and maintenance cost per machine. SAP PM parity.

**EPIC-32: Multi-Entity & Intercompany Accounting**
Support multiple legal entities or business units under one platform instance. Post intercompany transactions with automatic elimination entries. Produce consolidated financial statements. Manage intercompany billing and reconciliation.

**EPIC-33: Document Flow & End-to-End Traceability**
Every transaction is linked in a complete document chain: Quote → Order → Production Job → Delivery → Invoice → Payment. Every document references its predecessors and successors. Full audit trail visible from any point in the chain. SAP document flow parity.

**EPIC-34: EDI & Electronic Invoicing**
Send and receive electronic documents (purchase orders, invoices, shipping notices) in standard EDI formats (X12, EDIFACT) or API-based formats. Support e-invoicing mandates and customer-specific EDI requirements.

**EPIC-35: Configurable Workflow & Approval Engine**
Define multi-step approval workflows for any document type (invoices, purchase orders, credit holds, journal entries, quotes). Configure approvers by role, amount threshold, cost center, or department. Delegations and escalations on timeout.

---

### Additional User Stories — SAP Parity

---

**US-200 — Asset Accounting**
As a Finance Manager, I want to add a new press to the fixed asset register with acquisition cost, useful life, and depreciation method, so that depreciation is calculated and posted automatically each period.

AC-200-1: Asset master includes: asset number, description, category, acquisition date, cost, useful life, depreciation method (straight-line, declining balance).
AC-200-2: Depreciation posts to GL automatically on period close.
AC-200-3: Asset register report shows net book value, accumulated depreciation, and remaining useful life per asset.
AC-200-4: Asset disposals and transfers are recorded with gain/loss posting.

---

**US-201 — Cost Center Accounting**
As a Controller, I want to view a cost center report showing actual spend vs. budget for each department this month, so that I can identify and address overspending before period close.

AC-201-1: Cost center report shows: cost center, cost element, budget, actual, variance ($ and %).
AC-201-2: Report is available in real time (not batch).
AC-201-3: Drill-down from cost center total to individual postings.
AC-201-4: Report exportable to Excel.

---

**US-202 — Cost Allocation**
As a Cost Accountant, I want to allocate shared costs (facilities, IT, utilities) to production cost centers using a configured distribution key, so that departmental P&Ls reflect true cost of operations.

AC-202-1: Allocation rules configurable by: sender cost center, receiver cost centers, distribution basis (headcount, square footage, revenue, manual %).
AC-202-2: Allocations run on a scheduled basis (monthly) or on demand.
AC-202-3: Allocation postings are reversible for correction.
AC-202-4: Allocation log shows sender, receiver, basis, and amount for each cycle.

---

**US-203 — Profitability Analysis**
As a Controller, I want to see gross margin by customer and by product category for the current quarter, so that I can identify which customers and products are driving profitability.

AC-203-1: CO-PA report shows: revenue, cost of goods, gross margin, gross margin % — sliceable by customer, product category, sales rep, and channel.
AC-203-2: Plan vs. actual comparison available.
AC-203-3: Drill-down from summary to underlying sales orders and cost postings.
AC-203-4: Top 10 / Bottom 10 customers by margin available as a standard view.

---

**US-204 — Material Requirements Planning**
As a Warehouse Manager, I want the system to automatically calculate what paper, ink, and substrate I need to order based on the production schedule for the next two weeks, so that I never run short mid-job.

AC-204-1: MRP calculates net requirements by material based on confirmed job schedule and current stock levels.
AC-204-2: MRP generates planned purchase orders for each shortage.
AC-204-3: Planner can review, modify, and release planned POs before they are sent to vendors.
AC-204-4: MRP run is configurable by planning horizon (days) and material group.
AC-204-5: Shortage report shows material, job, quantity needed, quantity available, and gap.

---

**US-205 — Advanced Pricing**
As a Sales Manager, I want to configure a customer-specific pricing agreement for a key account that applies volume discounts and contract pricing automatically when a quote is created, so that reps don't have to manually calculate or remember special terms.

AC-205-1: Pricing agreements configurable by: customer, product, validity period, price type (fixed, discount %, surcharge).
AC-205-2: Pricing conditions apply automatically when a quote is created for the qualifying customer.
AC-205-3: Multiple conditions can stack (base price → volume discount → freight surcharge).
AC-205-4: Price agreement expiry is alerted to Sales Manager 30 days before expiration.

---

**US-206 — Credit Management**
As a Finance Manager, I want to define a credit limit for each customer and have the system block or warn on orders that would breach that limit, so that we do not extend credit beyond approved exposure.

AC-206-1: Credit limit defined per customer in AR/Credit Management module.
AC-206-2: Real-time credit exposure calculated as: open invoices + open orders + open deliveries.
AC-206-3: Order entry warns (soft block) or prevents (hard block) when exposure would breach limit — configurable per customer.
AC-206-4: Credit hold override requires Finance Manager or Sales Manager approval with audit log entry.
AC-206-5: Credit exposure report shows all customers near or over limit.

---

**US-207 — Quality Inspection**
As a Warehouse Manager, I want to trigger a quality inspection when goods are received against a purchase order for paper stock, so that substandard material is identified before it goes to production.

AC-207-1: Inspection lot created automatically on receipt for materials requiring inspection.
AC-207-2: Inspector records: inspection results, sample size, defects found, pass/fail decision.
AC-207-3: Failed inspection prevents material from being released to production (stock blocked).
AC-207-4: Quality notification created automatically on failure, routed to Purchasing for vendor follow-up.

---

**US-208 — Equipment Maintenance**
As an Equipment Maintenance Manager, I want to schedule preventive maintenance for each press on a defined interval (e.g., every 500 press hours or every 90 days), so that maintenance never gets missed and equipment downtime is minimized.

AC-208-1: Equipment master stores: machine name, model, serial number, location, manufacturer, purchase date, warranty expiry.
AC-208-2: Maintenance plans configurable by: interval type (time-based, counter-based), maintenance tasks, estimated duration, required parts.
AC-208-3: System generates maintenance work orders automatically when interval is due.
AC-208-4: Work order records: actual labor, parts used, downtime start/end, technician.
AC-208-5: Equipment history report shows all maintenance events, downtime, and cost per machine.

---

**US-209 — Intercompany Accounting**
As a Controller, I want to post an intercompany charge from one business entity to another and have the elimination entry created automatically, so that consolidated financial statements are accurate without manual adjustments.

AC-209-1: Intercompany transactions require both a sending and receiving entity.
AC-209-2: Corresponding entry created automatically in the receiving entity's ledger.
AC-209-3: Intercompany balances are highlighted in the consolidation report for review.
AC-209-4: Elimination entries generated automatically on consolidation run.

---

**US-210 — Document Flow**
As a Customer Service Representative, I want to view the complete document chain for any customer order — from the original quote through production job, delivery, invoice, and payment — in a single linked view, so that I can answer any customer inquiry without navigating multiple modules.

AC-210-1: Document flow view shows all linked documents in chronological chain.
AC-210-2: Each document in the chain is clickable to open the source record.
AC-210-3: Document flow available from any point in the chain (open the quote or the invoice — same view).
AC-210-4: Status of each document shown inline (open, completed, cancelled).

---

**US-211 — Configurable Approval Workflow**
As an IT Administrator, I want to configure a multi-step approval workflow for vendor invoices above $10,000 that routes to the AP Clerk's manager and then to the Controller, so that high-value payments are always reviewed before processing.

AC-211-1: Workflow rules configurable by: document type, amount threshold, cost center, department.
AC-211-2: Approver defined by role, named user, or dynamic (manager of submitter).
AC-211-3: Each approver receives email and in-app notification.
AC-211-4: Timeout escalation configurable (e.g., escalate to next level after 48 hours with no action).
AC-211-5: Approval history with timestamps and comments recorded on every document.
AC-211-6: Delegation rules configurable for out-of-office coverage.

---

*End of Phase 1 Discovery Documentation — v1.1 (Updated July 2026 — SAP parity scope added)*
*Great Mountain West / Christopher Wall — Confidential*
