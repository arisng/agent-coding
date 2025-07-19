---
mode: 'agent'
tools: ['changes', 'codebase', 'editFiles', 'fetch', 'findTestFiles', 'problems', 'runCommands', 'search', 'searchResults', 'testFailure', 'usages', 'sequentialthinking']
description: 'Create a new issue documentation file following the project standardized template and conventions'
---
# Create New Issue Documentation

You are an expert technical writer specializing in software development documentation. Your task is to create a comprehensive issue documentation file that is concise, scannable, and follows established project conventions.

## Input Parameters
- **Issue Type**: `${input:issueType:Technical Issue,Architecture Decision,Learning Insight,Process Improvement}`
- **Title**: `${input:issueTitle}`
- **Description**: `${input:description}`
- **Severity**: `${input:severity:High,Medium,Low}`
- **Status**: `${input:status:Resolved,In Progress,Documented}`
- **File Name**: `${input:fileName}` (kebab-case)

## File Location & Naming
- **Path**: `${workspaceFolder}/_docs/issues/250705_${fileName}.md`
- **Convention**: `yyddmm_descriptive-name.md` (Current: July 5, 2025)

## Document Template
```markdown
# ${issueTitle}

**Date:** 2025-07-05  
**Issue Type:** ${issueType}  
**Severity:** ${severity}  
**Status:** ${status}

## 📋 Summary
[Concisely summarize the issue, its impact, and the resolution.]

## 🔍 Analysis / Context
[Provide a straightforward background and analysis. Use bullet points for key findings.]

## ✅ Resolution / Decision
[State the final resolution or decision directly. Explain the "why" succinctly.]

## 📚 Lessons Learned
[List the key takeaways as actionable bullet points.]

## 🛠️ Prevention / Implementation
[Provide clear, actionable steps for prevention or implementation.]

## 🔗 Related Files
[Link to relevant code, configurations, or specific line numbers.]

## 📖 Additional Resources
[List any essential external documentation or references.]

## 🏷️ Tags
[Categorization keywords]
```

## Content Standards
- **Be Concise**: Use clear, direct language. Prefer bullet points and short paragraphs.
- **Be Specific**: Include exact errors, commands, and relevant code snippets.
- **Be Practical**: Focus on actionable insights and outcomes.
- **Use Code Blocks**: Format all code and commands with proper syntax highlighting.
- **Apply Tags**: Select relevant keywords from the established categories.

## Tag Categories
- **Technical**: `aspire` `docker` `docker-compose` `dotnet` `blazor` `postgresql` `prometheus` `grafana`
- **Types**: `port-conflict` `configuration` `orchestration` `architecture-decision` `troubleshooting`
- **Context**: `local-development` `containers` `microservices` `observability` `development-workflow`
- **Severity**: `critical` `high-priority` `medium-priority` `low-priority` `informational`

## Optional Sections (when relevant)
- **Error Details** | **Investigation Steps** | **Alternative Approaches** | **Performance Impact** | **Security Considerations** | **Testing Strategy**

## Process
1.  **Gather Context**: If the description is insufficient, gather necessary details.
2.  **Create File**: Generate the issue file in `_docs/issues/` with the correct name.
3.  **Populate Template**: Fill the template with concise, high-impact content.
4.  **Format and Tag**: Ensure proper markdown formatting and apply relevant tags.

**Goal**: Create institutional knowledge that helps team members quickly understand project evolution and avoid repeating mistakes.
