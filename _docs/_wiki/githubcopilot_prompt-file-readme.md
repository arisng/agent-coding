# All about Prompt files in Github Copilot

## Settings

**Setting**: `setting(chat.promptFilesLocations)`

Prompt files describe a standalone, complete chat request, including the prompt text, chat mode, and tools to use. Prompt files are useful for creating reusable chat requests for common tasks. For example, you can add a prompt file for creating a front-end component, or to perform a security review.

Prompt files use the `.prompt.md` file suffix. They can be located in your user data folder or in the workspace. The `vscode://settings/chat.promptFilesLocations` setting lists the folder where prompt files are looked for.

### Workspace prompt file location

1. Run the Chat: New Prompt File command from the Command Palette (Ctrl+Shift+P).
2. Choose the location where the prompt file should be created. By default, only the `.github/prompts` folder is available. Add more prompt folders for your workspace with the `vscode://settings/chat.promptFilesLocations` setting.

### User prompt file location

1. Select the Chat: New Prompt File command from the Command Palette (Ctrl+Shift+P).
2. Select User Data Folder as the location for the prompt file.
3. If you use multiple VS Code profiles, the prompt file is created in the current profile's user data folder.

## How to create a prompt file

To create a prompt file, use the **Chat: New Prompt File...** command from the Command Palette.

## How to run a prompt file

There are several ways to run a prompt file:

* Type `/` in the chat input field, followed by the prompt file name.
* Open the prompt file in an editor and press the 'Play' button in the editor tool bar. This enables you to quickly iterate on the prompt and run it without having to switch back to the Chat view.
* Use the **Chat: Run Prompt File...** command from the Command Palette.
* Pass additional information in the chat input field. For example, `/create-react-form: formName=MyForm`

## Syntax

Prompt files can have the following Front Matter metadata headers to indicate how they should be run:

* `mode`: the chat mode to use when invoking the prompt (`ask`, `edit`, or `agent` mode).
* `tools`: if the `mode` is `agent`, the list of tools that are available for the prompt.

The following example shows a prompt file for generating release notes, that runs in agent mode, and can use a set of tools:

```md
---
mode: 'agent'
tools: ['getCurrentMilestone', 'getReleaseFeatures', 'file_search', 'semantic_search', 'read_file', 'insert_edit_into_file', 'create_file', 'replace_string_in_file', 'fetch_webpage', 'vscode_search_extensions_internal']
---
Generate release notes for the features I worked in the current release and update them in the release notes file. Use [release notes writing instructions file](.github/instructions/release-notes-writing.instructions.md) as a guide.
```

Learn more about [prompt files](https://code.visualstudio.com/docs/copilot/copilot-customization#_prompt-files-experimental) in our documentation.

Can-do list:

* can reference other .prompt.md files to create a hierarchy of prompts
* can reference other prompt files or instruction files by using Markdown links (use relative paths to reference these files)
* can reference variables by using the ${variableName} syntax
* can reference the following variables:
  * Workspace variables - ${workspaceFolder}, ${workspaceFolderBasename}
  * Selection variables - ${selection}, ${selectedText}
  * File context variables - ${file}, ${fileBasename}, ${fileDirname}, ${fileBasenameNoExtension}
  * Input variables - ${input:variableName}, ${input:variableName:placeholder} (pass values to the prompt from the chat input field)

## Sample prompt files

### Prompt for a reusable task to generate a React form

```md
---
mode: 'agent'
tools: ['githubRepo', 'codebase']
description: 'Generate a new React form component'
---
Your goal is to generate a new React form component based on the templates in #githubRepo contoso/react-templates.

Ask for the form name and fields if not provided.

Requirements for the form:
* Use form design system components: [design-system/Form.md](../docs/design-system/Form.md)
* Use `react-hook-form` for form state management:
* Always define TypeScript types for your form data
* Prefer *uncontrolled* components using register
* Use `defaultValues` to prevent unnecessary rerenders
* Use `yup` for validation:
* Create reusable validation schemas in separate files
* Use TypeScript types to ensure type safety
* Customize UX-friendly validation rules
```

### Prompt for performing a security review of a REST API

```md
---
mode: 'edit'
description: 'Perform a REST API security review'
---
Perform a REST API security review:

* Ensure all endpoints are protected by authentication and authorization
* Validate all user inputs and sanitize data
* Implement rate limiting and throttling
* Implement logging and monitoring for security events

```
