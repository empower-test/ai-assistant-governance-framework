# Company Extension Rules

Payroll123 supports company-specific behavior through extensions.
AI assistants MUST respect this precedence.

## Precedence

When a request names a company code, check in this order:

1. `extensions/companies/{COMPANY}/`
2. `plugins/{COUNTRY_CODE}/`
3. base Payroll123 files such as `pg/`, `pgx/`, `api/`, or `classes/`

## Placement Rule

- If the change applies only to one company, implement it in the company extension.
- If the change applies to one country or statutory plugin, implement it in the plugin.
- If the change applies to every company and country, implement it in the base file.

## Base File Guardrail

Do not modify a base file for a company-specific request unless:

- no extension point exists,
- the base behavior is objectively broken for all companies, or
- the human explicitly approves a global change.

Document the reason.

## Overrides

If the extension exists but lacks the required method or property:

- prefer overriding the method or property in the extension,
- prefer a narrow flag or hook over changing global behavior,
- avoid copying large base files unless that is the established local pattern.

## Multi-Transaction Requests

If the request names multiple transactions, reports, or modules, search for and evaluate all of them.
Do not stop after the first match.
