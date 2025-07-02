---
mode: 'agent'
# tools: ['codebase', 'searchResults', 'usages']
description: 'Writing test cases for a feature into a markdown file.'
---

Your goal is to write test cases in markdown for `{{FEATURE}}`, based on the details provided in `{{SOURCE}}`.
Ask user for {{DESTINATION}} file path if not provided and ensure the output is in Markdown format.

Follow a structure similar to the provided example test case document. Each test case should clearly define:
1. Test Case ID: A unique identifier (e.g., CATEGORY_ACTION_NNN).
2. Description: A concise summary of the test's purpose.
3. Prerequisites/Input: The initial state, conditions, or specific data required before the test action.
4. Action(s): The specific steps or operations performed during the test.
5. Expected Outcome: The anticipated result, state changes, or outputs after the action(s).
6. Rules Referenced: (Optional) Specific rules, requirements, or specifications from `{{SOURCE}}` that this test case verifies.

Organize test cases into logical sections if applicable (e.g., Initial State, Core Functionality, Edge Cases, Error Handling).
Focus on creating clear, textual descriptions for diverse test scenarios. Do not write executable code.
The output must be in Markdown format.
