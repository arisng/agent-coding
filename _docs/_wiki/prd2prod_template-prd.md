# PRD Template

- [1. Template](#1-template)
- [2. Example: Real-Life PRD (Export to CSV)](#2-example-real-life-prd-export-to-csv)
- [3. Example: Real-Life Workflow in Action (Export to CSV)](#3-example-real-life-workflow-in-action-export-to-csv)

## 1. Template

Use this template as a starting point for every new `_prd.md` file. It is designed for small, actionable, and traceable scopes.

```markdown
# <Feature/Enhancement/Fix Name>

## Overview
- Brief summary of the feature, enhancement, or fix and its value.

## Goals
- List specific, measurable objectives for this scope.

## Functional Features
- F001: <Describe the first functional feature>
- F002: <Describe the second functional feature>

## Non-Functional Features
- N001: <Describe the first non-functional requirement>
- N002: <Describe the second non-functional requirement>

## Acceptance Criteria
- Bullet points describing what must be true for this PRD to be considered complete.

## Out of Scope
- (Optional) Explicitly state what is not included in this scope.

## Dependencies
- (Optional) List any dependencies, prerequisites, or related projects.

## Related Files
- Link to related `task_`, `issue_`, or other documentation files.
```

---

## 2. Example: Real-Life PRD (Export to CSV)

Below is a concrete example of a filled PRD using this template:

```markdown
# Export to CSV PRD

## Overview
Enable users to export their data to CSV format from the dashboard.

## Goals
- Allow export of current dashboard data as a CSV file.

## Functional Features
- F001: Implement export button on the dashboard.
- F002: Generate CSV file from current data.

## Non-Functional Features
- N001: Ensure CSV file is correctly formatted.
- N002: CSV export process should not exceed 2 minutes for 10,000 rows.

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

## 3. Example: Real-Life Workflow in Action (Export to CSV)

See [prd2prod_example1.md](./prd2prod_example1.md) for a complete, end-to-end real-life workflow example following the mental model.

This approach ensures every step is traceable, actionable, and prioritized, starting from a well-structured PRD and flowing through all downstream documentation and feedback steps. It also demonstrates how new PRDs can extend or inherit from existing ones.
