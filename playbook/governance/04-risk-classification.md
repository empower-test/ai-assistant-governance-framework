# Risk Classification

Classify each request before implementation.

## Low Risk

Examples:

- typo in label or documentation,
- narrow display-only change,
- local syntax compatibility fix with no behavior change,
- adding missing null checks where output is unchanged.

Required evidence:

- file inspection,
- syntax validation when PHP is touched,
- short final summary.

## Medium Risk

Examples:

- report query change,
- form validation change,
- company extension override,
- API response shape change,
- session-dependent behavior,
- UI behavior that affects workflow.

Required evidence:

- implementation plan,
- focused regression checks,
- syntax validation,
- risk notes.

## High Risk

Examples:

- payroll calculations,
- deductions, loans, taxes, overtime, benefits, or severance,
- permissions and access control,
- employee personal data,
- database writes or migrations,
- production deployment,
- changes affecting all companies or countries.

Required evidence:

- explicit scope and assumptions,
- before/after behavior,
- test report,
- audit report,
- human approval before production deployment.

## Automatic Escalation

Escalate to high risk when:

- the assistant cannot determine whether a change affects payroll totals,
- a query touches employee compensation or identity data,
- a base file is changed while the request names a specific company,
- validation cannot be run for a change that affects payroll or security.
