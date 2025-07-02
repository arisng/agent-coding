# PRD2Prod Comprehensive Guide

A complete guide to the PRD2Prod methodology and specialized prompt system for efficient product development from requirements to production deployment.

## Table of Contents

- [1. Quick Navigation](#1-quick-navigation)
- [2. System Overview](#2-system-overview)
- [3. Workflow Structure](#3-workflow-structure)
- [4. Key Principles](#4-key-principles)
- [5. Specialized Prompt System](#5-specialized-prompt-system)
- [6. Usage Patterns](#6-usage-patterns)
- [7. Process Flow](#7-process-flow)
- [8. File Organization](#8-file-organization)
- [9. Templates and Examples](#9-templates-and-examples)
- [10. Benefits](#10-benefits)
- [11. Getting Started](#11-getting-started)
- [12. Support and Troubleshooting](#12-support-and-troubleshooting)

## 1. Quick Navigation

- **[PRD Guidelines](./prd2prod_guide-prd.md)** - How to create effective Product Requirements Documents
- **[Workflow Guide](./prd2prod_guide-workflow.md)** - Step-by-step development process and examples
- **[Naming Conventions](./prd2prod_guide-naming.md)** - File organization and naming standards
- **[Content Structure](./prd2prod_guide-structure.md)** - Templates and content formatting guidelines

## 2. System Overview

The PRD2Prod system provides a repeatable, traceable approach to software development that ensures:

- **Actionable Scope**: Small, deliverable increments that provide clear value
- **Clear Traceability**: Every piece of work maps back to requirements and progress tracking
- **Systematic Documentation**: Consistent structure across all project artifacts
- **Feedback Integration**: Continuous improvement through production feedback loops
- **Simplicity Focus**: Minimal code impact and easy maintenance
- **Flexible Workflow**: Mandatory and optional steps based on project complexity

The workflow has been broken down into 8 specialized prompt files, each focused on a specific aspect of the development workflow with emphasis on simplicity, minimal code impact, and easy maintenance.

## 3. Workflow Structure

### 3.1. Mandatory Steps

- **Step 1**: PRD Creation (Required starting point)
- **Step 2**: Progress Tracking (Required for project management)
- **Step 5**: Task Breakdown (Required for implementation planning)
- **Step 6**: Coding (Required for actual development)

### 3.2. Optional Steps

- **Step 3**: Design Specifications (Optional, specialized for frontend/backend)
- **Step 4**: Development Specifications (Optional, specialized for frontend/backend)
- **Step 7**: Testing & Deployment (Optional for comprehensive validation)

### 3.3. Step Dependencies

```text
Step 0 (Coordinator) → Step 1 (PRD) → Step 2 (Progress)
                                          ↓
Step 3 (Design Specs) ← ← ← ← ← ← ← ← ← ← ┘ (Optional)
          ↓
Step 4 (Dev Specs) ← ← ← ← ← ← ← ← ← ← ← ← ← (Optional)
          ↓
Step 5 (Task Breakdown) ← ← ← ← ← ← ← ← ← ← ← (Mandatory)
          ↓
Step 6 (Coding) ← ← ← ← ← ← ← ← ← ← ← ← ← ← ← (Mandatory)
          ↓
Step 7 (Testing & Deploy) ← ← ← ← ← ← ← ← ← ← (Optional)
```

## 4. Key Principles

### 4.1. Small, Actionable Scopes

- PRDs should be completable in 1-5 days
- Each PRD addresses a single feature, enhancement, or fix
- Dependencies are minimized or clearly documented
- Avoid massive or complex changes

### 4.2. Linear Workflow with Flexibility

- High-level overview → Progress index → Design specs → Development specs → Tasks → Implementation
- Each step builds context for the next
- Consistent process regardless of task complexity
- Optional steps can be skipped for simpler projects

### 4.3. Upstream-Only Referencing

- PRDs only reference other PRDs and progress files
- Downstream files reference upstream files, not vice versa
- Clear separation of concerns and dependency management

### 4.4. Continuous Feedback

- Production issues feed back into the workflow
- User feedback is systematically captured and prioritized
- Regular retrospectives improve the process itself

### 4.5. Simplicity and Maintainability

- Every task should impact as little code as possible
- Focus on easy-to-maintain solutions
- Prioritize simple, isolated changes

## 5. Specialized Prompt System

### 5.1. Available Specialists

#### Step 0: Workflow Coordinator

**File**: `prd2prod-step0-coordinator.md`
**Purpose**: Routes users to appropriate step specialists and manages workflow coordination
**Use When**: Starting a new project or unsure which step you need

#### Step 1: PRD Creation (Mandatory)

**File**: `prd2prod-step1-prd-creation.md`
**Purpose**: Creates comprehensive Product Requirements Documents
**Prerequisites**: None (starting point)
**Use When**: Defining requirements and project scope

#### Step 2: Progress Tracking (Mandatory)

**File**: `prd2prod-step2-progress-tracking.md`
**Purpose**: Sets up progress monitoring and milestone tracking
**Prerequisites**: Completed PRD
**Use When**: Need to establish project tracking and reporting

#### Step 3: Design Specifications (Optional)

**File**: `prd2prod-step3-design-specs.md`
**Purpose**: Creates detailed system and UX design specifications (frontend/backend specialized)
**Prerequisites**: PRD, Progress Tracking
**Use When**: Translating requirements into design decisions
**Scope**: Specialized for frontend or backend with tech stack placeholders

#### Step 4: Development Specifications (Optional)

**File**: `prd2prod-step4-dev-specs.md`
**Purpose**: Creates technical implementation specifications (frontend/backend specialized)
**Prerequisites**: PRD, Progress Tracking, Design Specs (if used)
**Use When**: Defining technical architecture and implementation details
**Scope**: Specialized for frontend or backend with tech stack placeholders (frameworks, libraries, packages, patterns)

#### Step 5: Task Breakdown (Mandatory)

**File**: `prd2prod-step5-task-breakdown.md`
**Purpose**: Converts specifications into actionable development tasks with minimal code impact
**Prerequisites**: PRD, Progress Tracking, optional Design/Dev Specs
**Use When**: Planning implementation and creating simple, maintainable work items
**Focus**: Small, isolated changes that are easy to maintain

#### Step 6: Coding (Mandatory)

**File**: `prd2prod-step6-implementation.md`
**Purpose**: Executes development tasks with focus on simplicity and minimal code changes
**Prerequisites**: All mandatory steps completed
**Use When**: Ready to write code and build features
**Approach**: Avoid massive or complex changes, prioritize maintainability

#### Step 7: Testing & Deployment (Optional)

**File**: `prd2prod-step7-testing-deployment.md`
**Purpose**: Comprehensive testing and production deployment
**Prerequisites**: All mandatory steps including coding
**Use When**: Implementation is complete and ready for testing/deployment

### 5.2. System Features

#### Specialized Focus

- Each prompt is laser-focused on one workflow step
- Reduced context and faster inference
- Step-specific expertise and guidance
- Emphasis on simplicity and minimal code impact

#### Mandatory vs Optional Steps

- **Mandatory steps (1, 2, 5, 6)**: Core workflow that must be completed
- **Optional steps (3, 4, 7)**: Can be skipped for simpler projects
- Flexible workflow adaptation based on project complexity

#### Frontend/Backend Specialization

- Steps 3 & 4 can be specialized for frontend or backend development
- Tech stack placeholders for frameworks, libraries, packages, and patterns
- User provides specific technology choices as input

#### Template Integration

- Each specialist references appropriate `prd2prod_template-*` files
- Ensures consistency across all deliverables
- Built-in quality validation

#### Prerequisite Validation

- Each step validates upstream deliverables are complete
- Mandatory steps must be completed before coding
- Optional steps can be skipped based on project needs
- Maintains workflow integrity and traceability

#### Quality Assurance

- Step-specific quality checklists
- Template compliance verification
- Focus on maintainable, simple solutions
- Handoff preparation for next steps

## 6. Usage Patterns

### 6.1. Minimal Workflow (Mandatory Only)

Start with Step 0 Coordinator → Step 1 → Step 2 → Step 5 → Step 6

**Best for**: Simple features, bug fixes, small enhancements

### 6.2. Linear Workflow (Full)

Start with Step 0 Coordinator → Step 1 → Step 2 → Step 3 → Step 4 → Step 5 → Step 6 → Step 7

**Best for**: Complex features, new systems, critical deployments

### 6.3. Jump to Specific Step

Use any specialist directly if you know exactly which step you need

**Best for**: Experienced users, specific workflow needs

### 6.4. Resume Workflow

Use Step 0 Coordinator to assess current state and resume at appropriate step

**Best for**: Returning to interrupted work, team handoffs

## 7. Process Flow

```text
User Feedback/Requirements
         ↓
[Step 0: Coordinator] ←──────────────┐
         ↓                           │
[Step 1: PRD Creation] ←─────────────┤
         ↓                           │
[Step 2: Progress Tracking]          │
         ↓                           │
[Step 3: Design Specs] (Optional)    │ Feedback
         ↓                           │ Loop
[Step 4: Dev Specs] (Optional)       │
         ↓                           │
[Step 5: Task Breakdown]             │
         ↓                           │
[Step 6: Coding]                     │
         ↓                           │
[Step 7: Testing & Deploy] (Optional)│
         ↓                           │
[Production Deployment] ─────────────┘
```

## 8. File Organization

### 8.1. File Types and Purposes

| Prefix | Purpose | Example |
|--------|---------|---------|
| `_` | Core documents (PRD, Progress, Logs) | `_prd.md`, `_progress.md` |
| `task_` | Feature-specific task breakdowns | `task_F001_user-auth.md` |
| `spec-design_` | Conceptual design and architecture | `spec-design_F001_auth-flow.md` |
| `spec-dev_` | Implementation details and code samples | `spec-dev_F001_auth-api.md` |
| `issue_` | Problem documentation and solutions | `issue_login-timeout.md` |
| `log_` | Daily progress tracking | `log_250626.md` |

### 8.2. Status Values

- **Not Started**: Work has not begun
- **In Progress**: Work is actively being done
- **Blocked**: Progress halted due to dependencies
- **Review**: Work complete, under review
- **Done**: Work fully completed and accepted
- **Deferred**: Work postponed for future consideration

## 9. Templates and Examples

- **[PRD Template](./prd2prod_template-prd.md)** - Copy-paste ready PRD template
- **[Progress Template](./prd2prod_template-progress.md)** - Progress tracking template
- **[Task Template](./prd2prod_template-task.md)** - Task breakdown template
- **[Design Spec Template](./prd2prod_template-spec-design.md)** - Design specification template
- **[Dev Spec Template](./prd2prod_template-spec-dev.md)** - Development specification template
- **[Example Workflow](./prd2prod_example1.md)** - Complete end-to-end example

## 10. Benefits

1. **Efficiency**: Faster inference with focused, smaller prompts
2. **Modularity**: Use any step independently or in sequence
3. **Consistency**: All specialists follow same templates and standards
4. **Quality**: Built-in validation and quality checks
5. **Flexibility**: Jump to any step or follow complete workflow
6. **Simplicity**: Focus on minimal code changes and easy maintenance
7. **Adaptability**: Mandatory vs optional steps based on project complexity
8. **Specialization**: Frontend/backend focus with tech stack customization
9. **Traceability**: Clear documentation and dependency tracking
10. **Scalability**: Works for individual developers to large teams

## 11. Getting Started

### 11.1. For New Projects

1. **Start with the Coordinator**: Use `prd2prod-step0-coordinator.md`
2. **Choose Your Workflow**:
   - **Minimal**: Complete mandatory steps only (1 → 2 → 5 → 6)
   - **Comprehensive**: Include optional steps as needed (1 → 2 → 3 → 4 → 5 → 6 → 7)
3. **Apply Standards**: Use [Naming Conventions](./prd2prod_guide-naming.md) and [Content Structure](./prd2prod_guide-structure.md)

### 11.2. For Existing Projects

1. **Assess Current State**: Review existing documentation against our guidelines
2. **Prioritize Gaps**: Identify missing PRDs, unclear workflows, or inconsistent naming
3. **Incrementally Adopt**: Apply guidelines to new work while gradually improving existing documentation
4. **Establish Feedback Loops**: Implement continuous improvement processes

### 11.3. For Specific Needs

- **Bug fixes**: Use minimal workflow (Steps 1, 2, 5, 6)
- **New features**: Consider full workflow with design specs
- **Architecture changes**: Include development specifications
- **Critical releases**: Include testing & deployment step

## 12. Support and Troubleshooting

### 12.1. Common Issues

- **Scope Too Large**: Break into multiple smaller PRDs
- **Unclear Dependencies**: Map dependencies explicitly in PRD
- **Inconsistent Naming**: Apply naming conventions systematically
- **Lost Context**: Follow the linear workflow order
- **Complex Changes**: Break down into smaller, simpler tasks

### 12.2. Best Practices

- Review PRDs regularly to ensure they remain relevant
- Use the checklist before finalizing any PRD
- Link related PRDs to show inheritance and dependencies
- Keep documentation up-to-date as work progresses
- Prioritize simple, maintainable solutions
- Use optional steps judiciously based on project complexity

### 12.3. Quality Checklist

Before proceeding from any step:

- [ ] All prerequisites are met
- [ ] Documentation follows templates
- [ ] Scope is appropriately sized (1-5 days)
- [ ] Dependencies are clearly identified
- [ ] Next steps are prepared
- [ ] Quality standards are met

---

*This comprehensive system is designed to scale from individual developers to large teams while maintaining clarity, simplicity, and traceability at every step. The specialized prompt system enables efficient execution with minimal complexity and maximum maintainability.*
