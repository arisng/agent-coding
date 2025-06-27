# Naming Conventions

File organization and naming standards for the PRD to Production documentation system.

- [1. General Principles](#1-general-principles)
  - [1.1. Basic Rules](#11-basic-rules)
  - [1.2. Hierarchical Organization](#12-hierarchical-organization)
- [2. File Categories and Prefixes](#2-file-categories-and-prefixes)
  - [2.1. Core/Index Documents (Top Listing)](#21-coreindex-documents-top-listing)
  - [2.2. Feature-Specific Task Lists](#22-feature-specific-task-lists)
  - [2.3. Issue Documentation](#23-issue-documentation)
  - [2.4. Daily Log Files](#24-daily-log-files)
  - [2.5. Specifications](#25-specifications)
    - [2.5.1. Design Specifications](#251-design-specifications)
    - [2.5.2. Development Specifications](#252-development-specifications)
    - [2.5.3. Alternative Development Specifications](#253-alternative-development-specifications)
  - [2.6. General Supporting Documentation](#26-general-supporting-documentation)
- [3. File Relationships Diagram](#3-file-relationships-diagram)
- [4. Directory Structure](#4-directory-structure)
  - [4.1. Project Root Structure](#41-project-root-structure)
  - [4.2. Benefits of This Structure](#42-benefits-of-this-structure)
- [5. ID Conventions](#5-id-conventions)
  - [5.1. Feature IDs](#51-feature-ids)
  - [5.2. ID Usage Examples](#52-id-usage-examples)
  - [5.3. ID References](#53-id-references)
- [6. Best Practices](#6-best-practices)
  - [6.1. File Naming](#61-file-naming)
  - [6.2. ID Management](#62-id-management)
  - [6.3. Directory Organization](#63-directory-organization)
- [7. Common Patterns](#7-common-patterns)
  - [7.1. Creating New Features](#71-creating-new-features)
  - [7.2. Handling Issues](#72-handling-issues)
  - [7.3. Documentation Updates](#73-documentation-updates)

## 1. General Principles

### 1.1. Basic Rules

- **Lowercase:** All filenames should be in lowercase
- **Kebab-case:** Words in filenames should be separated by hyphens (`-`) for the descriptive part of the name
- **Descriptive:** Filenames should clearly indicate their purpose and content
- **Consistent:** Follow established patterns for similar file types

### 1.2. Hierarchical Organization

Files are organized using a hierarchical naming pattern that groups related content:

```
prd2prod.md                          # Main hub (no suffix)
prd2prod-guide-*.md                  # Core guidance documents
prd2prod-template-*.md               # Templates and boilerplates
prd2prod-example-*.md                # Examples and case studies
prd2prod-reference-*.md              # Reference materials
```

## 2. File Categories and Prefixes

### 2.1. Core/Index Documents (Top Listing)

- **Prefix:** `_` (underscore)
- **Pattern:** `_<descriptive-name-in-kebab-case>.md`
- **Example:** `_prd.md`, `_progress.md`, `_logs.md`
- **Purpose:** For primary documents like the Product Requirements Document (PRD), main progress index, and logs index, ensuring they are listed at the top of directory listings

### 2.2. Feature-Specific Task Lists

- **Prefix:** `task_`
- **Pattern:** `task_<ID>_<feature-name-in-kebab-case>.md`
- **ID Structure:** The ID should start with `F` for functional features (e.g., `F001`, `F002`) or `N` for non-functional (e.g., `N001`, `N002`)
- **Example:** `task_F001_folder-management.md`, `task_F002_file-upload.md`
- **Purpose:** Contains tasks related to a specific feature, uniquely identified

### 2.3. Issue Documentation

- **Prefix:** `issue_`
- **Pattern:** `issue_<brief-issue-description-in-kebab-case>.md`
- **Example:** `issue_efcore-host-aborted-exception.md`
- **Purpose:** Documents a specific issue, its context, and potential solutions or follow-ups

### 2.4. Daily Log Files

- **Prefix:** `log_`
- **Pattern:** `log_YYMMDD.md` (e.g., `log_250626.md`)
- **Purpose:** Contains the detailed log for a specific day

### 2.5. Specifications

#### 2.5.1. Design Specifications

- **Prefix:** `spec-design_`
- **Pattern:** `spec-design_<feature-ID>_<topic-in-kebab-case>.md`
- **Example:** `spec-design_F002_architecture-overview.md`
- **Purpose:** Defines conceptual knowledge, system architecture, and design rationale. Includes diagrams (UML, flowcharts), high-level architecture, pseudocode, and explanations of design decisions

#### 2.5.2. Development Specifications

- **Prefix:** `spec-dev_`
- **Pattern:** `spec-dev_<feature-ID>_<topic-in-kebab-case>.md`
- **Example:** `spec-dev_F002_api-contracts.md`
- **Purpose:** Defines concrete coding approaches, implementation details, and technical steps for developers. Includes code samples, API contracts, configuration, and step-by-step implementation guides

#### 2.5.3. Alternative Development Specifications

- **Prefix:** `devspec_`
- **Pattern:** `devspec_<feature-ID>_<topic-in-kebab-case>.md`
- **Example:** `devspec_F002_chunked-upload-handler.md`
- **Purpose:** Alternative naming for development specifications when `spec-dev_` prefix is not preferred

### 2.6. General Supporting Documentation

- **No Prefix (Standard Names):** Other general documents
- **Pattern:** `<descriptive-name-in-kebab-case>.md`
- **Example:** `naming-conventions.md`, `troubleshooting-guide.md`
- **Purpose:** For general guidelines or supporting documents that don't fall into the above categories

## 3. File Relationships Diagram

Below is a simple ASCII art diagram showing the relationships between the main documentation files:

```
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
           +---+-----+------+
               |     |
         +-----+     +------+
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
- prd2prod-guide-*.md provides guidance for all files
```

## 4. Directory Structure

### 4.1. Project Root Structure

```
project-root/
├── _prd.md                          # Main requirements document
├── _progress.md                     # Progress tracking index
├── _logs.md                         # Logs index
├── task_F001_user-auth.md           # Feature tasks
├── task_F002_file-upload.md
├── spec-design_F001_auth-flow.md    # Design specifications
├── spec-dev_F001_auth-api.md        # Development specifications
├── issue_login-timeout.md           # Issue documentation
├── log_250626.md                    # Daily logs
└── docs/
    ├── prd2prod.md                  # Main documentation hub
    ├── prd2prod-guide-prd.md        # PRD guidelines
    ├── prd2prod-guide-workflow.md   # Workflow guide
    ├── prd2prod-guide-naming.md     # This file
    ├── prd2prod-guide-structure.md  # Content structure guide
    ├── prd2prod-template-prd.md     # PRD template
    └── prd2prod-example-*.md        # Examples
```

### 4.2. Benefits of This Structure

- **Clear Separation:** Documentation separate from project files
- **Easy Navigation:** Related files grouped together
- **Consistent Patterns:** Predictable naming across all file types
- **Scalable:** Easy to add new categories and files

## 5. ID Conventions

### 5.1. Feature IDs

- **Functional Features:** Use `F` prefix (F001, F002, F003, etc.)
- **Non-Functional Features:** Use `N` prefix (N001, N002, N003, etc.)
- **Sequential Numbering:** Start from 001 and increment sequentially
- **Zero-Padded:** Always use three digits (001, not 1)

### 5.2. ID Usage Examples

```markdown
## Functional Features
- F001: User authentication system
- F002: File upload capability
- F003: Export to CSV functionality

## Non-Functional Features  
- N001: System performance optimization
- N002: Security audit compliance
- N003: Deployment automation
```

### 5.3. ID References

When referencing features across documents:

- **In Progress Files:** List by ID for easy tracking
- **In Task Files:** Include ID in filename and content
- **In Spec Files:** Include ID in filename for clear association
- **Cross-References:** Always use full ID (F001, not F1 or 1)

## 6. Best Practices

### 6.1. File Naming

- **Be Descriptive:** Filename should indicate content without opening
- **Avoid Abbreviations:** Use full words when possible
- **Consistent Separators:** Use hyphens consistently, not mixed with underscores
- **Logical Grouping:** Use prefixes that group related files together

### 6.2. ID Management

- **Sequential Assignment:** Assign IDs in order of creation/priority
- **No Reuse:** Don't reuse IDs even if features are cancelled
- **Clear Mapping:** Maintain clear mapping between IDs and features
- **Documentation:** Document ID assignments in progress files

### 6.3. Directory Organization

- **Flat Structure:** Avoid deep nesting unless necessary
- **Logical Grouping:** Group files by purpose, not by date
- **Consistent Placement:** Always put similar files in same location
- **Clear Ownership:** Each file should have clear purpose and owner

## 7. Common Patterns

### 7.1. Creating New Features

1. **Assign ID:** Get next available F### or N### ID
2. **Create PRD:** `_prd_<feature-name>.md` (if separate PRD needed)
3. **Update Progress:** Add entry to `_progress.md`
4. **Create Task File:** `task_<ID>_<feature-name>.md`
5. **Create Specs:** `spec-design_<ID>_*.md` and `spec-dev_<ID>_*.md`

### 7.2. Handling Issues

1. **Create Issue File:** `issue_<brief-description>.md`
2. **Link to Tasks:** Reference from relevant task files
3. **Track in Progress:** Update status in `_progress.md`
4. **Resolve and Document:** Update all related files when resolved

### 7.3. Documentation Updates

1. **Follow Naming Conventions:** Use established patterns
2. **Update Cross-References:** Ensure all links remain valid
3. **Maintain Consistency:** Keep formatting and structure consistent
4. **Version Control:** Document changes and rationale

---

This naming convention ensures consistency, discoverability, and maintainability across all project documentation.
