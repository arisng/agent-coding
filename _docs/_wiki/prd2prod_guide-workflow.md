# Workflow Guide

A step-by-step guide for moving from Product Requirements Documents (PRDs) to production deployment using a linear, repeatable workflow.

## Table of Contents

- [Linear Workflow Overview](#linear-workflow-overview)
- [Workflow Steps](#workflow-steps)
- [Examples by Complexity](#examples-by-complexity)
- [Feedback Loops](#feedback-loops)
- [Troubleshooting Common Issues](#troubleshooting-common-issues)

## Linear Workflow Overview

The linear workflow provides a consistent, repeatable process for efficiently capturing and using relevant context for any coding task, from simple documentation updates to complex feature implementations.

### Core Principle

Move from high-level context to actionable, fine-grain details in a consistent way for every coding task.

### Process Flow

```
PRD Creation → Progress Indexing → Design Specs → Dev Specs → Tasks → Implementation → Feedback
```

## Workflow Steps

### 1. Start with the High-Level Overview

- Begin with the core Product Requirements Document (`_prd.md`) to understand the big picture and project goals
- Review the feature's value proposition and acceptance criteria
- Understand dependencies and constraints

### 2. Review the Progress Index

- Use the main progress index (`_progress.md`) to see prioritized scopes and how work is organized
- Check current status and priority of related work
- Identify any blocking dependencies

### 3. Consult Design Specifications

- Reference `spec-design_` files for conceptual knowledge, architecture diagrams, and design rationale
- Use these to understand the "why" behind the approach
- Review system architecture and design decisions

### 4. Consult Development Specifications

- Reference `spec-dev_` and `devspec_` files for concrete coding approaches, implementation details, and technical steps
- Use these to guide actual development work
- Review API contracts, code samples, and configuration details

### 5. Drill Down into Actionable Tasks

- For specific features, consult the relevant `task_` files for detailed task breakdowns and unique identifiers
- Break work into small, manageable pieces
- Assign priorities and dependencies

### 6. Track Issues and Daily Progress

- Use `issue_` files for troubleshooting and documenting problems
- Use `log_` files for daily activity tracking
- Update progress status regularly

## Examples by Complexity

### Trivial Task (Documentation Update)

#### Workflow Application

1. **Start with the High-Level Overview**
   - Review `_prd.md` to confirm the documentation area and context
   - Verify the change aligns with project goals

2. **Review the Progress Index**
   - Check `_progress.md` for any related documentation tasks or priorities
   - Confirm no conflicting work is in progress

3. **Drill Down into Actionable Tasks**
   - Locate the relevant `task_` file (if any) for documentation updates
   - Create task file if none exists

4. **Skip Design/Development Specifications**
   - Not required for trivial documentation changes
   - Proceed directly to implementation

5. **Track Progress**
   - Optionally, log the update in `log_YYMMDD.md`
   - Update progress status when complete

#### Time Investment
- **Total Time:** 15-30 minutes
- **Documentation:** Minimal (update logs only)

### Complex Task (Implementing Chunked File Upload)

#### Workflow Application

1. **Start with the High-Level Overview**
   - Read `_prd.md` to understand the need for chunked file upload and its business value
   - Review acceptance criteria and success metrics

2. **Review the Progress Index**
   - In `_progress.md`, find the entry for file upload (e.g., Scope Name: File Management, ID: F002)
   - Check dependencies and current status

3. **Consult Design Specifications**
   - Review `spec-design_F002_chunked-upload.md` for:
     - Sequence diagrams of the upload process
     - Pseudocode outlining the chunking logic
     - Rationale for design decisions (e.g., why chunking is needed)

4. **Consult Development Specifications**
   - Follow `spec-dev_F002_chunked-upload-handler.md` and `devspec_F002_chunked-upload-handler.md` for:
     - API contracts and endpoint definitions
     - Step-by-step implementation instructions
     - Code samples and configuration details

5. **Drill Down into Feature Tasks**
   - Open `task_F002_file-upload.md` for a breakdown of tasks, priorities, and related requirements
   - Create subtasks as needed

6. **Track Issues and Daily Progress**
   - Document any blockers in `issue_chunked-upload-error.md`
   - Log daily progress in `log_YYMMDD.md`
   - Update progress status regularly

#### Time Investment
- **Total Time:** 2-5 days
- **Documentation:** Comprehensive (all file types)

### Real-Life Feature Delivery and Feedback Loop

#### Scenario: "Export to CSV" Feature Request

**1. Capture the Idea**
- A user submits feedback requesting the ability to export data to CSV
- Create a new `issue_export-to-csv-request.md` to document the request

**2. Prioritize and Plan**
- The issue is reviewed and prioritized in `_progress.md`
- Create `_prd_export-to-csv.md` following PRD guidelines
- Add entry to progress index with appropriate priority

**3. Design**
- Create `spec-design_F003_export-to-csv.md`, including:
  - A flowchart of the export process
  - Pseudocode for the export logic
  - Design rationale (e.g., why CSV, user needs, edge cases)

**4. Development Planning**
- Create `spec-dev_F003_export-to-csv-handler.md`, detailing:
  - API contracts for the export endpoint
  - Step-by-step implementation instructions
  - Code samples and configuration notes

**5. Task Breakdown**
- Create `task_F003_export-to-csv.md` with specific implementation tasks
- Update progress status as work progresses
- Log daily progress in `log_YYMMDD.md`

**6. Testing and Release**
- The feature is tested, reviewed, and marked as "Done" in `_progress.md`
- The feature is deployed to production
- Documentation is updated to reflect completion

**7. Feedback Loop**
- After release, monitoring tools detect a performance issue with large exports
- Create new `issue_export-csv-performance.md`
- Link the issue in `_progress.md` and create new `task_` for optimization
- The cycle repeats: design, develop, test, and deploy the fix

## Feedback Loops

### Closing the Cycle

To ensure continuous improvement and rapid response to real-world issues, integrate feedback from production and users back into your workflow:

#### Production Incidents
- Capture incidents, outages, or critical bugs as new `issue_` files
- Reference these issues in the relevant `task_` and `_progress.md` files for prioritization and tracking
- Create emergency PRDs for critical fixes when needed

#### User Feedback
- Document user-reported problems, feature requests, or usability concerns as `issue_` files or new `task_` files
- Link these to the appropriate scope in `_progress.md` for visibility
- Prioritize based on user impact and business value

#### Monitoring & Metrics
- Use logs, dashboards, and monitoring tools to identify performance, reliability, or security issues
- Create `issue_` or `task_` files as needed, and update the status in `_progress.md`
- Establish thresholds for automated issue creation

#### Retrospectives & Reviews
- After releases or major milestones, review what went well and what can be improved
- Capture action items as new `task_` or `issue_` files and feed them into the workflow
- Update process documentation based on lessons learned

### Feedback Integration Process

```
Production Issue → Issue File → Progress Update → PRD (if needed) → Task → Fix → Deploy
```

## Troubleshooting Common Issues

### Workflow Blockages

#### Problem: Can't Start Due to Missing Context
**Solution:**
- Always start with the PRD, even if incomplete
- Document what you know and what questions remain
- Create issue files for blocking questions

#### Problem: Scope Keeps Growing
**Solution:**
- Split large scopes into multiple PRDs
- Use "Out of Scope" sections aggressively
- Focus on minimum viable implementation first

#### Problem: Dependencies Block Progress
**Solution:**
- Map dependencies explicitly in PRDs
- Consider alternative approaches that reduce dependencies
- Create parallel work streams when possible

### Documentation Gaps

#### Problem: Missing Design Rationale
**Solution:**
- Always create design specs before development specs
- Document the "why" behind decisions
- Include diagrams and examples

#### Problem: Inconsistent File Organization
**Solution:**
- Follow naming conventions strictly
- Use file prefixes consistently
- Regular cleanup and reorganization

### Team Coordination Issues

#### Problem: Multiple People Working on Same Scope
**Solution:**
- Clear ownership assignment in progress files
- Regular status updates
- Break work into smaller, independent pieces

#### Problem: Lost Context Between Team Members
**Solution:**
- Complete documentation before handoffs
- Use the linear workflow consistently
- Regular team reviews of progress and blockers

## Best Practices

### Workflow Efficiency

- **Batch Similar Tasks:** Group related work to minimize context switching
- **Document Decisions:** Capture rationale in design specs
- **Regular Reviews:** Check progress and adjust priorities weekly
- **Automate Where Possible:** Use templates and tools to reduce manual work

### Quality Assurance

- **Peer Reviews:** Have others review PRDs and specs before implementation
- **Testing Integration:** Include testing considerations in all specs
- **Production Readiness:** Plan deployment and monitoring from the start

### Continuous Improvement

- **Metrics Collection:** Track cycle times and issue rates
- **Process Refinement:** Regular retrospectives and process updates
- **Tool Evolution:** Improve templates and automation based on usage

---

**Next Steps:** Apply this workflow to your current project, starting with creating or updating your PRDs and progress index.
