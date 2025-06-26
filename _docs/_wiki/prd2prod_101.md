# PRD to Production Guidelines

A comprehensive system for managing product development from requirements to production deployment.

- [1. Quick Navigation](#1-quick-navigation)
- [2. Overview](#2-overview)
- [3. Getting Started](#3-getting-started)
  - [3.1. For New Projects](#31-for-new-projects)
  - [3.2. For Existing Projects](#32-for-existing-projects)
- [4. Key Principles](#4-key-principles)
  - [4.1. Small, Actionable Scopes](#41-small-actionable-scopes)
  - [4.2. Linear Workflow](#42-linear-workflow)
  - [4.3. Upstream-Only Referencing](#43-upstream-only-referencing)
  - [4.4. Continuous Feedback](#44-continuous-feedback)
- [5. Process Flow Diagram](#5-process-flow-diagram)
- [6. Quick Reference](#6-quick-reference)
  - [6.1. File Types and Purposes](#61-file-types-and-purposes)
  - [6.2. Status Values](#62-status-values)
- [7. Templates and Examples](#7-templates-and-examples)
- [8. Support and Troubleshooting](#8-support-and-troubleshooting)
  - [8.1. Common Issues](#81-common-issues)
  - [8.2. Best Practices](#82-best-practices)

## 1. Quick Navigation

- **[PRD Guidelines](./prd2prod_guide-prd.md)** - How to create effective Product Requirements Documents
- **[Workflow Guide](./prd2prod_guide-workflow.md)** - Step-by-step development process and examples
- **[Naming Conventions](./prd2prod_guide-naming.md)** - File organization and naming standards
- **[Content Structure](./prd2prod_guide-structure.md)** - Templates and content formatting guidelines

## 2. Overview

This system provides a repeatable, traceable approach to software development that ensures:

- **Actionable Scope**: Small, deliverable increments that provide clear value
- **Clear Traceability**: Every piece of work maps back to requirements and progress tracking
- **Systematic Documentation**: Consistent structure across all project artifacts
- **Feedback Integration**: Continuous improvement through production feedback loops

## 3. Getting Started

### 3.1. For New Projects

1. **Start with Requirements**: Create a focused PRD using our [PRD Guidelines](./prd2prod_guide-prd.md)
2. **Follow the Workflow**: Use the [Workflow Guide](./prd2prod_guide-workflow.md) to move from requirements to implementation
3. **Organize Your Files**: Apply [Naming Conventions](./prd2prod_guide-naming.md) for consistency
4. **Structure Your Content**: Use [Content Structure](./prd2prod_guide-structure.md) templates

### 3.2. For Existing Projects

1. **Assess Current State**: Review existing documentation against our guidelines
2. **Prioritize Gaps**: Identify missing PRDs, unclear workflows, or inconsistent naming
3. **Incrementally Adopt**: Apply guidelines to new work while gradually improving existing documentation
4. **Establish Feedback Loops**: Implement continuous improvement processes

## 4. Key Principles

### 4.1. Small, Actionable Scopes

- PRDs should be completable in 1-5 days
- Each PRD addresses a single feature, enhancement, or fix
- Dependencies are minimized or clearly documented

### 4.2. Linear Workflow

- High-level overview → Progress index → Design specs → Development specs → Tasks → Issues/Logs
- Each step builds context for the next
- Consistent process regardless of task complexity

### 4.3. Upstream-Only Referencing

- PRDs only reference other PRDs and progress files
- Downstream files reference upstream files, not vice versa
- Clear separation of concerns and dependency management

### 4.4. Continuous Feedback

- Production issues feed back into the workflow
- User feedback is systematically captured and prioritized
- Regular retrospectives improve the process itself

## 5. Process Flow Diagram

```
User Feedback/Requirements
         ↓
    [Create PRD] ←──────────────┐
         ↓                     │
   [Update Progress]           │
         ↓                     │
   [Design Specs]              │
         ↓                     │ Feedback
   [Development Specs]         │ Loop
         ↓                     │
   [Break Down Tasks]          │
         ↓                     │
   [Implementation]            │
         ↓                     │
   [Testing & Review]          │
         ↓                     │
   [Production Deployment] ────┘
```

## 6. Quick Reference

### 6.1. File Types and Purposes

| Prefix | Purpose | Example |
|--------|---------|---------|
| `_` | Core documents (PRD, Progress, Logs) | `_prd.md`, `_progress.md` |
| `task_` | Feature-specific task breakdowns | `task_F001_user-auth.md` |
| `spec-design_` | Conceptual design and architecture | `spec-design_F001_auth-flow.md` |
| `spec-dev_` | Implementation details and code samples | `spec-dev_F001_auth-api.md` |
| `issue_` | Problem documentation and solutions | `issue_login-timeout.md` |
| `log_` | Daily progress tracking | `log_250626.md` |

### 6.2. Status Values

- **Not Started**: Work has not begun
- **In Progress**: Work is actively being done  
- **Blocked**: Progress halted due to dependencies
- **Review**: Work complete, under review
- **Done**: Work fully completed and accepted
- **Deferred**: Work postponed for future consideration

## 7. Templates and Examples

- **[PRD Template](./prd2prod_template-prd.md)** - Copy-paste ready PRD template
- **[Example Workflow](./prd2prod_example1.md)** - Complete end-to-end example
- **Progress File Examples** - See [Content Structure](./prd2prod_guide-structure.md)

## 8. Support and Troubleshooting

### 8.1. Common Issues

- **Scope Too Large**: Break into multiple smaller PRDs
- **Unclear Dependencies**: Map dependencies explicitly in PRD
- **Inconsistent Naming**: Apply naming conventions systematically
- **Lost Context**: Follow the linear workflow order

### 8.2. Best Practices

- Review PRDs regularly to ensure they remain relevant
- Use the checklist before finalizing any PRD
- Link related PRDs to show inheritance and dependencies
- Keep documentation up-to-date as work progresses

---

*This system is designed to scale from individual developers to large teams while maintaining clarity and traceability at every step.*
