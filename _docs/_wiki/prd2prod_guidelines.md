# General Guidelines

- [1. Linear Workflow: A Repeatable Mental Model](#1-linear-workflow-a-repeatable-mental-model)
  - [1.1. Sample Linear Workflow in Action](#11-sample-linear-workflow-in-action)
    - [1.1.1. Example 1: Trivial Task (Documentation Update)](#111-example-1-trivial-task-documentation-update)
    - [1.1.2. Example 2: Complex Task (Implementing Chunked File Upload)](#112-example-2-complex-task-implementing-chunked-file-upload)
- [2. Naming Conventions](#2-naming-conventions)
  - [2.1. General Principles](#21-general-principles)
  - [2.2. File Categories and Prefixes](#22-file-categories-and-prefixes)
  - [2.3. File Relationships Diagram](#23-file-relationships-diagram)
  - [2.3.1. File Relationships Overview (Text Version)](#231-file-relationships-overview-text-version)
  - [2.3.2. File Relationships Diagram (ASCII Art)](#232-file-relationships-diagram-ascii-art)
- [3. Content Structure](#3-content-structure)
  - [3.1. Content Structure for `_progress` Files](#31-content-structure-for-_progress-files)
  - [3.1.1. Recommended Status Values for `_progress` Files](#311-recommended-status-values-for-_progress-files)
  - [3.2. Content Structure for `devspec_` Files](#32-content-structure-for-devspec_-files)

## 1. Linear Workflow: A Repeatable Mental Model

To efficiently capture and use relevant context for coding tasks, follow this linear workflow as a repeatable process:

1. **Start with the High-Level Overview**
   - Begin with the core Product Requirements Document (`_prd.md`) to understand the big picture and project goals.

2. **Review the Progress Index**
   - Use the main progress index (`_progress.md`) to see prioritized scopes and how work is organized.

3. **Drill Down into Feature Tasks**
   - For specific features, consult the relevant `feat_` files for detailed task breakdowns and unique identifiers.

4. **Consult Design Specifications**
   - Reference `spec-design_` files for conceptual knowledge, architecture diagrams, and design rationale. Use these to understand the "why" behind the approach.

5. **Consult Development Specifications**
   - Reference `spec-dev_` and `devspec_` files for concrete coding approaches, implementation details, and technical steps. Use these to guide actual development work.

6. **Track Issues and Daily Progress**
   - Use `issue_` files for troubleshooting and documenting problems, and `log_` files for daily activity tracking.

This workflow ensures you move from high-level context to actionable, fine-grain details in a consistent, repeatable way for every coding task.

### 1.1. Sample Linear Workflow in Action

Below are two examples demonstrating how to apply the linear workflow for different levels of task complexity.

#### 1.1.1. Example 1: Trivial Task (Documentation Update)

1. **Start with the High-Level Overview**
   - Review `_prd.md` to confirm the documentation area and context.

2. **Review the Progress Index**
   - Check `_progress.md` for any related documentation tasks or priorities.

3. **Drill Down into Feature Tasks**
   - Locate the relevant `feat_` file (if any) for documentation updates.

4. **Consult Design Specifications**
   - Not required for trivial documentation changes.

5. **Consult Development Specifications**
   - Not required for trivial documentation changes.

6. **Track Issues and Daily Progress**
   - Optionally, log the update in `log_YYMMDD.md`.

#### 1.1.2. Example 2: Complex Task (Implementing Chunked File Upload)

1. **Start with the High-Level Overview**
   - Read `_prd.md` to understand the need for chunked file upload and its business value.

2. **Review the Progress Index**
   - In `_progress.md`, find the entry for file upload (e.g., Scope Name: File Management, ID: F002).

3. **Drill Down into Feature Tasks**
   - Open `feat_F002_file-upload.md` for a breakdown of tasks, priorities, and related requirements.

4. **Consult Design Specifications**
   - Review `spec-design_F002_chunked-upload.md` for:
     - Sequence diagrams of the upload process.
     - Pseudocode outlining the chunking logic.
     - Rationale for design decisions (e.g., why chunking is needed).

5. **Consult Development Specifications**
   - Follow `spec-dev_F002_chunked-upload-handler.md` and `devspec_F002_chunked-upload-handler.md` for:
     - API contracts and endpoint definitions.
     - Step-by-step implementation instructions.
     - Code samples and configuration details.

6. **Track Issues and Daily Progress**
   - Document any blockers in `issue_chunked-upload-error.md`.
   - Log daily progress in `log_YYMMDD.md`.

This approach ensures you always have the right context and level of detail for any coding task, from the simplest to the most complex.

## 2. Naming Conventions

This document outlines the naming conventions used for Markdown files within this project's documentation, primarily located under `docs/prd1_azure-blob-storage-management/`.

### 2.1. General Principles

- **Lowercase:** All filenames should be in lowercase.
- **Kebab-case:** Words in filenames should be separated by hyphens (`-`) for the descriptive part of the name.

### 2.2. File Categories and Prefixes

To easily identify the purpose and ensure desired sorting for documentation files, specific prefixes are used:

1. **Core/Index Documents (Top Listing):**
    - **Prefix:** `_` (underscore)
    - **Pattern:** `_<descriptive-name-in-kebab-case>.md`
    - **Example:** `_prd.md`, `_progress.md`, `_logs.md`
    - **Purpose:** For primary documents like the Product Requirements Document (PRD), main progress index, and logs index, ensuring they are listed at the top of directory listings.

2. **Feature-Specific Task Lists:**
    - **Prefix:** `feat_`
    - **Pattern:** `feat_<ID>_<feature-name-in-kebab-case>.md`
    - **ID Structure:** The ID should start with `F` for functional features (e.g., `F001`, `F002`).
    - **Example:** `feat_F001_folder-management.md`, `feat_F002_file-upload.md`
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

### 2.3. File Relationships Diagram

Below is a diagram illustrating the relationships and typical references between documentation files in this system:

```mermaid
flowchart TD
    PRD[_prd.md\n(Product Requirements)]
    PROGRESS[_progress.md\n(Progress Index)]
    FEAT[feat_*.md\n(Feature Tasks)]
    SPECDEV[spec-dev_*.md\n(Development Specs)]
    SPECDESIGN[spec-design_*.md\n(Design Specs)]
    ISSUE[issue_*.md\n(Issues)]
    LOG[log_*.md\n(Daily Logs)]
    DOC[naming-conventions.md\n(General Docs)]

    PRD --> PROGRESS
    PROGRESS --> FEAT
    FEAT --> SPECDEV
    FEAT --> SPECDESIGN
    FEAT --> ISSUE
    PROGRESS --> ISSUE
    PROGRESS --> LOG
    FEAT --> LOG
    SPECDEV --> LOG
    SPECDESIGN --> LOG
    DOC --- PRD
    DOC --- PROGRESS
    DOC --- FEAT
    DOC --- SPECDEV
    DOC --- SPECDESIGN
    DOC --- ISSUE
    DOC --- LOG
```

This diagram shows the typical navigation and reference flow, helping new and existing team members understand how to move between files and where to find relevant context.

### 2.3.1. File Relationships Overview (Text Version)

The following text-based outline describes how the main documentation files relate to each other:

- `_prd.md` (Product Requirements)
  - References: `_progress.md`

- `_progress.md` (Progress Index)
  - References: `feat_*.md` (Feature Tasks)
  - References: `issue_*.md` (Issues)
  - References: `log_*.md` (Daily Logs)

- `feat_*.md` (Feature Tasks)
  - References: `spec-dev_*.md` (Development Specs)
  - References: `spec-design_*.md` (Design Specs)
  - References: `issue_*.md` (Issues)
  - References: `log_*.md` (Daily Logs)

- `spec-dev_*.md` (Development Specs)
  - May reference: `log_*.md` (Daily Logs)

- `spec-design_*.md` (Design Specs)
  - May reference: `log_*.md` (Daily Logs)

- `issue_*.md` (Issues)
  - May be referenced by: `_progress.md`, `feat_*.md`

- `log_*.md` (Daily Logs)
  - May be referenced by: `_progress.md`, `feat_*.md`, `spec-dev_*.md`, `spec-design_*.md`

- `naming-conventions.md` (General Docs)
  - Provides guidance for all other files

This outline helps clarify the navigation and reference flow for your documentation system in a simple, text-only format.

### 2.3.2. File Relationships Diagram (ASCII Art)

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
           | feat_*.md      |
           | (Feature Tasks)|
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
- feat_*.md and _progress.md both reference issue_*.md (Issues)
- naming-conventions.md provides guidance for all files
```

This diagram provides a quick, text-based overview of how the main documentation files are connected.

## 3. Content Structure

### 3.1. Content Structure for `_progress` Files

`_progress` files serve as a high-level index and priority guide for functionality and non-functionality scopes outlined in the corresponding `_prd` file. They also provide an overview of development priorities and progress, with detailed tasks delegated to `feat_` files. The following structure should be followed:

1. **Title:**
    - The file should start with a title in the format `# Progress for <Feature/Project Name>`.
    - Example: `# Progress for Azure Blob Storage Management`

2. **Introduction:**
    - A brief introduction explaining the purpose of the `_progress` file.
    - Example: `This document provides a high-level overview of development priorities and progress, and serves as an index for detailed tasks outlined in the corresponding 'feat_' files.`

3. **Priority Sections:**
    - Divide the tasks into two main sections:
        - **Functionality Scopes:** High-level features or functionalities.
        - **Non-Functionality Scopes:** Aspects like performance, security, deployment, or compliance.

4. **Task Index:**
    - For each scope, list the related `feat_` files as references (if applicable).
    - Use the following format:
        - **Scope Name:** A concise name for the scope.
        - **ID:** A unique identifier (e.g., `F001` for functional, `N001` for non-functional).
        - **Priority:** High, Medium, or Low.
        - **Status:** Current status (e.g., Not Started, In Progress, Done).
        - **Related Files:** Links to the corresponding `feat_<ID>_<name>.md` files (for functional scopes).
    - Example:

        ```markdown
        - **Scope Name:** File Management
          - **ID:** F001
          - **Priority:** High
          - **Status:** In Progress
          - **Related Files:** [feat_F001_file-management.md](./feat_F001_file-management.md)
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

### 3.1.1. Recommended Status Values for `_progress` Files

To ensure consistency and clarity, use the following status values in the `_progress` file:

- **Not Started**: Work has not begun on this scope or task.
- **In Progress**: Work is actively being done.
- **Blocked**: Progress is halted due to a dependency, issue, or external factor.
- **Review**: Work is complete and under review (e.g., code review, QA).
- **Done**: Work is fully completed and accepted.
- **Deferred**: Work is intentionally postponed for future consideration.

Use these statuses in the "Status" field of each entry in the Task Index section to clearly communicate the current state of each scope or task.

### 3.2. Content Structure for `devspec_` Files

[doc-guideline-devspec.md](./doc-guideline-devspec.md)
