# Naming Conventions

File organization and naming standards for the PRD to Production documentation system.

## Table of Contents

- [General Principles](#general-principles)
- [File Categories and Prefixes](#file-categories-and-prefixes)
- [File Relationships Diagram](#file-relationships-diagram)
- [Directory Structure](#directory-structure)
- [ID Conventions](#id-conventions)

## General Principles

### Basic Rules

- **Lowercase:** All filenames should be in lowercase
- **Kebab-case:** Words in filenames should be separated by hyphens (`-`) for the descriptive part of the name
- **Descriptive:** Filenames should clearly indicate their purpose and content
- **Consistent:** Follow established patterns for similar file types

### Hierarchical Organization

Files are organized using a hierarchical naming pattern that groups related content:

```
prd2prod.md                          # Main hub (no suffix)
prd2prod-guide-*.md                  # Core guidance documents
prd2prod-template-*.md               # Templates and boilerplates
prd2prod-example-*.md                # Examples and case studies
prd2prod-reference-*.md              # Reference materials
```

## File Categories and Prefixes

### Core/Index Documents (Top Listing)

- **Prefix:** `_` (underscore)
- **Pattern:** `_<descriptive-name-in-kebab-case>.md`
- **Example:** `_prd.md`, `_progress.md`, `_logs.md`
- **Purpose:** For primary documents like the Product Requirements Document (PRD), main progress index, and logs index, ensuring they are listed at the top of directory listings

### Feature-Specific Task Lists

- **Prefix:** `task_`
- **Pattern:** `task_<ID>_<feature-name-in-kebab-case>.md`
- **ID Structure:** The ID should start with `F` for functional features (e.g., `F001`, `F002`) or `N` for non-functional (e.g., `N001`, `N002`)
- **Example:** `task_F001_folder-management.md`, `task_F002_file-upload.md`
- **Purpose:** Contains tasks related to a specific feature, uniquely identified

### Issue Documentation

- **Prefix:** `issue_`
- **Pattern:** `issue_<brief-issue-description-in-kebab-case>.md`
- **Example:** `issue_efcore-host-aborted-exception.md`
- **Purpose:** Documents a specific issue, its context, and potential solutions or follow-ups

### Daily Log Files

- **Prefix:** `log_`
- **Pattern:** `log_YYMMDD.md` (e.g., `log_250626.md`)
- **Purpose:** Contains the detailed log for a specific day

### Specifications

#### Design Specifications

- **Prefix:** `spec-design_`
- **Pattern:** `spec-design_<feature-ID>_<topic-in-kebab-case>.md`
- **Example:** `spec-design_F002_architecture-overview.md`
- **Purpose:** Defines conceptual knowledge, system architecture, and design rationale. Includes diagrams (UML, flowcharts), high-level architecture, pseudocode, and explanations of design decisions

#### Development Specifications

- **Prefix:** `spec-dev_`
- **Pattern:** `spec-dev_<feature-ID>_<topic-in-kebab-case>.md`
- **Example:** `spec-dev_F002_api-contracts.md`
- **Purpose:** Defines concrete coding approaches, implementation details, and technical steps for developers. Includes code samples, API contracts, configuration, and step-by-step implementation guides

#### Alternative Development Specifications

- **Prefix:** `devspec_`
- **Pattern:** `devspec_<feature-ID>_<topic-in-kebab-case>.md`
- **Example:** `devspec_F002_chunked-upload-handler.md`
- **Purpose:** Alternative naming for development specifications when `spec-dev_` prefix is not preferred

### General Supporting Documentation

- **No Prefix (Standard Names):** Other general documents
- **Pattern:** `<descriptive-name-in-kebab-case>.md`
- **Example:** `naming-conventions.md`, `troubleshooting-guide.md`
- **Purpose:** For general guidelines or supporting documents that don't fall into the above categories

## File Relationships Diagram

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

## Directory Structure

### Project Root Structure

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

### Benefits of This Structure

- **Clear Separation:** Documentation separate from project files
- **Easy Navigation:** Related files grouped together
- **Consistent Patterns:** Predictable naming across all file types
- **Scalable:** Easy to add new categories and files

## ID Conventions

### Feature IDs

- **Functional Features:** Use `F` prefix (F001, F002, F003, etc.)
- **Non-Functional Features:** Use `N` prefix (N001, N002, N003, etc.)
- **Sequential Numbering:** Start from 001 and increment sequentially
- **Zero-Padded:** Always use three digits (001, not 1)

### ID Usage Examples

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

### ID References

When referencing features across documents:

- **In Progress Files:** List by ID for easy tracking
- **In Task Files:** Include ID in filename and content
- **In Spec Files:** Include ID in filename for clear association
- **Cross-References:** Always use full ID (F001, not F1 or 1)

## Best Practices

### File Naming

- **Be Descriptive:** Filename should indicate content without opening
- **Avoid Abbreviations:** Use full words when possible
- **Consistent Separators:** Use hyphens consistently, not mixed with underscores
- **Logical Grouping:** Use prefixes that group related files together

### ID Management

- **Sequential Assignment:** Assign IDs in order of creation/priority
- **No Reuse:** Don't reuse IDs even if features are cancelled
- **Clear Mapping:** Maintain clear mapping between IDs and features
- **Documentation:** Document ID assignments in progress files

### Directory Organization

- **Flat Structure:** Avoid deep nesting unless necessary
- **Logical Grouping:** Group files by purpose, not by date
- **Consistent Placement:** Always put similar files in same location
- **Clear Ownership:** Each file should have clear purpose and owner

## Common Patterns

### Creating New Features

1. **Assign ID:** Get next available F### or N### ID
2. **Create PRD:** `_prd_<feature-name>.md` (if separate PRD needed)
3. **Update Progress:** Add entry to `_progress.md`
4. **Create Task File:** `task_<ID>_<feature-name>.md`
5. **Create Specs:** `spec-design_<ID>_*.md` and `spec-dev_<ID>_*.md`

### Handling Issues

1. **Create Issue File:** `issue_<brief-description>.md`
2. **Link to Tasks:** Reference from relevant task files
3. **Track in Progress:** Update status in `_progress.md`
4. **Resolve and Document:** Update all related files when resolved

### Documentation Updates

1. **Follow Naming Conventions:** Use established patterns
2. **Update Cross-References:** Ensure all links remain valid
3. **Maintain Consistency:** Keep formatting and structure consistent
4. **Version Control:** Document changes and rationale

---

This naming convention ensures consistency, discoverability, and maintainability across all project documentation.
