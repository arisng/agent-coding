# All about Prompt files in Github Copilot

## Settings

**Setting**: `setting(chat.promptFilesLocations)`

Prompt files describe a standalone, complete chat request, including the prompt text, chat mode, and tools to use. Prompt files are useful for creating reusable chat requests for common tasks. For example, you can add a prompt file for creating a front-end component, or to perform a security review.

Prompt files use the `.prompt.md` file suffix. They can be located in your user data folder or in the workspace. The `setting(chat.promptFilesLocations)` setting lists the folder where prompt files are looked for.

## How to create a prompt file

To create a prompt file, use the **Chat: New Prompt File...** command from the Command Palette.

## How to run a prompt file

There are several ways to run a prompt file:

* Type `/` in the chat input field, followed by the prompt file name.
  ![Screenshot that shows running a prompt in the Chat view with a slash command.](images/1_100/run-prompt-as-slash-command.png)

* Open the prompt file in an editor and press the 'Play' button in the editor tool bar. This enables you to quickly iterate on the prompt and run it without having to switch back to the Chat view.
  ![Screenshot that shows running a prompt by using the play button in the editor.](images/1_100/run-prompt-from-play-button.png)

* Use the **Chat: Run Prompt File...** command from the Command Palette.

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
