# PRD to Production Guidelines

- [1. Explicit Guidance on PRD Scope](#1-explicit-guidance-on-prd-scope)
  - [1.1. What Makes a Good PRD Scope?](#11-what-makes-a-good-prd-scope)
  - [1.2. PRD Scope Checklist](#12-prd-scope-checklist)
  - [1.3. Best Practices for PRD Scoping](#13-best-practices-for-prd-scoping)
  - [1.4. Lightweight PRD Template](#14-lightweight-prd-template)
  - [1.5. Example: Small PRD Scope](#15-example-small-prd-scope)
  - [1.6. Referencing Convention for PRDs](#16-referencing-convention-for-prds)
- [2. Linear Workflow: A Repeatable Mental Model](#2-linear-workflow-a-repeatable-mental-model)
  - [2.1. Sample Linear Workflow in Action](#21-sample-linear-workflow-in-action)
    - [2.1.1. Example 1: Trivial Task (Documentation Update)](#211-example-1-trivial-task-documentation-update)
    - [2.1.2. Example 2: Complex Task (Implementing Chunked File Upload)](#212-example-2-complex-task-implementing-chunked-file-upload)
    - [2.1.3. Example 3: Real-Life Feature Delivery and Feedback Loop](#213-example-3-real-life-feature-delivery-and-feedback-loop)
  - [2.2. Feedback Loops: Closing the Cycle](#22-feedback-loops-closing-the-cycle)
- [3. Naming Conventions](#3-naming-conventions)
  - [3.1. General Principles](#31-general-principles)
  - [3.2. File Categories and Prefixes](#32-file-categories-and-prefixes)
  - [3.3. File Relationships Diagram](#33-file-relationships-diagram)
- [4. Content Structure](#4-content-structure)
  - [4.1. Content Structure for `_progress` Files](#41-content-structure-for-_progress-files)
  - [4.2. Recommended Status Values for `_progress` Files](#42-recommended-status-values-for-_progress-files)
  - [4.3. Content Structure for `devspec_` Files](#43-content-structure-for-devspec_-files)

## 1. Explicit Guidance on PRD Scope

A well-scoped PRD (Product Requirements Document) is the foundation for delivering actionable, traceable, and manageable work. The goal is to define a scope that is small enough to be delivered quickly, yet meaningful enough to provide value.

### 1.1. What Makes a Good PRD Scope?

- **Actionable:** The scope should be small enough to be completed in a short cycle (ideally days, not weeks).
- **Testable:** The outcome should be verifiable (e.g., via acceptance criteria or test cases).
- **Traceable:** Each PRD should map directly to progress, tasks, and feedback.
- **Independent:** Avoid dependencies that could block progress; split large features into smaller, independent deliverables.
- **Valuable:** Each PRD should deliver a user-facing or technical improvement.
- **Faster Delivery:** Small scopes reduce risk and allow for quicker iteration.
- **Clear Ownership:** Each PRD can be assigned to an individual or small team.
- **Easier Review:** Focused changes are easier to review, test, and validate.
- **Continuous Improvement:** Frequent, small releases enable rapid feedback and learning.

### 1.2. PRD Scope Checklist

Before finalizing a PRD, ensure you can answer "yes" to the following:

- [ ] Is the scope clearly defined and unambiguous?
- [ ] Can the work be completed in a short cycle (e.g., 1-5 days)?
- [ ] Are acceptance criteria or success metrics specified?
- [ ] Are dependencies and risks identified and minimized?
- [ ] Is the scope small enough to allow for rapid feedback and iteration?
- [ ] Does the PRD link to related tasks, specs, and issues?
- [ ] The PRD addresses a single feature, enhancement, or fix (not a broad project)?
- [ ] The scope is clear enough to break down into a handful of `task_` files (ideally 1–5 tasks)?
- [ ] Dependencies and blockers are identified and limited?
- [ ] The PRD can be closed independently (not open-ended or perpetually growing)?
- [ ] Stakeholders can review and approve the PRD without ambiguity?

### 1.3. Best Practices for PRD Scoping

- **Start Small:** If a feature is too big, split it into multiple PRDs, each with its own `_prd.md` and progress tracking.
- **Iterate:** Use feedback loops to refine and expand scope in future cycles.
- **Document Out-of-Scope Items:** Clearly state what is not included to avoid ambiguity.
- **Link Everything:** Reference related `task_`, `spec-`, and `issue_` files for traceability.
- **Keep It Actionable:** Avoid vague or aspirational language—focus on what will be delivered.
- **Review Regularly:** Revisit open PRDs to ensure they remain relevant and scoped appropriately.
- **Link Related PRDs:** Use references to connect related or dependent PRDs.

### 1.4. Lightweight PRD Template

A reusable PRD template is available for all new scopes. See [prd2prod_template-prd.md](./prd2prod_template-prd.md) for a copy-paste ready version.

### 1.5. Example: Small PRD Scope

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

## Dependencies & Risks
- None for initial version.

## Links & References
- [task_F003_export-to-csv.md](./task_F003_export-to-csv.md)
- [spec-design_F003_export-to-csv.md](./spec-design_F003_export-to-csv.md)
```

By following this guidance, your PRDs will be concise, actionable, and tightly integrated with the rest of your workflow.

### 1.6. Referencing Convention for PRDs

- In the "Related Files" section of a PRD, only reference:
  - Other PRDs (to show inheritance, extension, or dependencies)
  - The internal progress file (`_progress.md`)
- Do not reference downstream files such as `task_`, `spec-`, or `issue_` files directly from a PRD.
- This ensures clear separation of concerns and maintains upstream-only referencing. Downstream files should reference the PRD, not the other way around.

## 2. Linear Workflow: A Repeatable Mental Model

To efficiently capture and use relevant context for coding tasks, follow this linear workflow as a repeatable process:

1. **Start with the High-Level Overview**
   - Begin with the core Product Requirements Document (`_prd.md`) to understand the big picture and project goals.

2. **Review the Progress Index**
   - Use the main progress index (`_progress.md`) to see prioritized scopes and how work is organized.

3. **Consult Design Specifications**
   - Reference `spec-design_` files for conceptual knowledge, architecture diagrams, and design rationale. Use these to understand the "why" behind the approach.

4. **Consult Development Specifications**
   - Reference `spec-dev_` and `devspec_` files for concrete coding approaches, implementation details, and technical steps. Use these to guide actual development work.

5. **Drill Down into Actionable Tasks**
   - For specific features, consult the relevant `task_` files for detailed task breakdowns and unique identifiers.

6. **Track Issues and Daily Progress**
   - Use `issue_` files for troubleshooting and documenting problems, and `log_` files for daily activity tracking.

This workflow ensures you move from high-level context to actionable, fine-grain details in a consistent, repeatable way for every coding task.

### 2.1. Sample Linear Workflow in Action

See [prd2prod_example1.md](./prd2prod_example1.md) for a complete, real-life, end-to-end example that demonstrates the linear workflow in practice. This example covers:

- Creating a PRD with functional and non-functional features (IDs starting from 001)
- Referencing and extending existing PRDs
- Prioritizing and indexing scopes in `_progress.md`
- Creating specifications before breaking down into actionable tasks
- Tracking issues, progress, and feedback loops

This example provides a concrete reference for applying the mental model described in this section.

Below are two more examples demonstrating how to apply the linear workflow for different levels of task complexity.

#### 2.1.1. Example 1: Trivial Task (Documentation Update)

1. **Start with the High-Level Overview**
   - Review `_prd.md` to confirm the documentation area and context.

2. **Review the Progress Index**
   - Check `_progress.md` for any related documentation tasks or priorities.

3. **Drill Down into Actionable Tasks**
   - Locate the relevant `task_` file (if any) for documentation updates.

4. **Consult Design Specifications**
   - Not required for trivial documentation changes.

5. **Consult Development Specifications**
   - Not required for trivial documentation changes.

6. **Track Issues and Daily Progress**
   - Optionally, log the update in `log_YYMMDD.md`.

#### 2.1.2. Example 2: Complex Task (Implementing Chunked File Upload)

1. **Start with the High-Level Overview**
   - Read `_prd.md` to understand the need for chunked file upload and its business value.

2. **Review the Progress Index**
   - In `_progress.md`, find the entry for file upload (e.g., Scope Name: File Management, ID: F002).

3. **Consult Design Specifications**
   - Review `spec-design_F002_chunked-upload.md` for:
     - Sequence diagrams of the upload process.
     - Pseudocode outlining the chunking logic.
     - Rationale for design decisions (e.g., why chunking is needed).

4. **Consult Development Specifications**
   - Follow `spec-dev_F002_chunked-upload-handler.md` and `devspec_F002_chunked-upload-handler.md` for:
     - API contracts and endpoint definitions.
     - Step-by-step implementation instructions.
     - Code samples and configuration details.

5. **Drill Down into Feature Tasks**
   - Open `task_F002_file-upload.md` for a breakdown of tasks, priorities, and related requirements.

6. **Track Issues and Daily Progress**
   - Document any blockers in `issue_chunked-upload-error.md`.
   - Log daily progress in `log_YYMMDD.md`.

This approach ensures you always have the right context and level of detail for any coding task, from the simplest to the most complex.

#### 2.1.3. Example 3: Real-Life Feature Delivery and Feedback Loop

Suppose a user requests a new "Export to CSV" feature for your application. Here’s how the process flows from idea to production and back through the feedback loop:

1. **Capture the Idea**
   - A user submits feedback requesting the ability to export data to CSV.
   - You create a new `issue_export-to-csv-request.md` to document the request.

2. **Prioritize and Plan**
   - The issue is reviewed and prioritized in `_progress.md`.
   - A new `task_F003_export-to-csv.md` is created to break down the work required for the feature.

3. **Design**
   - A `spec-design_F003_export-to-csv.md` file is created, including:
     - A flowchart of the export process.
     - Pseudocode for the export logic.
     - Design rationale (e.g., why CSV, user needs, edge cases).

4. **Development**
   - A `spec-dev_F003_export-to-csv-handler.md` file is created, detailing:
     - API contracts for the export endpoint.
     - Step-by-step implementation instructions.
     - Code samples and configuration notes.
   - The `task_F003_export-to-csv.md` file is updated as work progresses.
   - Daily progress is logged in `log_YYMMDD.md`.

5. **Testing and Release**
   - The feature is tested, reviewed, and marked as "Done" in `_progress.md`.
   - The feature is deployed to production.

6. **Feedback Loop**
   - After release, monitoring tools detect a performance issue with large exports.
   - A new `issue_export-csv-performance.md` is created.
   - The issue is linked in `_progress.md` and a new `task_` is created for optimization.
   - The cycle repeats: design, develop, test, and deploy the fix, with all steps documented and tracked.

This example demonstrates how an idea moves from user feedback to a working feature in production, and how feedback from production is captured and reintegrated for continuous improvement.

### 2.2. Feedback Loops: Closing the Cycle

To ensure continuous improvement and rapid response to real-world issues, integrate feedback from production and users back into your workflow:

- **Production Incidents:**
  - Capture incidents, outages, or critical bugs as new `issue_` files.
  - Reference these issues in the relevant `task_` and `_progress.md` files for prioritization and tracking.

- **User Feedback:**
  - Document user-reported problems, feature requests, or usability concerns as `issue_` files or new `task_` files.
  - Link these to the appropriate scope in `_progress.md` for visibility.

- **Monitoring & Metrics:**
  - Use logs, dashboards, and monitoring tools to identify performance, reliability, or security issues.
  - Create `issue_` or `task_` files as needed, and update the status in `_progress.md`.

- **Retrospectives & Reviews:**
  - After releases or major milestones, review what went well and what can be improved.
  - Capture action items as new `task_` or `issue_` files and feed them into the workflow.

By systematically capturing and acting on feedback, your workflow becomes a closed loop—enabling you to deliver, learn, and improve with every cycle from PRD to production.

## 3. Naming Conventions

This document outlines the naming conventions used for Markdown files within this project's documentation, primarily located under `docs/prd1_azure-blob-storage-management/`.

### 3.1. General Principles

- **Lowercase:** All filenames should be in lowercase.
- **Kebab-case:** Words in filenames should be separated by hyphens (`-`) for the descriptive part of the name.

### 3.2. File Categories and Prefixes

To easily identify the purpose and ensure desired sorting for documentation files, specific prefixes are used:

1. **Core/Index Documents (Top Listing):**
    - **Prefix:** `_` (underscore)
    - **Pattern:** `_<descriptive-name-in-kebab-case>.md`
    - **Example:** `_prd.md`, `_progress.md`, `_logs.md`
    - **Purpose:** For primary documents like the Product Requirements Document (PRD), main progress index, and logs index, ensuring they are listed at the top of directory listings.

2. **Feature-Specific Task Lists:**
    - **Prefix:** `task_`
    - **Pattern:** `task_<ID>_<feature-name-in-kebab-case>.md`
    - **ID Structure:** The ID should start with `F` for functional features (e.g., `F001`, `F002`).
    - **Example:** `task_F001_folder-management.md`, `task_F002_file-upload.md`
    - **Purpose:** Contains tasks related to a specific feature, uniquely identified.

3. **Issue Documentation:**
    - **Prefix:** `issue_`
    - **Pattern:** `issue_<brief-issue-description-in-kebab-case>.md`
    - **Example:** `issue_efcore-host-aborted-exception.md`
    - **Purpose:** Documents a specific issue, its context, and potential solutions or follow-ups.

4. **Daily Log Files:**
    - **Prefix:** `log_`
    - **Pattern:** `log_YYMMDD.md` (e.g., `log_250507.md`)
    - **Purpose:** Contains the detailed log for a specific day.

5. **General Supporting Documentation:**
    - **No Prefix (Standard Names):** Other general documents like this `naming-conventions.md` file.
    - **Pattern:** `<descriptive-name-in-kebab-case>.md`
    - **Example:** `naming-conventions.md`
    - **Purpose:** For general guidelines or supporting documents that don't fall into the above categories.

6. **Specifications:**
    - **Prefix:** `spec-dev_` or `spec-design_`
    - **Pattern:**
        - `spec-dev_<feature-ID>_<topic-in-kebab-case>.md`
        - `spec-design_<feature-ID>_<topic-in-kebab-case>.md`
    - **Example:**
        - `spec-dev_F002_api-contracts.md`
        - `spec-design_F002_architecture-overview.md`
    - **Purpose:**
        - `spec-dev_`: Defines concrete coding approaches, implementation details, and technical steps for developers. Includes code samples, API contracts, configuration, and step-by-step implementation guides.
        - `spec-design_`: Defines conceptual knowledge, system architecture, and design rationale. Includes diagrams (UML, flowcharts), high-level architecture, pseudocode, and explanations of design decisions.

### 3.3. File Relationships Diagram

Below is a simple ASCII art diagram showing the relationships between the main documentation files:

```ASCII
           +----------------+
           |   _prd.md      |
           | (Requirements) |
           +-------+--------+
                   |
                   v
           +----------------+
           | _progress.md    |
           | (Progress Index)|
           +-------+--------+
                   |
                   v
           +----------------+
           | task_*.md      |
           | (Task Files)   |
           +---+-----+------
               |     |
         +-----+     +------
         v                  v
+----------------+   +-------------------+
| spec-dev_*.md  |   | spec-design_*.md  |
| (Dev Specs)    |   | (Design Specs)    |
+----------------+   +-------------------+
               |           |
               +-----+-----+
                     |
                     v
              +----------------+
              |  log_*.md      |
              | (Daily Logs)   |
              +----------------+

Other relationships:
- task_*.md and _progress.md both reference issue_*.md (Issues)
- naming-conventions.md provides guidance for all files
```

This diagram provides a quick, text-based overview of how the main documentation files are connected.

## 4. Content Structure

### 4.1. Content Structure for `_progress` Files

`_progress` files serve as a high-level index and priority guide for functionality and non-functionality scopes outlined in the corresponding `_prd` file. They also provide an overview of development priorities and progress, with detailed tasks delegated to `task_` files. The following structure should be followed:

1. **Title:**
    - The file should start with a title in the format `# Progress for <Feature/Project Name>`.
    - Example: `# Progress for Azure Blob Storage Management`

2. **Introduction:**
    - A brief introduction explaining the purpose of the `_progress` file.
    - Example: `This document provides a high-level overview of development priorities and progress, and serves as an index for detailed tasks outlined in the corresponding 'task_' files.`

3. **Priority Sections:**
    - Divide the tasks into two main sections:
        - **Functionality Scopes:** High-level features or functionalities.
        - **Non-Functionality Scopes:** Aspects like performance, security, deployment, or compliance.

4. **Task Index:**
    - For each scope, list the related `task_` files as references (if applicable).
    - Use the following format:
        - **Scope Name:** A concise name for the scope.
        - **ID:** A unique identifier (e.g., `F001` for functional, `N001` for non-functional).
        - **Priority:** High, Medium, or Low.
        - **Status:** Current status (e.g., Not Started, In Progress, Done).
        - **Related Files:** Links to the corresponding `task_<ID>_<name>.md` files (for functional scopes).
    - Example:

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
          - **Description:** Ensuring the application meets performance benchmarks.
        ```

5. **References:**
    - Include a section at the end of the file for any references or related documentation.
    - Example:

        ```markdown
        ## References
        - [_prd.md](./_prd.md)
        - [Azure Blob Storage Documentation](https://learn.microsoft.com/en-us/azure/storage/blobs/)
        ```

By adhering to this structure, `_progress` files will effectively serve as a single source of truth for development priorities, task indexing, and progress tracking.

### 4.2. Recommended Status Values for `_progress` Files

To ensure consistency and clarity, use the following status values in the `_progress` file:

- **Not Started**: Work has not begun on this scope or task.
- **In Progress**: Work is actively being done.
- **Blocked**: Progress is halted due to a dependency, issue, or external factor.
- **Review**: Work is complete and under review (e.g., code review, QA).
- **Done**: Work is fully completed and accepted.
- **Deferred**: Work is intentionally postponed for future consideration.

Use these statuses in the "Status" field of each entry in the Task Index section to clearly communicate the current state of each scope or task.

### 4.3. Content Structure for `devspec_` Files

[doc-guideline-devspec.md](./doc-guideline-devspec.md)
