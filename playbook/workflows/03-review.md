# Review Workflow

Use this workflow when reviewing AI-generated or human-generated changes.

## Review Priorities

Lead with findings, ordered by severity.
Focus on:

- payroll correctness,
- data privacy,
- authorization,
- company isolation,
- SQL safety,
- PHP 8.4 compatibility,
- regression risk,
- missing tests.

## Finding Format

Each finding SHOULD include:

- severity,
- file and line,
- problem,
- impact,
- suggested fix.

## Severity

- Critical: can expose data, break payroll, corrupt data, or bypass authorization.
- High: likely production regression or incorrect payroll/report output.
- Medium: edge-case regression, incomplete validation, or maintainability risk.
- Low: minor issue with limited impact.

## No-Issue Review

If no issues are found, say so clearly and mention residual risk or test gaps.

## Review Boundaries

Do not treat unrelated legacy code as a finding unless the current change makes it worse or depends on it unsafely.
