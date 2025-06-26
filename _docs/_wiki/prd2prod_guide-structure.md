# Content Structure

Templates and content formatting guidelines for consistent documentation across the PRD to Production system.

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Content Structure for `_progress` Files](#content-structure-for-_progress-files)
  - [Required Structure](#required-structure)
  - [Example Entry Format](#example-entry-format)
- [Content Structure for `_prd` Files](#content-structure-for-_prd-files)
  - [Required Sections](#required-sections)
  - [Content Guidelines](#content-guidelines)
- [Content Structure for `task_` Files](#content-structure-for-task_-files)
  - [Required Structure](#required-structure-1)
  - [Example Task Structure](#example-task-structure)
- [Content Structure for Specification Files](#content-structure-for-specification-files)
  - [Design Specifications (`spec-design_`)](#design-specifications-spec-design_)
  - [Development Specifications (`spec-dev_`)](#development-specifications-spec-dev_)
- [Content Structure for `issue_` Files](#content-structure-for-issue_-files)
  - [Required Structure](#required-structure-2)
  - [Example Issue Structure](#example-issue-structure)
- [Content Structure for `log_` Files](#content-structure-for-log_-files)
  - [Required Structure](#required-structure-3)
  - [Example Log Structure](#example-log-structure)
- [Recommended Status Values](#recommended-status-values)
  - [Primary Status Values](#primary-status-values)
  - [Extended Status Values (Optional)](#extended-status-values-optional)
  - [Status Usage Guidelines](#status-usage-guidelines)
- [Templates and Examples](#templates-and-examples)
  - [Quick Reference](#quick-reference)
  - [Template Usage](#template-usage)
  - [Quality Checklist](#quality-checklist)

## Content Structure for `_progress` Files

`_progress` files serve as a high-level index and priority guide for functionality and non-functionality scopes outlined in the corresponding `_prd` file. They provide an overview of development priorities and progress, with detailed tasks delegated to `task_` files.

### Required Structure

1. **Title**
   - Format: `# Progress for <Feature/Project Name>`
   - Example: `# Progress for Azure Blob Storage Management`

2. **Introduction**
   - Brief explanation of the purpose of the `_progress` file
   - Example: `This document provides a high-level overview of development priorities and progress, and serves as an index for detailed tasks outlined in the corresponding 'task_' files.`

3. **Priority Sections**
   - **Functionality Scopes:** High-level features or functionalities
   - **Non-Functionality Scopes:** Aspects like performance, security, deployment, or compliance

4. **Task Index**
   - For each scope, list the related information using this format:
     - **Scope Name:** A concise name for the scope
     - **ID:** A unique identifier (e.g., `F001` for functional, `N001` for non-functional)
     - **Priority:** High, Medium, or Low
     - **Status:** Current status (see [Status Values](#recommended-status-values))
     - **Related Files:** Links to the corresponding `task_<ID>_<name>.md` files

### Example Entry Format

```markdown
- **Scope Name:** File Management
  - **ID:** F001
  - **Priority:** High
  - **Status:** In Progress
  - **Related Files:** [task_F001_file-management.md](./task_F001_file-management.md)

- **Scope Name:** System Performance
  - **ID:** N001
  - **Priority:** Medium
  - **Status:** Not Started
  - **Description:** Ensuring the application meets performance benchmarks
```

5. **References**
   - Include a section at the end for any references or related documentation
   - Example:

```markdown
## References
- [_prd.md](./_prd.md)
- [Azure Blob Storage Documentation](https://learn.microsoft.com/en-us/azure/storage/blobs/)
```

## Content Structure for `_prd` Files

PRD files should follow the structure defined in the [PRD Template](./prd2prod-template-prd.md). Key sections include:

### Required Sections

1. **Title:** Clear, descriptive name for the feature/enhancement/fix
2. **Overview:** Brief summary of the scope and its value
3. **Goals:** Specific, measurable objectives
4. **Functional Features:** F001, F002, etc. with descriptions
5. **Non-Functional Features:** N001, N002, etc. with descriptions
6. **Acceptance Criteria:** What must be true for completion
7. **Out of Scope:** What is explicitly excluded
8. **Dependencies:** Prerequisites or related work
9. **Related Files:** Links to other PRDs and progress file only

### Content Guidelines

- **Be Specific:** Avoid vague language, focus on deliverables
- **Be Concise:** Each PRD should be readable in 5-10 minutes
- **Be Actionable:** Every requirement should be implementable
- **Be Testable:** Include measurable acceptance criteria

## Content Structure for `task_` Files

Task files break down PRD features into actionable work items.

### Required Structure

1. **Title:** `# Task <ID>: <Feature Name>`
2. **Overview:** Brief description linking back to PRD
3. **Objectives:** Specific goals for this task
4. **Task Breakdown:** Numbered list of specific actions
5. **Acceptance Criteria:** How to verify completion
6. **Dependencies:** What must be completed first
7. **Estimated Effort:** Time estimate (hours/days)
8. **Status:** Current progress status
9. **Notes:** Additional context or decisions
10. **Related Files:** Links to PRD, progress, and spec files

### Example Task Structure

```markdown
# Task F001: User Authentication System

## Overview
Implement basic user authentication system as defined in [_prd_user-auth.md](./_prd_user-auth.md).

## Objectives
- Secure user login/logout functionality
- Session management
- Password reset capability

## Task Breakdown
1. Design database schema for user accounts
2. Implement login endpoint
3. Implement logout endpoint
4. Add session management middleware
5. Create password reset flow
6. Add input validation and security measures
7. Write unit tests
8. Update documentation

## Acceptance Criteria
- [ ] Users can register with email and password
- [ ] Users can log in with valid credentials
- [ ] Users can log out and sessions are cleared
- [ ] Password reset emails are sent successfully
- [ ] All security requirements from PRD are met

## Dependencies
- Database setup must be completed
- Email service must be configured

## Estimated Effort
3-4 days

## Status
In Progress

## Notes
- Using JWT tokens for session management
- Password requirements: 8+ chars, mixed case, numbers

## Related Files
- [_prd_user-auth.md](./_prd_user-auth.md)
- [_progress.md](./_progress.md) - Entry F001
- [spec-design_F001_auth-flow.md](./spec-design_F001_auth-flow.md)
```

## Content Structure for Specification Files

### Design Specifications (`spec-design_`)

Focus on conceptual knowledge and design rationale:

1. **Purpose and Scope:** What this spec covers
2. **Architecture Overview:** High-level system design
3. **Design Decisions:** Rationale for key choices
4. **Diagrams:** UML, flowcharts, sequence diagrams
5. **Pseudocode:** High-level algorithm descriptions
6. **Constraints:** Technical and business constraints
7. **Assumptions:** What we're assuming to be true
8. **Future Considerations:** Extensibility and scalability

### Development Specifications (`spec-dev_`)

Focus on implementation details:

1. **Purpose and Scope:** Brief description of what the specification covers
2. **Technical Requirements:** Specific technical constraints and requirements
3. **API Contracts:** Endpoint definitions, request/response formats
4. **Implementation Details:** Step-by-step implementation guidance
5. **Code Examples:** Relevant code samples and snippets
6. **Configuration:** Required configuration settings
7. **Testing Considerations:** Testing approach and requirements
8. **Dependencies:** External dependencies and prerequisites

## Content Structure for `issue_` Files

Issue files document problems and their resolution:

### Required Structure

1. **Title:** `# Issue: <Brief Description>`
2. **Summary:** Quick overview of the problem
3. **Description:** Detailed problem description
4. **Impact:** Who/what is affected
5. **Steps to Reproduce:** How to recreate the issue
6. **Expected Behavior:** What should happen
7. **Actual Behavior:** What actually happens
8. **Environment:** System details where issue occurs
9. **Logs/Screenshots:** Supporting evidence
10. **Proposed Solution:** How to fix it
11. **Status:** Current state of resolution
12. **Related Files:** Links to tasks, PRDs, or other issues

### Example Issue Structure

```markdown
# Issue: Login Timeout After 5 Minutes

## Summary
Users are being logged out automatically after 5 minutes of inactivity, which is too short for typical usage patterns.

## Description
The current session timeout is set to 5 minutes, causing frequent logouts during normal application use. Users report frustration with having to re-authenticate multiple times per session.

## Impact
- All active users
- Reduced user experience
- Increased support requests

## Steps to Reproduce
1. Log into the application
2. Leave the application idle for 5 minutes
3. Try to perform any action
4. Observe automatic logout

## Expected Behavior
Session should remain active for at least 30 minutes of inactivity for standard users.

## Actual Behavior
Session expires after exactly 5 minutes of inactivity.

## Environment
- Production environment
- All user types affected
- Occurring since deployment v2.1.0

## Proposed Solution
1. Increase default session timeout to 30 minutes
2. Add configurable timeout settings
3. Implement "remember me" option for extended sessions

## Status
Identified - pending task creation

## Related Files
- [task_F001_user-auth.md](./task_F001_user-auth.md)
- [_progress.md](./_progress.md)
```

## Content Structure for `log_` Files

Daily log files track progress and decisions:

### Required Structure

1. **Title:** `# Daily Log - <Date>`
2. **Summary:** Brief overview of the day's work
3. **Completed Tasks:** What was finished
4. **In Progress:** What is currently being worked on
5. **Blocked Items:** What is preventing progress
6. **Decisions Made:** Important choices or changes
7. **Next Steps:** What to focus on next
8. **Notes:** Additional context or observations

### Example Log Structure

```markdown
# Daily Log - June 26, 2025

## Summary
Focused on user authentication implementation and resolved session timeout issue.

## Completed Tasks
- Implemented login endpoint with JWT token generation
- Added input validation for user registration
- Fixed session timeout configuration (increased to 30 minutes)
- Updated unit tests for authentication module

## In Progress
- Password reset email functionality (60% complete)
- Session management middleware integration

## Blocked Items
- Email service configuration pending DevOps team
- Database migration requires approval

## Decisions Made
- Using JWT tokens instead of server-side sessions for better scalability
- Password requirements: minimum 8 characters, mixed case, numbers
- Session timeout set to 30 minutes for standard users

## Next Steps
- Complete password reset implementation once email service is ready
- Begin logout endpoint implementation
- Schedule code review with team

## Notes
- Found useful JWT library that simplifies token management
- Need to discuss rate limiting for login attempts in next team meeting
```

## Recommended Status Values

To ensure consistency and clarity across all files, use these standardized status values:

### Primary Status Values

- **Not Started:** Work has not begun on this scope or task
- **In Progress:** Work is actively being done
- **Blocked:** Progress is halted due to a dependency, issue, or external factor
- **Review:** Work is complete and under review (e.g., code review, QA)
- **Done:** Work is fully completed and accepted
- **Deferred:** Work is intentionally postponed for future consideration

### Extended Status Values (Optional)

- **Planning:** Requirements gathering and planning phase
- **Design:** Design and architecture phase
- **Development:** Active coding/implementation
- **Testing:** Testing and quality assurance
- **Deployment:** Deployment and production setup
- **Monitoring:** Post-deployment monitoring and observation

### Status Usage Guidelines

- **Be Consistent:** Use the same status values across all files
- **Be Current:** Update status regularly as work progresses
- **Be Clear:** Status should immediately indicate current state
- **Be Specific:** Use extended values when more granularity is helpful

## Templates and Examples

### Quick Reference

| File Type | Template Location | Example Location |
|-----------|------------------|------------------|
| PRD | [prd2prod-template-prd.md](./prd2prod-template-prd.md) | [prd2prod-example-csv-export.md](./prd2prod-example-csv-export.md) |
| Progress | [prd2prod-template-progress.md](./prd2prod_template-progress.md) | Various project examples |
| Task | [prd2prod-template-task.md](./prd2prod_template-task.md) | Task files in project root |
| Design Spec | [prd2prod-template-spec-design.md](./prd2prod_template-spec-design.md) | Spec files in project root |
| Dev Spec | [prd2prod-template-spec-dev.md](./prd2prod_template-spec-dev.md) | Spec files in project root |
| Issue | [prd2prod-template-issue.md](./prd2prod_template-issue.md) | Issue files in project root |
| Log | [prd2prod-template-log.md](./prd2prod_template-log.md) | Daily log files |

### Template Usage

1. **Copy Template:** Start with the appropriate template
2. **Fill Sections:** Complete all required sections
3. **Follow Guidelines:** Apply content structure rules
4. **Review Checklist:** Ensure all requirements are met
5. **Link Appropriately:** Connect to related files correctly

### Quality Checklist

Before finalizing any document:

- [ ] Title is clear and descriptive
- [ ] All required sections are present
- [ ] Content is specific and actionable
- [ ] Links to related files are correct
- [ ] Status is current and accurate
- [ ] Formatting follows conventions
- [ ] Grammar and spelling are correct

---

This content structure ensures consistency, clarity, and maintainability across all project documentation while supporting effective project management and team collaboration.
