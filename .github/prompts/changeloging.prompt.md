---
mode: 'agent'
tools: ['changes', 'codebase', 'editFiles', 'fetch', 'problems', 'runCommands', 'search', 'searchResults', 'terminalLastCommand', 'terminalSelection', 'usages', 'vscodeAPI']
description: 'Generate a changelog file for daily or weekly updates, always overriding the existing file.'
---


# Generate Changelog (Daily, Weekly, or Specific Date)

Generate a changelog file in the project, allowing the user to choose between daily, weekly, or a specific date:

- **Daily**: Generate changelog for today (current date)
- **Weekly**: Generate changelog for the current week (Monday–Sunday)
- **Specific Date**: Generate changelog for a user-specified date

## Requirements
- Prompt the user to select changelog type: `${input:changelogType:daily,weekly,specific}`
- For daily, use today's date for the changelog
- For weekly, use the current week (Monday–Sunday)
- For specific, prompt the user to enter a date: `${input:changelogDate:YYYY-MM-DD}` and use that date for the changelog
- Always override the existing changelog file if it exists
- The changelog file must be saved in the `/_docs/changelogs` folder
- File naming convention:
  - For daily or specific date: `yymmdd_changelog.md` (e.g., `250722_changelog.md` for July 22, 2025)
  - For weekly: `yymmdd-dd_changelog.md` (e.g., `250721-27_changelog.md` for the week of July 21–27, 2025)

## Instructions
1. Ask the user to choose between daily, weekly, or specific date changelog
2. If specific date is selected, prompt for the date in YYYY-MM-DD format
3. Gather all relevant changes for the selected period or date
4. Format the changelog clearly, including date or week range
5. Save the changelog file in the `/_docs/changelogs` folder using the correct naming convention
6. Overwrite the existing changelog file with the new content if it exists

## Output Format
- The changelog file must use the following structure:
  - Date (for daily) or week range (for weekly)
  - For each date or week, strictly group all changes under these explicit type headings (even if some groups are empty):
    - `### Added`
    - `### Changed`
    - `### Fixed`
    - `### Removed`
    - `### Deprecated`
    - `### Security`
  - List each change as a bullet point under the appropriate heading. Do not use inline type labels (e.g., "**Feature:**")—only use the headings for grouping.
  - If a group has no changes, include the heading with "_No changes_" or leave it empty for clarity.

## Error Handling
- If the changelog type is unclear, prompt the user again
- If no changes are found for the period, indicate this in the changelog file