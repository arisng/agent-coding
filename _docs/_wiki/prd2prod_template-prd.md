# PRD Template

Use this template as a starting point for every new `_prd.md` file. It is designed for small, actionable, and traceable scopes.

```markdown
# <Feature/Enhancement/Fix Name>

## Overview
- Brief summary of the scope and its value.

## Goals
- List of specific, measurable objectives.

## Scope
- What is included?
- What is explicitly excluded?

## Acceptance Criteria
- Bullet points describing what must be true for this PRD to be considered complete.

## Out of Scope
- (Optional) Explicitly state what is not included.

## Dependencies
- (Optional) List any dependencies or prerequisites.

## Related Files
- Link to related `task_`, `issue_`, or other documentation files.
```

---

## Example: Real-Life PRD (Export to CSV)

Below is a concrete example of a filled PRD using this template:

```markdown
# Export to CSV PRD

## Overview
Enable users to export their data to CSV format from the dashboard.

## Goals
- Allow export of current dashboard data as a CSV file.

## Scope
- Include: Export button, CSV generation, download link.
- Exclude: Advanced formatting, scheduled exports.

## Acceptance Criteria
- User can click 'Export' and receive a CSV file with current data.
- File matches displayed data and is correctly formatted.

## Out of Scope
- Scheduled/automated exports
- Exporting charts or images

## Dependencies
- None for initial version.

## Related Files
- [task_F003_export-to-csv.md](./task_F003_export-to-csv.md)
- [spec-design_F003_export-to-csv.md](./spec-design_F003_export-to-csv.md)
```

---

## Example: Real-Life Workflow in Action (Export to CSV)

See [prd2prod_example1.md](./prd2prod_example1.md) for a complete, end-to-end real-life workflow example following the mental model.

This approach ensures every step is traceable, actionable, and prioritized, starting from a well-structured PRD and flowing through all downstream documentation and feedback steps. It also demonstrates how new PRDs can extend or inherit from existing ones.
