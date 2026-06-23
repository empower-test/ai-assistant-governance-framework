# PHP 8.4 Coding Standard

Payroll123 targets PHP 8.4. Code must be compatible with PHP 8.4 while preserving existing behavior.

## Required

- Keep existing project style.
- Use explicit null checks when PHP 8.4 would warn or fail.
- Use `isset()`, `empty()`, `??`, or type checks only where behavior remains consistent.
- Use `mb_*` functions for multibyte strings.
- Validate modified files with `php -l` when possible.
- Prefer minimal compatibility fixes over behavioral rewrites.

## Prohibited

- Do not add `declare(strict_types=1)`.
- Do not add namespaces.
- Do not introduce typed properties or strict method signatures unless existing local code uses them and compatibility is proven.
- Do not silence warnings with broad error suppression.
- Do not replace business logic while fixing PHP 8.4 warnings.

## PHP 8.4 Compatibility Focus

Review for:

- null passed to string functions,
- array access on non-arrays,
- undefined indexes and variables,
- dynamic properties,
- removed or deprecated functions,
- incompatible method signatures,
- assumptions about numeric strings,
- implicit conversion warnings.

## Migration Classification

When auditing migration diffs:

- Mark `KEEP (PHP8)` only when the change prevents PHP 8.4 errors, warnings, or incompatibility.
- Mark `REVERT` when the change introduces business behavior not present in the source version.
- Mark `ADJUST` when the compatibility intent is valid but implementation should be closer to original behavior.
- Mark `NEEDS HUMAN DECISION` when payroll or authorization behavior is unclear.
