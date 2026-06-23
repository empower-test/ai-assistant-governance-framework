# Payroll123 Claude Code Context

Claude MUST follow this framework when working on Payroll123.
This file is the Claude-specific entry point. The rules also apply to Codex through `AGENTS.md`.

## Read First

Before touching code, read:

1. `README.md`
2. `AGENTS.md`
3. `playbook/standards/00-project-context.md`
4. `playbook/governance/00-operating-model.md`

For code changes, also read the standards under `playbook/standards/` and the relevant workflow under `playbook/workflows/`.

## Project Summary

Payroll123 is an enterprise HRMS and payroll platform built on PHP 8.4.
The local Docker environment is intended to mirror production PHP behavior.

## Code Location

The Payroll123 source code is located in the `payroll123/` subdirectory of this framework root.
All file reads, edits, and searches for Payroll123 code MUST target `payroll123/` and its subdirectories.
If `payroll123/` is empty or missing, ask the developer to clone Payroll123 there before proceeding.

Typical application structure relative to this framework root:

```text
payroll123/
|-- api/       REST endpoints and addons
|-- classes/   OOP classes, one class per file, usually extending CORE
|-- cli/       command-line scripts
|-- cron/      scheduled jobs
|-- krnl/      core configuration and helper functions
|-- pg/        UI pages based on processGrid()
|-- pgx/       extended page components and reports
|-- plugins/   country and feature plugins
|-- extensions/
|   └── companies/   company-specific overrides
```

## Required Agent Flow

For non-trivial code work, use this mental agent sequence even if separate Claude subagents are unavailable:

1. Architect: identify scope, files, risks, and implementation plan.
2. Developer: make the smallest safe change using existing patterns.
3. QA: validate behavior, syntax, and regression impact.
4. Auditor: check PHP 8.4, security, privacy, and payroll-data implications.

For one-line fixes, the flow may be compressed, but QA and audit thinking still apply.

## Critical Rules

- Use Payroll123 architecture over generic framework patterns.
- Company-specific changes go in `extensions/companies/{COMPANY}/` when applicable.
- Country-level changes go in `plugins/{COUNTRY_CODE}/` only when broader than one company.
- Base files are changed only when the fix applies globally.
- SQL must use PDO prepared statements.
- Do not pass global variables such as `$company`, `$lang`, or `$userid` into new APIs when the local pattern expects globals.
- Do not sanitize identifiers or paths with new regex rules unless the requirement explicitly asks for it or security review proves it is necessary.
- Do not change payroll formulas, approval rules, permissions, or report totals without explicit requirements and regression evidence.

## Validation Expectations

At minimum, run PHP syntax validation for modified PHP files when the environment allows it.
For risky changes, add focused manual or automated checks described in `playbook/testing/00-testing-strategy.md`.

## Final Response Expectations

When reporting back, include:

- what changed,
- files modified,
- validation performed,
- risks or assumptions.

Keep the response concise and factual.
