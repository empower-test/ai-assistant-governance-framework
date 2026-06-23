# PHP 8.4 Compatibility Checklist

Use this checklist for code changes and migration audits.

## Runtime Checks

- [ ] Modified PHP files pass `php -l`.
- [ ] No new `declare(strict_types=1)` was added.
- [ ] No namespaces were introduced.
- [ ] No incompatible method signatures were introduced.

## Common PHP 8.4 Issues

- [ ] Null is not passed to string functions without intentional handling.
- [ ] Array offsets are accessed only on arrays or guarded values.
- [ ] Undefined variables and indexes are handled without changing business logic.
- [ ] Dynamic property use is avoided or confirmed as safe in local pattern.
- [ ] Deprecated or removed functions are replaced.
- [ ] Numeric string assumptions are reviewed.
- [ ] Multibyte strings use `mb_*`.

## Migration Diff Classification

- [ ] Compatibility-only changes are marked `KEEP (PHP8)`.
- [ ] Functional changes not required for PHP 8.4 are marked `REVERT`.
- [ ] Valid compatibility intent with unsafe implementation is marked `ADJUST`.
- [ ] Ambiguous payroll/security behavior is marked `NEEDS HUMAN DECISION`.

## Evidence

- Syntax command:
- Files checked:
- Compatibility findings:
- Residual risk:
