# Regression Checklist

Use this checklist before marking a change complete.

## General

- [ ] Only requested behavior changed.
- [ ] Existing workflow still loads.
- [ ] No unrelated formatting or refactoring.
- [ ] No new notices, warnings, or fatal errors.
- [ ] No secrets or private data exposed.

## Company And Permissions

- [ ] Company-specific behavior remains isolated.
- [ ] Base behavior is unchanged for other companies unless intended.
- [ ] User permissions still apply.
- [ ] Direct URL/API access does not bypass checks.

## Database

- [ ] Queries use prepared statements.
- [ ] Company filters remain intact (`$company` present in every query that reads company-scoped data).
- [ ] No query returns rows from more than one company for a single-company session.
- [ ] Date and payroll period filters remain intact.
- [ ] Joins do not multiply rows unexpectedly.
- [ ] Aggregations still match expected totals.

## Reports

- [ ] Filters work.
- [ ] Totals are correct.
- [ ] Export output is unchanged unless intended.
- [ ] Column order and labels are preserved unless requested.

## Payroll

- [ ] Calculations are unchanged unless explicitly requested.
- [ ] Rounding behavior is unchanged unless explicitly requested.
- [ ] Retroactive, absence, loan, deduction, benefit, and overtime cases were considered when relevant.

## Final Evidence

- [ ] Syntax validation was run or limitation documented.
- [ ] Manual or automated tests are documented.
- [ ] Residual risk is stated.
