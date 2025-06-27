# Content Structure

Templates and content formatting guidelines for consistent documentation across the PRD to Production system.

- [1. Content Structure for `_progress` Files](#1-content-structure-for-_progress-files)
  - [1.1. Required Structure](#11-required-structure)
  - [1.2. Enhanced Entry Format with Visual Indicators](#12-enhanced-entry-format-with-visual-indicators)
  - [1.3. Template Reference](#13-template-reference)
  - [1.4. References Section Format](#14-references-section-format)
- [2. Content Structure for `_prd` Files](#2-content-structure-for-_prd-files)
  - [2.1. Required Sections](#21-required-sections)
  - [2.2. Content Guidelines](#22-content-guidelines)
- [3. Content Structure for `task_` Files](#3-content-structure-for-task_-files)
  - [3.1. Required Structure](#31-required-structure)
  - [3.2. Example Task Structure](#32-example-task-structure)
- [4. Content Structure for Specification Files](#4-content-structure-for-specification-files)
  - [4.1. Design Specifications (`spec-design_`)](#41-design-specifications-spec-design_)
  - [4.2. Development Specifications (`spec-dev_`)](#42-development-specifications-spec-dev_)
- [5. Content Structure for `issue_` Files](#5-content-structure-for-issue_-files)
  - [5.1. Required Structure](#51-required-structure)
  - [5.2. Example Issue Structure](#52-example-issue-structure)
- [6. Content Structure for `log_` Files](#6-content-structure-for-log_-files)
  - [6.1. Required Structure](#61-required-structure)
  - [6.2. Example Log Structure](#62-example-log-structure)
- [7. Recommended Status Values](#7-recommended-status-values)
  - [7.1. Primary Status Values](#71-primary-status-values)
  - [7.2. Extended Status Values (Optional)](#72-extended-status-values-optional)
  - [7.3. Status Usage Guidelines](#73-status-usage-guidelines)
- [8. Templates and Examples](#8-templates-and-examples)
  - [8.1. Quick Reference](#81-quick-reference)
  - [8.2. Template Usage](#82-template-usage)
  - [8.3. Quality Checklist](#83-quality-checklist)

## 1. Content Structure for `_progress` Files

`_progress` files serve as a high-level index and priority guide for functionality and non-functionality scopes outlined in the corresponding `_prd` file. They provide an overview of development priorities and progress, with detailed tasks delegated to `task_` files.

**Visual Design Principles:**

- Use clear status indicators (✅ ⏳ 🔴 ⚠️ 📋 ⏸️) for quick scanning
- Group items by status for easy identification of current work
- Include progress percentages and completion estimates
- Use consistent formatting for rapid information processing

### 1.1. Required Structure

1. **Title**
   - Format: `# Progress for <Feature/Project Name>`
   - Example: `# Progress for Azure Blob Storage Management`

2. **Current Focus Dashboard**
   - High-level statistics and current objective focus
   - Visual progress indicators and key metrics
   - Current work-in-progress (WIP) highlights
   - Flexible time period support (daily, weekly, or custom cycles)

3. **Status-Organized Sections**
   - Group by status (In Progress → Blocked → Under Review → Ready to Start → Completed → Deferred)
   - Include both functional and non-functional scopes within each status group
   - Use visual indicators for immediate recognition

4. **Current Focus Period**
   - What's actively being worked on right now
   - Immediate blockers and dependencies
   - Next priorities
   - Adaptable to any workflow cadence

5. **References**
   - Links to related documentation and PRD files

### 1.2. Enhanced Entry Format with Visual Indicators

Each scope entry should include:

- **Status Icon:** Visual indicator (✅ ⏳ 🔴 ⚠️ 📋 ⏸️)
- **Scope Name:** Clear, descriptive name
- **ID:** Unique identifier (F001, N001, etc.)
- **Priority:** High/Medium/Low with visual emphasis
- **Progress:** Completion percentage and current status
- **Estimate:** Expected timeline or remaining effort
- **Description:** Brief scope description
- **Related Files:** Links to task and specification files

**Status Icons Legend:**

- ✅ **Done:** Completed and verified
- ⏳ **In Progress:** Currently being worked on
- 🔴 **Blocked:** Cannot proceed due to dependencies
- ⚠️ **Review:** Completed but under review
- 📋 **Not Started:** Ready to begin
- ⏸️ **Deferred:** Postponed for future consideration

**Priority Visual Indicators:**

- 🔥 **High Priority**
- 🟡 **Medium Priority**
- 🔵 **Low Priority**

### 1.3. Template Reference

For a complete, ready-to-use template implementing these enhanced visual indicators and flexible time-period structure, see:

**[Progress Template](./prd2prod_template-progress.md)** - Copy-paste ready template with:

- Current Focus dashboard (adaptable to any time period)
- Status-organized sections with visual indicators
- Enhanced entry format with progress tracking
- Built-in legend and usage instructions
- Flexible workflow support (daily, weekly, or custom cycles)

The template demonstrates the visual scanning principles and provides placeholder content that can be quickly customized for any project or workflow methodology.

### 1.4. References Section Format

```markdown
## References
- [_prd.md](./_prd.md)
- [Related Documentation Link](./link-to-documentation.md)
```

## 2. Content Structure for `_prd` Files

PRD files should follow the structure defined in the [PRD Template](./prd2prod-template-prd.md). Key sections include:

### 2.1. Required Sections

1. **Title:** Clear, descriptive name for the feature/enhancement/fix
2. **Overview:** Brief summary of the scope and its value
3. **Goals:** Specific, measurable objectives
4. **Functional Features:** F001, F002, etc. with descriptions
5. **Non-Functional Features:** N001, N002, etc. with descriptions
6. **Acceptance Criteria:** What must be true for completion
7. **Out of Scope:** What is explicitly excluded
8. **Dependencies:** Prerequisites or related work
9. **Related Files:** Links to other PRDs and progress file only

### 2.2. Content Guidelines

- **Be Specific:** Avoid vague language, focus on deliverables
- **Be Concise:** Each PRD should be readable in 5-10 minutes
- **Be Actionable:** Every requirement should be implementable
- **Be Testable:** Include measurable acceptance criteria

## 3. Content Structure for `task_` Files

Task files break down PRD features into actionable work items.

### 3.1. Required Structure

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

### 3.2. Example Task Structure

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

## 4. Content Structure for Specification Files

### 4.1. Design Specifications (`spec-design_`)

Focus on conceptual knowledge and design rationale:

1. **Purpose and Scope:** What this spec covers
2. **Architecture Overview:** High-level system design
3. **Design Decisions:** Rationale for key choices
4. **Diagrams:** UML, flowcharts, sequence diagrams
5. **Pseudocode:** High-level algorithm descriptions
6. **Constraints:** Technical and business constraints
7. **Assumptions:** What we're assuming to be true
8. **Future Considerations:** Extensibility and scalability

### 4.2. Development Specifications (`spec-dev_`)

Focus on implementation details:

1. **Purpose and Scope:** Brief description of what the specification covers
2. **Technical Requirements:** Specific technical constraints and requirements
3. **API Contracts:** Endpoint definitions, request/response formats
4. **Implementation Details:** Step-by-step implementation guidance
5. **Code Examples:** Relevant code samples and snippets
6. **Configuration:** Required configuration settings
7. **Testing Considerations:** Testing approach and requirements
8. **Dependencies:** External dependencies and prerequisites

## 5. Content Structure for `issue_` Files

Issue files document problems and their resolution:

### 5.1. Required Structure

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

### 5.2. Example Issue Structure

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

## 6. Content Structure for `log_` Files

Daily log files provide quick progress snapshots with minimal cognitive overhead:

### 6.1. Required Structure

1. **Title:** `# Log [Date]`
2. **Done:** Completed work (bullet points)
3. **Working:** Current focus areas with status
4. **Blocked:** Impediments requiring action
5. **Next:** Tomorrow's priorities
6. **Notes:** Key decisions, discoveries, or observations

### 6.2. Example Log Structure

```markdown
# Log 2025-06-26

## Done
- Implemented login endpoint with JWT tokens
- Fixed session timeout (now 30 minutes)
- Updated auth unit tests

## Working
- Password reset flow (60% - waiting on email service)
- Session middleware integration (started today)

## Blocked
- Email config pending DevOps
- DB migration needs approval

## Next
- Complete logout endpoint
- Code review with team
- Start rate limiting research

## Notes
- Decision: JWT over server sessions for scalability
- Found good JWT library: [link]
- Password policy: 8+ chars, mixed case, numbers
```

## 7. Recommended Status Values

To ensure consistency and clarity across all files, use these standardized status values:

### 7.1. Primary Status Values

- **Not Started:** Work has not begun on this scope or task
- **In Progress:** Work is actively being done
- **Blocked:** Progress is halted due to a dependency, issue, or external factor
- **Review:** Work is complete and under review (e.g., code review, QA)
- **Done:** Work is fully completed and accepted
- **Deferred:** Work is intentionally postponed for future consideration

### 7.2. Extended Status Values (Optional)

- **Planning:** Requirements gathering and planning phase
- **Design:** Design and architecture phase
- **Development:** Active coding/implementation
- **Testing:** Testing and quality assurance
- **Deployment:** Deployment and production setup
- **Monitoring:** Post-deployment monitoring and observation

### 7.3. Status Usage Guidelines

- **Be Consistent:** Use the same status values across all files
- **Be Current:** Update status regularly as work progresses
- **Be Clear:** Status should immediately indicate current state
- **Be Specific:** Use extended values when more granularity is helpful

## 8. Templates and Examples

### 8.1. Quick Reference

| File Type | Template Location | Example Location |
|-----------|------------------|------------------|
| PRD | [prd2prod-template-prd.md](./prd2prod-template-prd.md) | [prd2prod-example-csv-export.md](./prd2prod-example-csv-export.md) |
| Progress | [prd2prod-template-progress.md](./prd2prod_template-progress.md) | Various project examples |
| Task | [prd2prod-template-task.md](./prd2prod_template-task.md) | Task files in project root |
| Design Spec | [prd2prod-template-spec-design.md](./prd2prod_template-spec-design.md) | Spec files in project root |
| Dev Spec | [prd2prod-template-spec-dev.md](./prd2prod_template-spec-dev.md) | Spec files in project root |
| Issue | [prd2prod-template-issue.md](./prd2prod_template-issue.md) | Issue files in project root |
| Log | [prd2prod-template-log.md](./prd2prod_template-log.md) | Daily log files |

### 8.2. Template Usage

1. **Copy Template:** Start with the appropriate template
2. **Fill Sections:** Complete all required sections
3. **Follow Guidelines:** Apply content structure rules
4. **Review Checklist:** Ensure all requirements are met
5. **Link Appropriately:** Connect to related files correctly

### 8.3. Quality Checklist

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
