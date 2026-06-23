# Security And Privacy Standard

Security and privacy override delivery speed.

## Mandatory Rules

- Do not commit credentials, `.env` secrets, database dumps, VPN files, private keys, or tokens.
- Do not expose employee personal data in logs, docs, screenshots, prompts, or final responses.
- Keep authorization checks and company isolation intact.
- Treat session logic as security-sensitive.
- Treat file upload, S3 paths, report exports, and downloads as security-sensitive.
- Prefer existing project security helpers and patterns.

## Payroll Data

The following data is sensitive:

- salary,
- wage types,
- deductions,
- benefits,
- tax data,
- bank accounts,
- government identifiers,
- home addresses,
- personal contact data,
- attendance and time events,
- performance and evaluation records.

## Company Data Isolation

**A user authenticated under Company A must never be able to read, write, or export data belonging to Company B.**
This is a non-negotiable, multi-tenant boundary. Violating it is a Critical finding and a merge blocker.

### The Rule

Every query, API response, report, and export that touches employee, payroll, or configuration data MUST be
scoped to the authenticated company. No exceptions.

### How It Works in Payroll123

The global variable `$company` carries the authenticated company code for the current session.
Payroll123 enforces isolation by requiring `$company` to appear as a filter condition in every
query that reads or writes company-scoped data (e.g. `WHERE company = :company`).

**The AI must:**

- Never remove, comment out, or bypass a `$company` filter in SQL.
- Never substitute a hardcoded company code in place of `$company`.
- Never add a query that returns rows across multiple companies unless the feature explicitly requires
  cross-company aggregation and the request comes with explicit approval.
- Flag any query that joins or subqueries across company boundaries without a clear isolation contract.

### Signs of a Violation

- A SQL query touches a company-scoped table but has no `WHERE company = ...` condition.
- An API response includes records from more than one company for a single-company session.
- A report export contains rows from companies other than the authenticated one.
- A `$company` filter was replaced with a literal value or removed during a refactor.

### Severity

Any finding that exposes or risks exposing cross-company data is classified **Critical**.
Work must not be merged until the isolation is restored and verified.

## Access Control

When touching permissions, menus, pages, APIs, reports, or exports, verify:

- authenticated access,
- company scope,
- role/profile permissions,
- user impersonation or switcher behavior,
- direct URL access,
- export/download access.

## Logging

Logs MUST NOT include:

- credentials,
- full request payloads with personal data,
- raw payroll data,
- bank account details,
- tokens,
- private employee identifiers beyond what is required for debugging.

## Security Review Triggers

Run a security audit when a change touches:

- SQL,
- authentication,
- sessions,
- authorization,
- file paths,
- uploads/downloads,
- API responses,
- report exports,
- employee or payroll data.
