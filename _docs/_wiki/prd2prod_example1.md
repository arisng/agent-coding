# Example: Real-Life End-to-End Workflow (Export to CSV)

- [1. Create the PRD](#1-create-the-prd)
- [2. Index in Progress](#2-index-in-progress)
- [3. Design and Development Specifications](#3-design-and-development-specifications)
- [4. Break Down into Tasks](#4-break-down-into-tasks)
- [5. Track Issues and Daily Progress](#5-track-issues-and-daily-progress)
- [6. Testing and Release](#6-testing-and-release)
- [7. Feedback Loop](#7-feedback-loop)

This example demonstrates how to follow the linear workflow, starting with a realistic PRD that identifies both functional and non-functional features (IDs starting from 001), references another PRD for extension, and prioritizes execution in `_progress.md`.

## 1. Create the PRD

Draft `_prd_export-to-csv.md` using the template. Identify functional and non-functional features, assign IDs starting from 001, and reference another PRD to show inheritance/extension. Only reference other PRDs and the internal progress file:

```markdown
# Export to CSV PRD

## Overview
Enable users to export dashboard data to CSV format for reporting and analysis. This PRD extends the existing [Export to Excel PRD](./_prd_export-to-excel.md) to provide CSV support.

## Functional Features
- **F001**: Export current dashboard data to CSV (core functionality)
- **F002**: Export filtered data to CSV

## Non-Functional Features
- **N001**: Ensure export completes within 5 seconds for up to 10,000 records
- **N002**: Log all export actions for audit purposes

## Acceptance Criteria
- User can export current or filtered data as a CSV file
- Export completes within performance targets
- All export actions are logged

## Out of Scope
- Scheduled/automated exports
- Exporting charts or images

## Dependencies
- None for initial version

## Related Files
- [Reference: _prd_export-to-excel.md](./_prd_export-to-excel.md)
- [Reference: _progress.md](./_progress.md)
```

## 2. Index in Progress

Add entries for each feature in `_progress.md`, prioritizing execution order and using IDs starting from 001:

```markdown
- **Scope Name:** Export to CSV
  - **ID:** F001
  - **Priority:** High
  - **Status:** In Progress
  - **Related Files:** [task_F001_export-to-csv.md](./task_F001_export-to-csv.md)

- **Scope Name:** Export Filtered Data
  - **ID:** F002
  - **Priority:** Medium
  - **Status:** Not Started
  - **Related Files:** [task_F002_export-filtered-csv.md](./task_F002_export-filtered-csv.md)

- **Scope Name:** Export Performance
  - **ID:** N001
  - **Priority:** High
  - **Status:** Not Started
  - **Related Files:** [task_N001_export-performance.md](./task_N001_export-performance.md)

- **Scope Name:** Export Logging
  - **ID:** N002
  - **Priority:** Medium
  - **Status:** Not Started
  - **Related Files:** [task_N002_export-logging.md](./task_N002_export-logging.md)
```

## 3. Design and Development Specifications

- Create `spec-design_F001_export-to-csv.md` for conceptual design, diagrams, and rationale.
- Create `spec-dev_F001_export-to-csv-handler.md` for API contracts and implementation details.
- Repeat for other features as needed.

## 4. Break Down into Tasks

Create a `task_` file for each feature, outlining actionable steps and linking to the PRD and `_progress.md`.

## 5. Track Issues and Daily Progress

- Log blockers or bugs in `issue_` files (e.g., `issue_export-csv-performance.md`).
- Record daily progress in `log_YYMMDD.md`.
- Update statuses in `_progress.md` and task files.

## 6. Testing and Release

- Test and review each feature as it is completed.
- Mark as "Done" in `_progress.md` and task files.
- Deploy to production.

## 7. Feedback Loop

- Monitor for user or production feedback.
- Capture new issues or improvement ideas as `issue_` files.
- Feed these back into the workflow for future cycles.

This approach ensures every step is traceable, actionable, and prioritized, starting from a well-structured PRD and flowing through all downstream documentation and feedback steps. It also demonstrates how new PRDs can extend or inherit from existing ones.
