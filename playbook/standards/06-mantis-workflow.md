# Mantis Workflow

This workflow applies when the user mentions a Mantis number, such as `Mantis 8140`, `#8140`, or `mantis8140`.

## Before Code Changes

If working inside the Payroll123 repository that uses `.current-mantis`:

1. Write only the numeric Mantis ID to `.current-mantis`.
2. Do this before modifying source files.

Example:

```text
8140
```

## During Code Changes

After each modified file, copy the file to:

```text
mantis/mantis{NUMBER}/
```

Preserve the relative path from `payroll123/`.

Example:

```text
payroll123/plugins/AG/reports/YAGURPTMB1/index.php
```

must be mirrored to:

```text
mantis/mantis8140/plugins/AG/reports/YAGURPTMB1/index.php
```

## After Completion

Clear `.current-mantis` when the task is complete.

## Multi-Item Rule

If the user mentions multiple transactions, reports, or files, the assistant MUST search for all of them and handle each relevant location.

## Final Response

Mention:

- Mantis number,
- files changed,
- Mantis mirror path,
- validation performed.
