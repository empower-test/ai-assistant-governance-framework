# PHP 8.4 Compatibility Audit

Use this audit for PHP 8.4 migration work and compatibility reviews.

## Keep As PHP 8.4 Compatibility

Mark `KEEP (PHP8)` only for changes that prevent PHP 8.4 errors, warnings, or incompatibilities, such as:

- null handling before string operations,
- array checks before offset access,
- replacement of removed or deprecated functions,
- compatible method signatures,
- explicit initialization of previously undefined variables,
- safe handling of nullable values.

## Revert As Functional Regression

Mark `REVERT` for changes that are not strictly required for PHP 8.4, such as:

- new business validations,
- extra function parameters,
- changed `processGrid()` behavior,
- changed labels, visibility, alignment, or UI defaults,
- changed SQL filters, joins, fields, or grouping,
- changed payroll formulas or report totals,
- new permission behavior.

## Adjust

Mark `ADJUST` when:

- the compatibility issue is real,
- but the implementation changes behavior too broadly,
- or the fix should be closer to the original logic.

## Required Evidence

For every finding, include:

- diff ID or file/line,
- classification,
- reason,
- recommended action,
- expected behavior after action.

## Standard Reasons

Use clear reasons such as:

- Prevents undefined variable warning in PHP 8.4.
- Prevents array offset access on a non-array value.
- Replaces a deprecated or removed PHP function.
- Functional change not present in the original production behavior.
- Additional SQL filter changes report output.
- Additional function argument is not required by original logic.
