---
mode: 'agent'
# tools: ['codebase', 'searchResults', 'usages']
description: 'Generate C# unit tests from test cases'
---
# C# Unit Test Generator

Your goal is to generate C# unit tests based on provided test cases and specifications.

## Required Information

- Test Cases File: ${input:testCasesFile:Path to test cases markdown file}
- Specifications File (Optional): ${input:specFile:Optional path to specifications/rules file}
- Target Scope (Optional): ${input:targetScope:Specific test group or section to focus on}

If no target scope is provided, I'll code test cases sequentially by headline from the test cases file, focusing on one section at a time.

## Testing Standards

Follow all conventions in [topic-unittest.instructions.md](../instructions/topic-unittest.instructions.md) and [topic-aspnetcore.instructions.md](../instructions/topic-aspnetcore.instructions.md), including:

- Test method naming: Use `MethodName_TestCondition_ExpectedResult` or `When_Action_Given_Condition_Then_ExpectedResult`
- Code style:
  - File scoped namespaces
  - Use of regions for organization
  - Explicit type declarations
  - Private fields: `_fieldName`
  - Public properties: `PropertyName`
- Empty tests: Implement to fail with `Assert.Fail("Test not yet implemented");`

## Libraries

- Use xUnit
- Follow AAA (Arrange-Act-Assert) pattern
- Use Moq for mocking dependencies when needed