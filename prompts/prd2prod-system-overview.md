# PRD2Prod Specialized Prompt System

This document provides an overview of the complete PRD2Prod specialized prompt system for efficient workflow execution.

## System Overview

The PRD2Prod workflow has been broken down into 8 specialized prompt files, each focused on a specific aspect of the development workflow:

## Available Specialists

### Step 0: Workflow Coordinator
**File**: `prd2prod-step0-coordinator.md`
**Purpose**: Routes users to appropriate step specialists and manages workflow coordination
**Use When**: Starting a new project or unsure which step you need

### Step 1: PRD Creation
**File**: `prd2prod-step1-prd-creation.md`  
**Purpose**: Creates comprehensive Product Requirements Documents
**Prerequisites**: None (starting point)
**Use When**: Defining requirements and project scope

### Step 2: Progress Tracking
**File**: `prd2prod-step2-progress-tracking.md`
**Purpose**: Sets up progress monitoring and milestone tracking
**Prerequisites**: Completed PRD
**Use When**: Need to establish project tracking and reporting

### Step 3: Design Specifications
**File**: `prd2prod-step3-design-specs.md`
**Purpose**: Creates detailed system and UX design specifications
**Prerequisites**: PRD, Progress Tracking
**Use When**: Translating requirements into design decisions

### Step 4: Development Specifications  
**File**: `prd2prod-step4-dev-specs.md`
**Purpose**: Creates technical implementation specifications
**Prerequisites**: PRD, Progress Tracking, Design Specs
**Use When**: Defining technical architecture and implementation details

### Step 5: Task Breakdown
**File**: `prd2prod-step5-task-breakdown.md`
**Purpose**: Converts specifications into actionable development tasks
**Prerequisites**: PRD, Progress Tracking, Design Specs, Dev Specs
**Use When**: Planning implementation and creating work items

### Step 6: Implementation
**File**: `prd2prod-step6-implementation.md`
**Purpose**: Executes development tasks and builds the solution
**Prerequisites**: All previous steps completed
**Use When**: Ready to write code and build features

### Step 7: Testing & Deployment
**File**: `prd2prod-step7-testing-deployment.md`
**Purpose**: Comprehensive testing and production deployment
**Prerequisites**: All previous steps including implementation
**Use When**: Implementation is complete and ready for testing/deployment

## Key Features

### Specialized Focus
- Each prompt is laser-focused on one workflow step
- Reduced context and faster inference
- Step-specific expertise and guidance

### Template Integration
- Each specialist references appropriate `prd2prod_template-*` files
- Ensures consistency across all deliverables
- Built-in quality validation

### Prerequisite Validation
- Each step validates upstream deliverables are complete
- Maintains workflow integrity and traceability
- Prevents skipping critical workflow steps

### Quality Assurance
- Step-specific quality checklists
- Template compliance verification
- Handoff preparation for next steps

## Usage Patterns

### Linear Workflow (Recommended)
Start with Step 0 Coordinator → Step 1 → Step 2 → ... → Step 7

### Jump to Specific Step
Use any specialist directly if you know exactly which step you need

### Resume Workflow
Use Step 0 Coordinator to assess current state and resume at appropriate step

## Benefits

1. **Efficiency**: Faster inference with focused, smaller prompts
2. **Modularity**: Use any step independently or in sequence  
3. **Consistency**: All specialists follow same templates and standards
4. **Quality**: Built-in validation and quality checks
5. **Flexibility**: Jump to any step or follow complete workflow

## Getting Started

1. **For new projects**: Start with `prd2prod-step0-coordinator.md`
2. **For specific needs**: Choose the appropriate step specialist
3. **For workflow assessment**: Use coordinator to determine current state

Each specialist will verify required documentation and templates before proceeding, ensuring workflow integrity and quality standards.
