# General Guidelines

## Naming Conventions

This document outlines the naming conventions used for Markdown files within this project's documentation, primarily located under `docs/prd1_azure-blob-storage-management/`.

### General Principles

- **Lowercase:** All filenames should be in lowercase.
- **Kebab-case:** Words in filenames should be separated by hyphens (`-`) for the descriptive part of the name.

### File Categories and Prefixes

To easily identify the purpose and ensure desired sorting for documentation files, specific prefixes are used:

1. **Core/Index Documents (Top Listing):**
    - **Prefix:** `_` (underscore)
    - **Pattern:** `_<descriptive-name-in-kebab-case>.md`
    - **Example:** `_prd.md`, `_tasks.md`, `_logs.md`
    - **Purpose:** For primary documents like the Product Requirements Document (PRD), main task index, and logs index, ensuring they are listed at the top of directory listings.

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

6. **Development Specification Files:**
    - **Prefix:** `devspec_`
    - **Pattern:** `devspec_<feature-ID>_<task-group-name-in-kebab-case>.md`
    - **Example:** `devspec_F002_chunked-upload-handler.md`
    - **Purpose:** Provides a detailed specification for a group of tasks within a feature (referenced by its ID), guiding development.

## Content Structure

### Content Structure for `_tasks` Files

`_tasks` files serve as a high-level index and priority guide for functionality and non-functionality scopes outlined in the corresponding `_prd` file. They also provide an overview of development priorities, with detailed tasks delegated to `feat_` files. The following structure should be followed:

1. **Title:**
    - The file should start with a title in the format `# Tasks for <Feature/Project Name>`.
    - Example: `# Tasks for Azure Blob Storage Management`

2. **Introduction:**
    - A brief introduction explaining the purpose of the `_tasks` file.
    - Example: `This document provides a high-level overview of development priorities and serves as an index for detailed tasks outlined in the corresponding 'feat_' files.`

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
        - **Related Files:** Links to the corresponding `feat_<ID>_<name>.md` files (for functional scopes).
    - Example:

        ```markdown
        - **Scope Name:** File Management
          - **ID:** F001
          - **Priority:** High
          - **Related Files:** [feat_F001_file-management.md](./feat_F001_file-management.md)
        - **Scope Name:** System Performance
          - **ID:** N001
          - **Priority:** Medium
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

By adhering to this structure, `_tasks` files will effectively serve as a single source of truth for development priorities and task indexing.

### Content Structure for `devspec_` Files

[doc-guideline-devspec.md](./doc-guideline-devspec.md)
