# Security Audit

Use this audit when changes touch access, data, SQL, files, sessions, APIs, or exports.

## Scope

Record:

- files reviewed,
- entry points,
- authenticated user assumptions,
- company scope,
- data types exposed,
- write operations,
- external integrations.

## Checklist

- [ ] Authentication is required where expected.
- [ ] Authorization and profile checks are preserved.
- [ ] Company isolation is enforced: every query, API response, and export scoped to `$company` — no cross-company data leaks.
- [ ] SQL uses prepared statements.
- [ ] User input is validated according to existing project patterns.
- [ ] File paths cannot escape intended storage.
- [ ] Upload/download behavior does not expose unauthorized files.
- [ ] API responses expose only required data.
- [ ] Logs do not include secrets or private employee data.
- [ ] Errors do not reveal sensitive internals.

## Findings

Classify each finding:

- Critical: data exposure, privilege bypass, credential leak, destructive write.
- High: likely unauthorized access or cross-company data leak.
- Medium: exploitable under specific conditions.
- Low: hardening or evidence gap.

## Required Output

- Findings:
- Recommended fixes:
- Validation:
- Residual risk:
