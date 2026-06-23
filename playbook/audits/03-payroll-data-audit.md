# Payroll Data Audit

Use this audit for changes affecting payroll or HR data correctness.

## Sensitive Domains

- payroll runs,
- wage types,
- salary,
- overtime,
- deductions,
- benefits,
- taxes,
- loans and balances,
- absences,
- attendance and time events,
- accounting exports,
- employee identity and banking data.

## Audit Questions

- What data is read?
- What data is written?
- Which company or companies are affected?
- Which payroll periods are affected?
- Which employee scenarios are affected?
- Are totals, rounding, or filters changed?
- Are statutory or country-specific rules involved?
- Can the change affect historical payroll?

## Required Checks

- [ ] Existing formula or rule was identified.
- [ ] Requested formula or rule was identified.
- [ ] Before/after behavior is documented.
- [ ] Company isolation is confirmed.
- [ ] Date and payroll period boundaries are confirmed.
- [ ] Totals and subtotals are checked when reports are involved.
- [ ] No private employee data appears in documentation or response.

## Decision

Use one:

- `KEEP`
- `REVERT`
- `ADJUST`
- `NEEDS HUMAN DECISION`

Explain the reason and required validation.
