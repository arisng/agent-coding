# PRD Guidelines

Comprehensive guidance for creating effective Product Requirements Documents (PRDs) that drive successful software development.

- [1. What Makes a Good PRD Scope?](#1-what-makes-a-good-prd-scope)
  - [1.1. Core Characteristics](#11-core-characteristics)
  - [1.2. Benefits of Small Scopes](#12-benefits-of-small-scopes)
- [2. PRD Scope Checklist](#2-prd-scope-checklist)
- [3. Best Practices for PRD Scoping](#3-best-practices-for-prd-scoping)
  - [3.1. Scope Management](#31-scope-management)
  - [3.2. Maintenance and Review](#32-maintenance-and-review)
  - [3.3. Team Collaboration](#33-team-collaboration)
- [4. PRD Template](#4-prd-template)
  - [4.1. Template Structure](#41-template-structure)
  - [4.2. Template Usage](#42-template-usage)
- [5. Referencing Convention for PRDs](#5-referencing-convention-for-prds)
  - [5.1. Allowed References](#51-allowed-references)
  - [5.2. Prohibited References](#52-prohibited-references)
  - [5.3. Rationale](#53-rationale)
  - [5.4. Example Reference Section](#54-example-reference-section)
- [6. Common PRD Patterns](#6-common-prd-patterns)
  - [6.1. Extending Existing PRDs](#61-extending-existing-prds)
  - [6.2. Breaking Down Large Features](#62-breaking-down-large-features)
  - [6.3. Emergency/Hotfix PRDs](#63-emergencyhotfix-prds)

## 1. What Makes a Good PRD Scope?

A well-scoped PRD (Product Requirements Document) is the foundation for delivering actionable, traceable, and manageable work. The goal is to define a scope that is small enough to be delivered quickly, yet meaningful enough to provide value.

### 1.1. Core Characteristics

- **Actionable:** The scope should be small enough to be completed in a short cycle (ideally days, not weeks).
- **Testable:** The outcome should be verifiable (e.g., via acceptance criteria or test cases).
- **Traceable:** Each PRD should map directly to progress, tasks, and feedback.
- **Independent:** Avoid dependencies that could block progress; split large features into smaller, independent deliverables.
- **Valuable:** Each PRD should deliver a user-facing or technical improvement.

### 1.2. Benefits of Small Scopes

- **Faster Delivery:** Small scopes reduce risk and allow for quicker iteration.
- **Clear Ownership:** Each PRD can be assigned to an individual or small team.
- **Easier Review:** Focused changes are easier to review, test, and validate.
- **Continuous Improvement:** Frequent, small releases enable rapid feedback and learning.

## 2. PRD Scope Checklist

Before finalizing a PRD, ensure you can answer "yes" to the following:

- [ ] Is the scope clearly defined and unambiguous?
- [ ] Can the work be completed in a short cycle (e.g., 1–5 days)?
- [ ] Are acceptance criteria or success metrics specified?
- [ ] Are dependencies and risks identified and minimized?
- [ ] Is the scope small enough to allow for rapid feedback and iteration?
- [ ] Does the PRD address a single feature, enhancement, or fix (not a broad project)?
- [ ] Is the scope clear enough to be broken down into a handful of actionable tasks (ideally 1–5 tasks, to be defined downstream)?
- [ ] Can the PRD be closed independently (not open-ended or perpetually growing)?
- [ ] Can stakeholders review and approve the PRD without ambiguity?

> **Note:** In accordance with the referencing convention, PRDs should only reference other PRDs and the internal progress file (`_progress.md`). Do not reference downstream files such as `task_`, `spec-`, or `issue_` files directly from a PRD. Downstream files will reference the PRD as needed.

## 3. Best Practices for PRD Scoping

### 3.1. Scope Management

- **Start Small:** If a feature is too big, split it into multiple PRDs, each with its own `_prd.md` and progress tracking.
- **Iterate:** Use feedback loops to refine and expand scope in future cycles.
- **Document Out-of-Scope Items:** Clearly state what is not included to avoid ambiguity.
- **Keep It Actionable:** Avoid vague or aspirational language—focus on what will be delivered.

### 3.2. Maintenance and Review

- **Review Regularly:** Revisit open PRDs to ensure they remain relevant and scoped appropriately.
- **Link Related PRDs:** Use references to connect related or dependent PRDs.
- **Version Control:** Update PRDs as requirements evolve, maintaining clear change history.

### 3.3. Team Collaboration

- **Clear Ownership:** Assign each PRD to a specific owner or team.
- **Stakeholder Alignment:** Ensure all stakeholders understand and approve the scope.
- **Communication:** Use PRDs as communication tools to align team understanding.

> **Important:** Follow the referencing convention outlined in the [Referencing Convention](#referencing-convention-for-prds) section when linking files from PRDs.

## 4. PRD Template

A reusable PRD template is available for all new scopes. The template includes:

### 4.1. Template Structure

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
- Link to related PRDs and the internal progress file only.
```

### 4.2. Template Usage

1. **Copy the template** from [prd2prod_template-prd.md](./prd2prod_template-prd.md)
2. **Fill in each section** with specific details for your scope
3. **Assign feature IDs** starting from F001 for functional features, N001 for non-functional
4. **Review against the checklist** before finalizing
5. **Link to progress tracking** in `_progress.md`

## 5. Referencing Convention for PRDs

### 5.1. Allowed References

In the "Related Files" section of a PRD, only reference:

- **Other PRDs** (to show inheritance, extension, or dependencies)
- **The internal progress file** (`_progress.md`)

### 5.2. Prohibited References

Do not reference downstream files directly from a PRD:

- `task_` files
- `spec-` files  
- `issue_` files
- `log_` files

### 5.3. Rationale

This ensures:

- **Clear separation of concerns** between requirements and implementation
- **Upstream-only referencing** maintains clean dependency flow
- **Downstream files reference upstream** files, not vice versa
- **Easier maintenance** when restructuring implementation details

### 5.4. Example Reference Section

```markdown
## Related Files

### Related PRDs
- [Export to Excel PRD](./_prd_export-to-excel.md) - Extended by this PRD
- [User Authentication PRD](./_prd_user-auth.md) - Dependency for secure exports

### Progress Tracking
- [Progress Index](./_progress.md) - See entries F003, F004 for this scope
```

## 6. Common PRD Patterns

### 6.1. Extending Existing PRDs

When building upon existing functionality:

```markdown
## Overview
This PRD extends the existing [Export to Excel PRD](./_prd_export-to-excel.md) 
to provide CSV export capabilities with similar functionality.

## Dependencies
- [Export to Excel PRD](./_prd_export-to-excel.md) must be completed first
- Shared export infrastructure must be available
```

### 6.2. Breaking Down Large Features

When a feature is too large:

```markdown
## Overview
This is Part 1 of the User Dashboard feature, focusing on basic layout and navigation.
See related PRDs for additional dashboard functionality.

## Related Files
- [User Dashboard Part 2 - Widgets](./_prd_dashboard-widgets.md)
- [User Dashboard Part 3 - Customization](./_prd_dashboard-custom.md)
```

### 6.3. Emergency/Hotfix PRDs

For critical fixes:

```markdown
## Overview
Critical security fix for user authentication vulnerability discovered in production.

## Goals
- Patch security vulnerability within 24 hours
- Maintain backward compatibility
- Deploy with minimal downtime

## Functional Features
- F001: Implement input validation for login endpoints
- F002: Add rate limiting to prevent brute force attacks
```

---

**Next Steps:** After creating your PRD, update the progress index and begin following the [linear workflow](./prd2prod_workflow-guide.md) for implementation planning.
