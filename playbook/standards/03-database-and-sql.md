# Database And SQL Standard

Database work in Payroll123 is high-risk when it touches payroll, employee, security, or company data.

## Required SQL Rules

- SQL MUST use PDO prepared statements for variable input.
- Do not concatenate user, request, session, company, date, employee, or payroll values into SQL.
- Preserve existing query semantics unless the request explicitly requires a change.
- Keep company isolation conditions intact.
- Keep permission filters intact.
- Validate report totals after query changes.

## Query Change Review

Before changing SQL, identify:

- source tables,
- join conditions,
- company filters,
- employee filters,
- date or payroll period filters,
- permission filters,
- aggregation logic,
- expected result shape.

## Prohibited Without Approval

- schema changes,
- bulk updates,
- destructive deletes,
- payroll run mutations,
- permission table changes,
- employee compensation updates,
- changes to accounting export logic.

## Reports

For report queries, verify:

- row count expectations,
- totals and subtotals,
- filters,
- date ranges,
- company and country behavior,
- exported column names and order where relevant.

## Data Privacy

Never include real employee personal data, bank information, salaries, government identifiers, or credentials in documentation, examples, prompts, commits, or final responses.
