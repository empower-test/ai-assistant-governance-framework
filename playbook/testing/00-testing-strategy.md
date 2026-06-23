# Testing Strategy

Testing depth depends on risk.

## Minimum Validation

For PHP changes:

```bash
php -l path/to/file.php
```

In Docker, validation commonly looks like:

```bash
docker exec empowerhr-dev php -l /var/www/html/dev/path/to/file.php
```

Use the actual container name and path for the local environment.

## Low-Risk Testing

Use:

- syntax validation,
- quick smoke test of affected page or command,
- final review of changed diff.

## Medium-Risk Testing

Use:

- syntax validation,
- affected workflow smoke test,
- before/after comparison when possible,
- company or plugin scope check,
- SQL parameter check when queries changed.

## High-Risk Testing

Use:

- syntax validation,
- focused regression scenarios,
- before/after totals,
- permission and company isolation checks,
- audit report,
- human review before deployment.

## What To Test By Domain

Reports:

- filters,
- row counts,
- totals,
- export format,
- company and date scope.

Payroll:

- affected employee scenarios,
- period boundaries,
- deductions and benefits,
- rounding,
- retroactive cases,
- accounting output if applicable.

APIs:

- request validation,
- authorization,
- response shape,
- error handling,
- data minimization.

UI pages:

- page load,
- grid filters,
- actions,
- permissions,
- company-specific behavior.

## When Tests Cannot Run

State:

- what could not run,
- why,
- what was checked instead,
- what the human should verify.
