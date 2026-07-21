# Audit Protocol

Audits provide evidence that a change is safe enough to review or release.

## When An Audit Is Required

Audit is required for:

- payroll calculations,
- deductions, benefits, taxes, loans, attendance, overtime, or accounting,
- security or permission changes,
- employee personal data handling,
- SQL changes in high-risk areas,
- PHP version migration diffs,

## Audit Method

1. Identify the original behavior.
2. Identify the proposed or implemented behavior.
3. Compare against Payroll123 standards.
4. Classify each finding.
5. Recommend keep, revert, adjust, or human decision.
6. Record validation evidence.

## Finding Classification

- `KEEP`: change is correct and necessary.
- `KEEP (PHP8)`: change is required for PHP 8.4 compatibility and does not alter business behavior.
- `REVERT`: change is unnecessary, unsafe, or changes behavior outside the request.
- `ADJUST`: change is directionally correct but implementation needs revision.
- `NEEDS HUMAN DECISION`: business, legal, payroll, or security intent is unclear.

## Audit Completeness

For diff audits:

- every diff must be reviewed,
- do not group unrelated diffs,
- preserve code blocks in generated audit documents,
- fill all summary and detail sections,
- verify Markdown or HTML structure remains valid.
