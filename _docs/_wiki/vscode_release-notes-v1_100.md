---
Order: 109
TOCTitle: April 2025
PageTitle: Visual Studio Code April 2025
MetaDescription: Learn what is new in the Visual Studio Code April 2025 Release (1.100)
MetaSocialImage: 1_100/release-highlights.png
Date: 2025-05-08
DownloadVersion: 1.100.0
---
# April 2025 (version 1.100)

_Release date: May 8, 2025_

- [April 2025 (version 1.100)](#april-2025-version-1100)
  - [Chat](#chat)
    - [Prompt and instructions files](#prompt-and-instructions-files)
      - [Instructions files](#instructions-files)
      - [Prompt files](#prompt-files)
      - [Improvements and notes](#improvements-and-notes)
    - [Faster agent mode edits](#faster-agent-mode-edits)
    - [Base model in chat](#base-model-in-chat)
    - [Search code of a GitHub repository with the `#githubRepo` tool](#search-code-of-a-github-repository-with-the-githubrepo-tool)
    - [Find Marketplace extensions with the extensions tool](#find-marketplace-extensions-with-the-extensions-tool)
    - [Improvements to the web page fetch tool](#improvements-to-the-web-page-fetch-tool)
    - [Chat input improvements](#chat-input-improvements)
    - [Chat mode keyboard shortcuts](#chat-mode-keyboard-shortcuts)
    - [Autofix diagnostics from agent mode edits](#autofix-diagnostics-from-agent-mode-edits)
    - [Handling of undo and manual edits in agent mode](#handling-of-undo-and-manual-edits-in-agent-mode)
    - [Conversation summary and prompt caching](#conversation-summary-and-prompt-caching)
    - [MCP support for Streamable HTTP](#mcp-support-for-streamable-http)
    - [MCP support for image output](#mcp-support-for-image-output)
    - [Enhanced input, output, and progress from MCP servers](#enhanced-input-output-and-progress-from-mcp-servers)
    - [MCP config generation uses inputs](#mcp-config-generation-uses-inputs)
    - [Inline chat V2 (Preview)](#inline-chat-v2-preview)
    - [Select and attach UI elements to chat (Experimental)](#select-and-attach-ui-elements-to-chat-experimental)
    - [Create and launch tasks in agent mode (Experimental)](#create-and-launch-tasks-in-agent-mode-experimental)
  - [Accessibility](#accessibility)
    - [Merge editor improvements](#merge-editor-improvements)
    - [Next edit suggestion enhancements](#next-edit-suggestion-enhancements)
    - [Review Copilot user requests from the accessible view](#review-copilot-user-requests-from-the-accessible-view)
    - [Unique accessibility sounds](#unique-accessibility-sounds)
  - [Editor Experience](#editor-experience)
    - [Floating window modes](#floating-window-modes)
    - [Secondary Side Bar default visibility](#secondary-side-bar-default-visibility)
    - [Mandatory extension signature verification](#mandatory-extension-signature-verification)
    - [Learn more links for malicious extensions](#learn-more-links-for-malicious-extensions)
    - [Prevent installation of Copilot Chat pre-release versions in VS Code stable](#prevent-installation-of-copilot-chat-pre-release-versions-in-vs-code-stable)
    - [Command to open a view without focus](#command-to-open-a-view-without-focus)
    - [Semantic text search with keyword suggestions (Experimental)](#semantic-text-search-with-keyword-suggestions-experimental)
  - [Code Editing](#code-editing)
    - [New Next Edit Suggestions (NES) model](#new-next-edit-suggestions-nes-model)
    - [Import suggestions](#import-suggestions)
    - [Generate alt text in HTML or Markdown](#generate-alt-text-in-html-or-markdown)
    - [Variable line heights](#variable-line-heights)
  - [Notebooks](#notebooks)
    - [Find and replace history persistence](#find-and-replace-history-persistence)
    - [Drag and drop cell outputs to chat](#drag-and-drop-cell-outputs-to-chat)
    - [Notebook tools for agent mode](#notebook-tools-for-agent-mode)
      - [Run cell](#run-cell)
      - [Get kernel state](#get-kernel-state)
      - [List/Install packages](#listinstall-packages)
  - [Source Control](#source-control)
    - [Quick diff decorations for staged changes](#quick-diff-decorations-for-staged-changes)
  - [Debugging](#debugging)
    - [Disassembly view context menu](#disassembly-view-context-menu)
    - [JavaScript debugger Network view](#javascript-debugger-network-view)
  - [Languages](#languages)
    - [Show browser support for CSS and HTML](#show-browser-support-for-css-and-html)
    - [Default syntax highlighting for `.*.env` files](#default-syntax-highlighting-for-env-files)
    - [Expandable hovers for JavaScript and TypeScript (Experimental)](#expandable-hovers-for-javascript-and-typescript-experimental)
  - [Remote Development](#remote-development)
    - [Dev container instructions files](#dev-container-instructions-files)
  - [Contributions to extensions](#contributions-to-extensions)
    - [Python](#python)
      - [Branch coverage support](#branch-coverage-support)
      - [Python Environments Quick Create command](#python-environments-quick-create-command)
      - [Python Environments chat tools](#python-environments-chat-tools)
      - [Color picker when using Pylance](#color-picker-when-using-pylance)
      - [AI Code Actions: Convert Format String (Experimental)](#ai-code-actions-convert-format-string-experimental)
    - [GitHub Pull Requests and Issues](#github-pull-requests-and-issues)
  - [Extension Authoring](#extension-authoring)
    - [Text Encodings](#text-encodings)
    - [ESM support for extensions](#esm-support-for-extensions)
  - [Proposed APIs](#proposed-apis)
    - [Tool calling for images](#tool-calling-for-images)
    - [MCP servers contributed by extensions](#mcp-servers-contributed-by-extensions)
    - [MCP Tool Annotations](#mcp-tool-annotations)
  - [Notable fixes](#notable-fixes)
  - [Thank you](#thank-you)
    - [Issue tracking](#issue-tracking)
    - [Pull requests](#pull-requests)

---

Welcome to the April 2025 release of Visual Studio Code. There are many updates in this version that we hope you'll like, some of the key highlights include:

- **Chat**
  - Custom instructions and reusable prompts ([more...](#prompt-and-instructions-files)).
  - Smarter results with tools for GitHub, extensions, and notebooks ([more...](#search-code-of-a-github-repository-with-the-githubrepo-tool)).
  - Image and Streamable HTTP support for MCP ([more...](#mcp-support-for-streamable-http)).

- **Chat performance**
  - Faster responses on repeat chat requests ([more...](#conversation-summary-and-prompt-caching)).
  - Faster edits in agent mode ([more...](#faster-agent-mode-edits)).

- **Editor experience**
  - Improved multi-window support for chat and editors ([more...](#floating-window-modes)).
  - Staged changes now easier to identify ([more...](#quick-diff-decorations-for-staged-changes)).

>If you'd like to read these release notes online, go to [Updates](https://code.visualstudio.com/updates) on [code.visualstudio.com](https://code.visualstudio.com).
**Insiders:** Want to try new features as soon as possible? You can download the nightly [Insiders](https://code.visualstudio.com/insiders) build and try the latest updates as soon as they are available.

## Chat

### Prompt and instructions files

You can tailor your AI experience in VS Code to your specific coding practices and technology stack by using Markdown-based instructions and prompt files. We've aligned the implementation and usage of these two related concepts, however they each have distinct purposes.

#### Instructions files

**Setting**: `setting(chat.instructionsFilesLocations)`

Instructions files (also known as custom instructions or rules) provide a way to describe common guidelines and context for the AI model in a Markdown file, such as code style rules, or which frameworks to use. Instructions files are not standalone chat requests, but rather provide context that you can apply to a chat request.

Instructions files use the `.instructions.md` file suffix. They can be located in your user data folder or in the workspace. The `setting(chat.instructionsFilesLocations)` setting lists the folders that contain instruction files.

You can manually attach instructions to a specific chat request, or they can be automatically added:

- To add them manually, use the **Add Context** button in the Chat view, and then select **Instructions...**.
  Alternatively use the **Chat: Attach Instructions...** command from the Command Palette. This brings up a picker that lets you select existing instructions files or create a new one to attach.

- To automatically add instructions to a prompt, add the `applyTo` Front Matter header to the instructions file to indicate which files the instructions apply to. If a chat request contains a file that matches the given glob pattern, the instructions file is automatically attached.

  The following example provides instructions for TypeScript files (`applyTo: '**/*.ts'`):

  ````md
  ---
  applyTo: '**/*.ts'
  ---
  Place curly braces on separate lines for multi-line blocks:
  if (condition)
  {
    doSomething();
  }
  else
  {
    doSomethingElse();
  }
  ````

You can create instruction files with the **Chat: New Instructions File...** command. Moreover, the files created in the _user data_ folder can be automatically synchronized across multiple user machines through the Settings Sync service. Make sure to check the **Prompts and Instructions** option in the **Backup and Sync Settings...** dialog.

Learn more about [instruction files](https://code.visualstudio.com/docs/copilot/copilot-customization#_instruction-files) in our documentation.

#### Prompt files

**Setting**: `setting(chat.promptFilesLocations)`

Prompt files describe a standalone, complete chat request, including the prompt text, chat mode, and tools to use. Prompt files are useful for creating reusable chat requests for common tasks. For example, you can add a prompt file for creating a front-end component, or to perform a security review.

Prompt files use the `.prompt.md` file suffix. They can be located in your user data folder or in the workspace. The `setting(chat.promptFilesLocations)` setting lists the folder where prompt files are looked for.

There are several ways to run a prompt file:

- Type `/` in the chat input field, followed by the prompt file name.
  ![Screenshot that shows running a prompt in the Chat view with a slash command.](images/1_100/run-prompt-as-slash-command.png)

- Open the prompt file in an editor and press the 'Play' button in the editor tool bar. This enables you to quickly iterate on the prompt and run it without having to switch back to the Chat view.
  ![Screenshot that shows running a prompt by using the play button in the editor.](images/1_100/run-prompt-from-play-button.png)

- Use the **Chat: Run Prompt File...** command from the Command Palette.

Prompt files can have the following Front Matter metadata headers to indicate how they should be run:

- `mode`: the chat mode to use when invoking the prompt (`ask`, `edit`, or `agent` mode).
- `tools`: if the `mode` is `agent`, the list of tools that are available for the prompt.

The following example shows a prompt file for generating release notes, that runs in agent mode, and can use a set of tools:

```md
---
mode: 'agent'
tools: ['getCurrentMilestone', 'getReleaseFeatures', 'file_search', 'semantic_search', 'read_file', 'insert_edit_into_file', 'create_file', 'replace_string_in_file', 'fetch_webpage', 'vscode_search_extensions_internal']
---
Generate release notes for the features I worked in the current release and update them in the release notes file. Use [release notes writing instructions file](.github/instructions/release-notes-writing.instructions.md) as a guide.
```

To create a prompt file, use the **Chat: New Prompt File...** command from the Command Palette.

Learn more about [prompt files](https://code.visualstudio.com/docs/copilot/copilot-customization#_prompt-files-experimental) in our documentation.

#### Improvements and notes

- Instructions and prompt files now have their own language IDs, configurable in the _language mode_ dialog for any file open document ("Prompt" and "Instructions" respectively). This allows, for instance, using untitled documents as temporary prompt files before saving them as files to disk.
- We renamed the **Chat: Use Prompt** command to **Chat: Run Prompt**. Furthermore, the command now runs the selected prompt _immediately_, as opposed to attaching it as chat context as it did before.
- Both file types now also support the `description` metadata in their headers, providing a common place for short and user-friendly prompt summaries. In the future, this header is planned to be used along with the `applyTo` header as the rule that determines if the file needs to be auto-included with chat requests (for example, `description: 'Code style rules for front-end components written in TypeScript.'`)

### Faster agent mode edits

We've implemented support for OpenAI's apply patch editing format (GPT 4.1 and o4-mini) and Anthropic’s replace string tool (Claude Sonnet 3.7 and 3.5) in agent mode. This means that you benefit from significantly faster edits, especially in large files.

The update for OpenAI models is on by default in VS Code Insiders and gradually rolling out to Stable. The Anthropic update is available for all users in both Stable and Insiders.

### Base model in chat

We're gradually rolling out GPT-4.1 as the default base model in chat in VS Code. You can use the model switcher in the Chat view to change to another model at any time.

### Search code of a GitHub repository with the `#githubRepo` tool

Imagine you need to ask a question about a GitHub repository, but you don't have it open in your editor. For example, you want to know how a specific function is implemented in the `microsoft/vscode` repository.

You can now use the `#githubRepo` tool to search for code snippets in any GitHub repository that you have access to. This tool takes a `user/repo` as extra input. For example, "how to implement factory pattern in TS #githubRepo microsoft/vscode".

You can also use [custom instructions](https://code.visualstudio.com/docs/copilot/copilot-customization#_custom-instructions) to hint when and how to use this tool, as shown in the following example:

```md
---
applyTo: '**'
---
Use the `#githubRepo` tool with `microsoft/vscode` to find relevant code snippets in the VS Code codebase.
Use the `#githubRepo` tool with `microsoft/typescript` to answer questions about how TypeScript is implemented.
```

![Screenshot showing using the #githubRepo tool in agent mode with hints from instructions files.](images/1_100/github-repo-tool-example.png)

If you want to ask about the repo you are currently working on, you can just use the [`#codebase` tool](https://code.visualstudio.com/docs/copilot/reference/workspace-context#_making-copilot-chat-an-expert-in-your-workspace).

Also, the `#githubRepo` tool is only for searching for relevant code snippets. The [GitHub MCP server](https://github.com/github/github-mcp-server?tab=readme-ov-file#github-mcp-server) provides tools for working with GitHub issues and pull requests. Learn more about [adding MCP servers in VS Code](https://code.visualstudio.com/docs/copilot/chat/mcp-servers#_add-an-mcp-server).

### Find Marketplace extensions with the extensions tool

Use the extensions tool (`#extensions`) in chat to find extensions from the Marketplace. Based on your chat prompt, the tool is automatically invoked, or you can explicitly reference it in your prompt with `#extensions`. The tool returns a list of extensions that match your query. You can install extensions directly from the results.

<video src="images/1_100/extensions-agent-tool.mp4" title="Video that shows using the extensions tool to display popular Java extensions." autoplay loop controls muted></video>

### Improvements to the web page fetch tool

Last month, we introduced the fetch tool (`#fetch`) for retrieving the contents of a web page right from chat, and include it as context for your prompt. If you missed that release note, check out [the initial release of the fetch tool](https://code.visualstudio.com/updates/v1_99#fetch-tool) release note and examples.

This iteration, we have made several big changes to the tool including:

- **Entire page as context**: We now add the entire page as context, rather than a subset. With larger context windows, we have the ability to give the model the entire page. For example, it's now possible to ask summarization questions that require as much of the page as possible. If you _do_ manage to fill up the context window, the fetch tool is smart enough to exclude the less relevant sections of the page. That way, you don't exceed the context window limit, while still keeping the important parts.
- **A standardized page format (Markdown)**: Previously, we formatted fetched webpages in a custom hierarchical format that did the job, but was sometimes hard to reason with because of its custom nature. We now convert fetched webpages into Markdown, a standardized language. This improves the reliability of the _relevancy detection_ and is a format that most language models know deeply, so they can reason with it more easily.

We'd love to hear how you use the fetch tool and if there are any capabilities you'd like to see from it!

### Chat input improvements

We have made several improvements to the chat input box:

- **Attachments**: when you reference context in the prompt text with `#`, they now also appear as an attachment pill. This makes it simpler to understand what's being sent to the language model.
- **Context picker**: we streamlined the context picker to make it simpler to pick files, folders, and other attachment types.
- **Done button**: we heard your feedback about the "Done"-button and we removed it! No more confusion about unexpected session endings. Now, we only start a new session when you create a new chat (`kb(workbench.action.chat.newChat)`).

### Chat mode keyboard shortcuts

The keyboard shortcut `kb(workbench.action.chat.open)` still just opens the Chat view, but the `kb(workbench.action.chat.openAgent)` shortcut now opens the Chat view and switches to [agent mode](vscode://GitHub.Copilot-Chat/chat?mode=agent). If you'd like to set up keyboard shortcuts for other chat modes, there is a command for each mode:

- `workbench.action.chat.openAgent`
- `workbench.action.chat.openEdit`
- `workbench.action.chat.openAsk`

### Autofix diagnostics from agent mode edits

**Setting**: `setting(github.copilot.chat.agent.autoFix)`

If a file edit in agent mode introduces new errors, agent mode can now detect them, and automatically propose a follow-up edit. This means that you don't have to send a follow-up prompt to ask agent mode to fix any errors. You can disable this behavior with `setting(github.copilot.chat.agent.autoFix)`.

### Handling of undo and manual edits in agent mode

Previously, making manual edits during an agent mode session could confuse the model. Now, the agent is prompted about your changes, and should re-read files when necessary before editing files that might have changed.

### Conversation summary and prompt caching

We've made some changes to how our agent mode prompt is built to optimize for prompt caching. Prompt caching is a way to speed up model responses by maintaining a stable prefix for the prompt. The next request is able to resume from that prefix, and the result is that each request should be a bit faster. This is especially effective in a repetitive series of requests with large context, like you typically have in agent mode.

When your conversation gets long, or your context gets very large, you might see a "Summarized conversation history" message in your agent mode session:

![Screenshot showing a summarized conversation message in the Chat view.](images/1_100/summarized-conversation.png)

Instead of keeping the whole conversation as a FIFO, breaking the cache, we compress the conversation so far into a summary of the most important information and the current state of your task. This keeps the prompt prefix stable, and your responses fast.

### MCP support for Streamable HTTP

This release adds support for the new Streamable HTTP transport for Model Context Protocol servers. Streamable HTTP servers are configured just like existing SSE servers, and our implementation is backwards-compatible with SSE servers:

```json
{
  "servers": {
    "my-mcp-server": {
      "url": "http://localhost:3000/mcp"
    }
  }
}
```

Learn more about [MCP support in VS Code](https://code.visualstudio.com/docs/copilot/chat/mcp-servers).

### MCP support for image output

We now support MCP servers that generate images as part of their tool output.

Note that not all language models support reading images from tool output. For example, although GPT-4.1 has vision capability, it does not currently support reading images from tools.

### Enhanced input, output, and progress from MCP servers

We have enhanced the UI that shows MCP server tool input and output, and have also added support for MCP's new progress messages.

<video src="images/1_100/mcp-confirm.mp4" autoplay loop controls muted></video>
_Theme: [Codesong](https://marketplace.visualstudio.com/items?itemName=connor4312.codesong) (preview on [vscode.dev](https://vscode.dev/editor/theme/connor4312.codesong))_

### MCP config generation uses inputs

To help keep your secrets secure, AI-assisted configurations generated by the **MCP: Add Server** command now generate `inputs` for any secrets, rather than inlining them into the resulting configuration.

### Inline chat V2 (Preview)

**Setting**: `setting(inlineChat.enableV2:true)`

We have been working on a revamped version of inline chat `kb(inlineChat.start)`. Its theme is still "bringing chat into code", but behind the scenes it uses the same logic as chat edits. This means better use of the available context and a better code-editing strategy. You can enable inline chat v2 via `setting(inlineChat.enableV2:true)`

Further, there is now a more lightweight UX that can optionally be enabled. With the `setting(inlineChat.hideOnRequest:true)` setting, inline chat hides as soon as a request is made. It then minimizes into the chat-editing overlay, which enables accepting or discarding changes, or restoring the inline chat control.

<video src="images/1_100/inlinechat2.mp4" title="Video that shows inline chat v2 and hide-on-request in action." autoplay loop controls muted></video>

### Select and attach UI elements to chat (Experimental)

**Setting**: `setting(chat.sendElementsToChat.enabled)`

While you're developing a web application, you might want to ask chat about specific UI elements of a web page. You can now use the built-in Simple Browser to attach UI elements as context to chat.

After opening any locally-hosted site via the built-in Simple Browser (launch it with the **Simple Browser: Show** command), a new toolbar is now shown where you can select **Start** to select any element in the site that you want. This attaches a screenshot of the selected element, and the HTML and CSS of the element.

<video src="images/1_100/ui-element-selection-demo.mp4" title="Video showing the full flow of the UI element selection experimental feature. In the demo, we attach a hero from a webpage and ask chat to add a background image to that hero." autoplay loop controls muted></video>

Configure what is attached to chat with:

- `setting(chat.sendElementsToChat.attachCSS)`: enable or disable attaching the associated CSS
- `setting(chat.sendElementsToChat.attachImages)`: enable or disable attaching the screenshot of the selected element

This experimental feature is enabled by default for all Simple Browsers, but can be disabled with `setting(chat.sendElementsToChat.enabled)`.

### Create and launch tasks in agent mode (Experimental)

**Setting**: `setting(github.copilot.chat.newWorkspaceCreation.enabled)`

In the previous release, we introduced the `setting(github.copilot.chat.newWorkspaceCreation.enabled)` (Experimental) setting to enable workspace creation with agent mode.

Now, at the end of this creation flow, you are prompted to create and run a task for launching your app or project. This streamlines the project launch process and enables easy task reuse.

## Accessibility

### Merge editor improvements

The merge editor is now more accessible. To learn about available actions, open the accessibility help dialog within the merge editor (`kb(editor.action.accessibilityHelp)`). Key actions include `Merge Editor: Complete Merge` (`kb(mergeEditor.acceptMerge)`) and `Toggle Between Merge Editor Inputs` (`kb(mergeEditor.toggleBetweenInputs)`). The currently focused input is also now announced to assistive technologies.

### Next edit suggestion enhancements

The new setting `setting(accessibility.signals.nextEditSuggestion)` notifies you when a predicted suggestion is available. Review and accept suggestions through the accessible view (`kb(editor.action.accessibleView)`). Additionally, `setting(accessibility.signals.diffLineAdded)` and `setting(accessibility.signals.diffLineRemoved)` provide audio cues during navigation to make diff review accessible.

### Review Copilot user requests from the accessible view

When in [agent mode](vscode://GitHub.Copilot-Chat/chat?mode=agent), tool invocations or terminal commands sometimes require user permission to run. Review these actions within the accessible view (`kb(editor.action.accessibleView)`).

### Unique accessibility sounds

`setting(accessibility.signals.save.sound)` now has its own distinct sound and no longer shares audio with `setting(accessibility.signals.terminalCommandSucceeded.sound)`.

## Editor Experience

### Floating window modes

Floating windows in VS Code allow you to move editors and certain views out of the main window into a smaller window for lightweight multi-window setups. There are two new modes a floating window can have:

- Compact: we hide certain UI elements to make more room for the actual content
- Always-on-top: the window stays on top of all other windows until you leave this mode

Here is an example of how to turn a floating editor window into compact mode:

<video src="images/1_100/floating-compact.mp4" title="Video that shows floating window compact mode." autoplay loop controls muted></video>

We use compact mode by default for when you create a chat in a new window. Combined with the option to have the window always on top, you can always keep the Chat view around for asking questions!

<video src="images/1_100/floating-pinned.mp4" title="Video that shows floating window always on top." autoplay loop controls muted></video>

We introduced new commands if you prefer to use keyboard shortcuts for these actions:

- `workbench.action.toggleWindowAlwaysOnTop`: to toggle always on top mode
- `workbench.action.enableWindowAlwaysOnTop`: to set the floating window always on top
- `workbench.action.disableWindowAlwaysOnTop`: to set the floating window to normal
- `workbench.action.toggleCompactAuxiliaryWindow`: to toggle compact mode
- `workbench.action.enableCompactAuxiliaryWindow`: to enable compact mode
- `workbench.action.disableCompactAuxiliaryWindow`: to disable compact mode

> **Note:** even in compact mode you can create complex editor layouts and open other editors.

### Secondary Side Bar default visibility

**Setting**: `setting(workbench.secondarySideBar.defaultVisibility)`

By default, the Secondary Side Bar is hidden when you open a new workspace or window. With the new setting `setting(workbench.secondarySideBar.defaultVisibility)`, you can control if the Secondary Side Bar should open automatically in new workspaces or windows. You can pick from:

- `hidden`: this is the default and keeps the Secondary Side Bar hidden
- `visibleInWorkspace`: this opens the Secondary Side Bar if you open a folder or multi-root workspace
- `visible`: this always opens the Secondary Side Bar

Note that after a workspace or window has been opened, the visibility becomes a workspace state and overrides the setting value. If you close the Secondary Side Bar, it will remain closed in that workspace or window.

### Mandatory extension signature verification

Extension signature verification is now required on all platforms: Windows, macOS, and Linux. Previously, this verification was only mandatory on Windows and macOS. With this release, Linux now also enforces extension signature verification, ensuring that all extensions are properly validated before installation.

This change further strengthens security by preventing the installation of potentially malicious extensions. For more information, see the [Extension Signing](https://code.visualstudio.com/docs/configure/extensions/extension-marketplace#_the-extension-signature-cannot-be-verified-by-vs-code).

> **Note:** Mandatory extension signature verification remains disabled on Linux ARM32 builds due to [issue #248308](https://github.com/microsoft/vscode/issues/248308). This is expected to be resolved in the next release.

### Learn more links for malicious extensions

When an extension is identified as malicious, VS Code now provides links to additional information explaining why the extension was flagged. These "Learn More" links connect users to GitHub issues or documentation with details about the security concerns, helping you better understand the potential risks.

### Prevent installation of Copilot Chat pre-release versions in VS Code stable

VS Code now prevents the installation of the pre-release version of the Copilot Chat extension in VS Code Stable. This helps avoid situations where you inadvertently install the Copilot Chat pre-release version and get stuck in a broken state. This means that you can only install the Copilot Chat extension pre-release version in the Insiders build of VS Code.

### Command to open a view without focus

Views (tree views and webview views) can now be opened without focusing them. This is useful for extensions and keyboard shortcuts that want to open a view but not take focus away from the current editor. The command is `your-view-id.open`, and it takes a property bag argument: `{ preserveFocus: boolean}`.

### Semantic text search with keyword suggestions (Experimental)

**Setting**: `setting(github.copilot.chat.search.keywordSuggestions:true)`

Semantic text search now supports AI-powered keyword suggestions. By enabling this feature, you will start seeing relevant references or definitions that might help you find the code you are looking for.

<video src="images/1_100/ai-keywords.mp4" title="Video that shows AI-powered keyword suggestions in Visual Studio Code." autoplay loop controls muted></video>

## Code Editing

### New Next Edit Suggestions (NES) model

**Setting**: `setting(github.copilot.nextEditSuggestions.enabled)`

We're excited to introduce a new model powering NES, designed to provide faster and more contextually relevant code recommendations. This updated model offers improved performance, delivering suggestions with reduced latency, and offering suggestions that are less intrusive and align more closely with your recent edits. This update is part of our ongoing commitment to refining AI-assisted development tools within Visual Studio Code.

### Import suggestions

**Setting**: `setting(github.copilot.nextEditSuggestions.fixes:true)`

Next Edit Suggestions (NES) can now automatically suggest adding missing import statements in JavaScript and TypeScript files. Enable this feature by setting `setting(github.copilot.nextEditSuggestions.fixes:true)`. We plan to further enhance this capability by supporting imports from additional languages in future updates.

![Screenshot showing NES suggesting an import statement.](images/1_100/nes-import.png)

### Generate alt text in HTML or Markdown

You can now generate or update existing alt text in HTML and Markdown files. Navigate to any line containing an embedded image and trigger the quick fix via `kb(editor.action.quickFix)` or by selecting the lightbulb icon.

![Screenshot that shows generating alt text for an image html element.](images/1_100/generate-alt-text.png)

### Variable line heights

It is now possible to define variable line heights on a monaco editor by setting the line height value in the `IModelDecorationOptions` type. If two line heights are set on a line, the maximum of the two is used on the line.

Note that for simplicity for now, the line height is set only on the first line of the corresponding decoration range. In the following screen recording, lines 24 and 32 are rendered with a larger line height than the default one.

<video src="images/1_100/variable-line-heights.mp4" title="Video that shows variable line heights in the editor." autoplay loop controls muted></video>

This work is not yet available to extensions, but will roll out after some more testing.

## Notebooks

### Find and replace history persistence

The Notebook Find control now supports persistent history for both the find and replace input fields. This persists across reloads, and is controlled by the settings `setting(editor.find.history)` and `setting(editor.find.replaceHistory)`.

### Drag and drop cell outputs to chat

To enhance existing support for cell output usage within chat, outputs are now able to be dragged into the Chat view for a seamless attachment experience. Currently, only image and textual outputs are supported. Outputs with an image mime type are directly draggable, however to avoid clashing with text selection, textual outputs require holding the `kbstyle(alt)` modifier key to enable dragging. We are exploring UX improvements in the coming releases.

<video src="images/1_100/output-dnd.mp4" title="Video that shows multiple cell outputs being attached as chat context via drag and drop." autoplay loop controls muted></video>

### Notebook tools for agent mode

#### Run cell

Chat now has an LLM tool to run notebook cells, which allows the agent to perform updates based on cell run results or perform its own data exploration as it builds out a notebook.

<video src="images/1_100/agent-notebook-run-edit-loop.mp4" title="Video that shows copilot running notebook cells, making updates based on an error, and retrying those cells." autoplay loop controls muted></video>

#### Get kernel state

The agent can find out which cells have been executed in the current kernel session, and read the active variables by using the Kernel State tool.

#### List/Install packages

The Jupyter extension contributes tools for listing and installing packages into the environment that's being used as the notebook's kernel. The operation is delegated to the Python Environments extension if available; otherwise, it attempts to use the pip package manager.

## Source Control

### Quick diff decorations for staged changes

To address a long-time feature request, this milestone we have added quick diff editor decorations for staged changes. Now you can view your staged changes directly from the editor, without needing to open the Source Control view.

<video src="images/1_100/staged-changes-diff-decorations.mp4" title="Video that shows managing staged changed from an editor by using diff decorations." autoplay loop controls muted></video>

You can customize the color of the staged changes quick diff decorations by using the following theme tokens: `editorGutter.addedSecondaryBackground`, `editorGutter.modifiedSecondaryBackground`, `editorGutter.deletedSecondaryBackground`.

If you do not want to see quick diff decorations for staged changes, you can hide them by using the **Diff Decorations** submenu that is available in the editor gutter context menu.

## Debugging

### Disassembly view context menu

Thanks to a community contribution, we now have a context menu in the disassembly view.

![Screenshot that shows the context menu in the Disassembly view.](images/1_100/disassembly-context.png)

### JavaScript debugger Network view

Recent versions of Node.js have enhanced its network debugging capabilities. The [experimental network view](https://code.visualstudio.com/updates/v1_93#experimental-network-view) will be enabled by default on recent versions of Node.js that support it well (v22.14.0 and above).

## Languages

### Show browser support for CSS and HTML

When hovering over a CSS property, HTML element, or HTML attribute, you now see a summary of how well that property or element is supported across browsers using [Baseline](https://developer.mozilla.org/docs/Glossary/Baseline/Compatibility).

![Screenshot that shows baseline browser support in the CSS hover.](images/1_100/css-baseline.png)

### Default syntax highlighting for `.*.env` files

Files with name format `.*.env` are now syntax highlighted as `.ini` files.

### Expandable hovers for JavaScript and TypeScript (Experimental)

**Setting**: `setting(typescript.experimental.expandableHover)`

We've continued to iterate on the expandable hover feature for JavaScript and TypeScript. This feature lets you use a `+` and `-` in the hover control to show more or less type information.

<video src="images/1_100/expandable-hover.mp4" title="Video that shows TypeScript expandable hover." autoplay loop controls muted></video>

This feature is still experimental but you can try it today by enabling `setting(typescript.experimental.expandableHover)`. You must be using TypeScript version 5.9 or above, for example by installing the [TypeScript nightly extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-typescript-next).

## Remote Development

The [Remote Development extensions](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack), allow you to use a [Dev Container](https://code.visualstudio.com/docs/devcontainers/containers), remote machine via SSH or [Remote Tunnels](https://code.visualstudio.com/docs/remote/tunnels), or the [Windows Subsystem for Linux](https://learn.microsoft.com/windows/wsl) (WSL) as a full-featured development environment.

### Dev container instructions files

Dev Container features and images now include instructions files describing their tools and configuration. VS Code chat can automatically use this context, improving the relevance and accuracy of its suggestions during development.

## Contributions to extensions

### Python

#### Branch coverage support

Branch coverage is now supported in the Testing Explorer for Python! Note that your `coveragepy` version must be >= 7.7 for this feature. You can upgrade coverage by running `pip install coverage==7.7`.

<video src="images/1_100/python-branch-coverage.mp4" title="Video showing branch coverage run using the Test Explorer and branch coverage displayed." autoplay loop controls muted></video>

#### Python Environments Quick Create command

The [Python Environments](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-python-envs) extension has added support for Quick Create, making the environment creation process more seamless. Quick Create minimizes the input needed from you to create new virtual environments by detecting the latest Python version on your machine to create the virtual environment and install any workspace dependencies with a single click. This will create a `.venv` in your workspace for venv-based environments, and `.conda`  for-conda based environments. You can access Quick Create via the **Python: Create Environment** command in the Command Palette.

![Screenshot showing Quick Create in the Python: Create Environment quick pick.](images/1_100/python-envs-quick-create.png)

#### Python Environments chat tools

The [Python Environments](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-python-envs) extension (preview) now includes two chat tools: “Get Python Environment Information” and “Install Python Package”. To use these tools, you can either directly reference them in your prompt by adding `#pythonGetEnvironmentInfo` `#pythonInstallPackage`, or agent mode will automatically call the tool as applicable. These tools seamlessly detect appropriate environment information based on file or workspace context, and handle package installation with accurate environment resolution.

<video src="images/1_100/python-get-env-tool.mp4" title="Video demoing the get environment information tool call implicitly by the model in agent mode." autoplay loop controls muted></video>

<video src="images/1_100/python-install-pkg-tool.mp4" title="Video demoing the get install package tool call for numpy version 2.2." autoplay loop controls muted></video>

#### Color picker when using Pylance

Pylance can now display an interactive color swatch directly in the editor for recognized color values in Python files, making it easier to visualize and pick colors on the fly. To try it out, you can enable `setting(python.analysis.enableColorPicker:true)`. Supported formats include #RGB (like "#001122") and #RGBA (like "#001122FF").

![Screenshot showing the color swatch displayed in the editor next to #RGB color format.](images/1_100/pylance-color-picker.png)

#### AI Code Actions: Convert Format String (Experimental)

When using Pylance, there's a new experimental AI Code Action for converting string concatenations to f-string or format(). To try it out, select the **Convert to f-string with Copilot** or the **Convert to format() call with Copilot** Code Actions through the light bulb when selecting a symbol in the string you wish to convert, or through `kbstyle(Ctrl + .)`/`kbstyle(Cmd + .)`.

![Screenshot showing the convert strings Code Actions, powered by AI.](images/1_100/pylance-convert-string.png)

This experience is enabled via the following setting:

```json
"python.analysis.aiCodeActions": {"convertFormatString": true}
```

Then once you define a new symbol, for example, a class or a function, you can select the **Generate Symbol with Copilot** Code Action and let AI handle the implementation. If you want, you can then use Pylance's **Move Symbol** Code Actions to move it to a different file.

### GitHub Pull Requests and Issues

There has been more progress on the [GitHub Pull Requests](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github) extension, which enables you to work on, create, and manage pull requests and issues. New features include:

- Ask questions in chat about the active pull request, such as "Address all comments in the #activePullRequest".
- View issues in a webview, just like you can view pull requests.
- Polish and alignment of the "Pull Requests", "Issues", and "Notifications" views.
- Prepared for the release of GitHub's Project Padawan by enabling assignment of issues to Copilot, @-mentioning of Copilot, and ensuring it will be displayed properly in the UI.

Review the [changelog for the 0.110.0](https://github.com/microsoft/vscode-pull-request-github/blob/main/CHANGELOG.md#01100) release of the extension to learn about the other highlights.

## Extension Authoring

### Text Encodings

We finalized the API for working with text encodings in VS Code.

Specifically, this new API allows you to:

- Get the current `encoding` of a `TextDocument`
- Open a `TextDocument` with a specific `encoding`
- Encode a `string` to a `Uint8Array` with a specific `encoding`
- Decode a `Uint8Array` to a `string` using a specific `encoding`

### ESM support for extensions

The NodeJS extension host now supports extensions that use JavaScript-modules (ESM). All it needs is the `"type": "module"` entry in your extension's `package.json` file. With that, the JavaScript code can use `import` and `export` statements, including the special module `import('vscode')`. Find a sample here: <https://github.com/jrieken/vscode-esm-sample-extension>.

Note that ESM support isn't for the web worker extension host yet. There are some technical challenges that need to be overcome first. We'll post updates on <https://github.com/microsoft/vscode/issues/130367>. Stay tuned!

## Proposed APIs

### Tool calling for images

Last iteration, we added a [proposed API](https://github.com/microsoft/vscode/blob/main/src/vscode-dts/vscode.proposed.languageModelDataPart.d.ts) so that extensions can attach images and send vision requests to the language model. This iteration, we've expanded on this API to allow tool call results to include images as well.

Check out [this API proposal issue](https://github.com/microsoft/vscode/issues/245104) to see a usage example and to stay up to date with the status of this API.

### MCP servers contributed by extensions

Extensions are able to programmatically contribute extensions to the editor by using the new [proposed API](https://github.com/microsoft/vscode/blob/main/src/vscode-dts/vscode.proposed.languageModelDataPart.d.ts). This is an alternative to users hardcoding configuration for each server in their settings or `mcp.json`.

If this API is interesting to you, check out [its sample](https://github.com/microsoft/vscode-extension-samples/tree/main/mcp-extension-sample/) and [the API proposal issue](https://github.com/microsoft/vscode/issues/243522) to stay up to date with the status of this API.

### MCP Tool Annotations

VS Code will now display the human-readable names of MCP servers with tools configured with the appropriate [tool annotations](https://modelcontextprotocol.io/docs/concepts/tools#tool-annotations). Additionally, tools marked with `readOnlyHint: true` in their annotations will be allowed to run without requiring user confirmation.

## Notable fixes

- [244939](https://github.com/microsoft/vscode/issues/244939) - Personal Microsoft accounts logs out very quickly (few mins to few hours)

## Thank you

Last but certainly not least, a big _**Thank You**_ to the contributors of VS Code.

### Issue tracking

Contributions to our issue tracking:

- [@albertosantini (Alberto Santini)](https://github.com/albertosantini)
- [@gjsjohnmurray (John Murray)](https://github.com/gjsjohnmurray)
- [@RedCMD (RedCMD)](https://github.com/RedCMD)
- [@IllusionMH (Andrii Dieiev)](https://github.com/IllusionMH)

### Pull requests

Contributions to `vscode`:

- [@ahojukka5 (Jukka Aho)](https://github.com/ahojukka5): Update chatExecuteActions.ts [PR #246494](https://github.com/microsoft/vscode/pull/246494)
- [@alexweininger (Alex Weininger)](https://github.com/alexweininger): fix: handle cancellation errors inside edit session identity provider [PR #247450](https://github.com/microsoft/vscode/pull/247450)
- [@andrewbranch (Andrew Branch)](https://github.com/andrewbranch): Allow disabling built-in TS/JS extension in favor of tsgo [PR #246858](https://github.com/microsoft/vscode/pull/246858)
- [@BABA983 (BABA)](https://github.com/BABA983): A command to accept all combination [PR #225132](https://github.com/microsoft/vscode/pull/225132)
- [@batsev](https://github.com/batsev): Git - validate branch name before creation [PR #245029](https://github.com/microsoft/vscode/pull/245029)
- [@brthom (Ben Thomas)](https://github.com/brthom): Fix test items sorting in Testing Explorer to use natural file order [PR #246352](https://github.com/microsoft/vscode/pull/246352)
- [@bytemain (Jiacheng)](https://github.com/bytemain)
  - fix: correct filtering logic for file-based recommendations [PR #245062](https://github.com/microsoft/vscode/pull/245062)
  - refactor(nls): use then for JSON parsing [PR #247013](https://github.com/microsoft/vscode/pull/247013)
- [@Cecil0o0 (hj)](https://github.com/Cecil0o0): git: make Letter/Text/Color semantically consistency [PR #245889](https://github.com/microsoft/vscode/pull/245889)
- [@eps1lon (Sebastian "Sebbie" Silbermann)](https://github.com/eps1lon): Deemphasize old JSX transform [PR #246738](https://github.com/microsoft/vscode/pull/246738)
- [@futurist (James Yang)](https://github.com/futurist): fix: runCommand type [PR #246198](https://github.com/microsoft/vscode/pull/246198)
- [@gabritto (Gabriela Araujo Britto)](https://github.com/gabritto)
  - [typescript-language-features] Re-add expandable hover [PR #246899](https://github.com/microsoft/vscode/pull/246899)
  - [typescript-language-features] make expandable hover true by default [PR #247343](https://github.com/microsoft/vscode/pull/247343)
- [@guiserle (guiserle)](https://github.com/guiserle): config: Resolve variables returned by commands [PR #246641](https://github.com/microsoft/vscode/pull/246641)
- [@huntertran (Tuan Tran Van)](https://github.com/huntertran): Replace single line break with double line break for commit description in git blame hover popup [PR #245779](https://github.com/microsoft/vscode/pull/245779)
- [@johnscollins98 (John Collins)](https://github.com/johnscollins98): #245665 fix early task exit with empty promptString input [PR #246834](https://github.com/microsoft/vscode/pull/246834)
- [@KapitanOczywisty](https://github.com/KapitanOczywisty): Fix html derivative grammar consuming php code, fixes #237262 [PR #245076](https://github.com/microsoft/vscode/pull/245076)
- [@luantranminh (Tran Minh Luan)](https://github.com/luantranminh): argv: update description for `add-mcp` [PR #246473](https://github.com/microsoft/vscode/pull/246473)
- [@manabu-nakamura (nakamura)](https://github.com/manabu-nakamura)
  - tooltip text of close button is internationalized [PR #245190](https://github.com/microsoft/vscode/pull/245190)
  - tooltip text for close button is internationalized (2) [PR #245333](https://github.com/microsoft/vscode/pull/245333)
  - normalize ellipsis [PR #246447](https://github.com/microsoft/vscode/pull/246447)
- [@mdanish-kh (Muhammad Danish)](https://github.com/mdanish-kh): Update WinGet configuration file location & extension [PR #242241](https://github.com/microsoft/vscode/pull/242241)
- [@mkhuzaima (Muhammad Khuzaima Umair)](https://github.com/mkhuzaima): Set DragData when directory is dragged [PR #243656](https://github.com/microsoft/vscode/pull/243656)
- [@mortalYoung (野迂迂)](https://github.com/mortalYoung): fix: remove necessary async declaration [PR #247213](https://github.com/microsoft/vscode/pull/247213)
- [@nknguyenhc (Nguyen)](https://github.com/nknguyenhc): Goto definition for built-in symbols in HTML script [PR #244074](https://github.com/microsoft/vscode/pull/244074)
- [@noahbowman (Noah)](https://github.com/noahbowman): #188711 - Walkthrough Focus-Visible Outline [PR #247650](https://github.com/microsoft/vscode/pull/247650)
- [@pedrofrazaopacheco (Pedro Frazão Pacheco)](https://github.com/pedrofrazaopacheco): Fixes microsoft/vscode#240654: Avoid encoding reserved chars in JSON schema URL [PR #244934](https://github.com/microsoft/vscode/pull/244934)
- [@pisv (Vladimir Piskarev)](https://github.com/pisv): Merge Editor: fix a bug in `LineRange.join(other)` [PR #227585](https://github.com/microsoft/vscode/pull/227585)
- [@RedCMD (RedCMD)](https://github.com/RedCMD)
  - Fix template.expression brackets #190564 [PR #245786](https://github.com/microsoft/vscode/pull/245786)
  - YAML auto trigger code completion in strings #239679 [PR #246939](https://github.com/microsoft/vscode/pull/246939)
- [@s-rigaud (Samuel Rigaud)](https://github.com/s-rigaud)
  - test: fix typos [PR #247259](https://github.com/microsoft/vscode/pull/247259)
  - fix: vscode-dts typos [PR #247263](https://github.com/microsoft/vscode/pull/247263)
  - fix: toggleApplicationScope typo [PR #247264](https://github.com/microsoft/vscode/pull/247264)
- [@sfaut](https://github.com/sfaut): Fix PHP f* files functions signatures [PR #246964](https://github.com/microsoft/vscode/pull/246964)
- [@thegecko (Rob Moran)](https://github.com/thegecko): Add disassembly view context menu [PR #212500](https://github.com/microsoft/vscode/pull/212500)
- [@theskcd](https://github.com/theskcd): [vscode] Decorations from #file is much better and does not break on new line [PR #231948](https://github.com/microsoft/vscode/pull/231948)
- [@tjcork (tjcork)](https://github.com/tjcork): Use parameter expansion to fetch envs for envVarCollections in shellIntegration-bash.sh [PR #245264](https://github.com/microsoft/vscode/pull/245264)
- [@tmm1 (Aman Karmani)](https://github.com/tmm1): tsb: small build improvements [PR #237450](https://github.com/microsoft/vscode/pull/237450)
- [@Victuracor (Victuracor)](https://github.com/Victuracor): Fix a typo in extensions/typescript-language-features/package.nls.json [PR #245713](https://github.com/microsoft/vscode/pull/245713)
- [@whistlegraph (jeffrey)](https://github.com/whistlegraph): fixes issue #662 (enables Pointer Lock Web API) [PR #210875](https://github.com/microsoft/vscode/pull/210875)
- [@wolfgang42 (Wolfgang Faust)](https://github.com/wolfgang42): feat: markdown-basics snippets: quote all lines [PR #246871](https://github.com/microsoft/vscode/pull/246871)
- [@zobo (Damjan Cvetko)](https://github.com/zobo): Also replace keys in object within variable substitution [PR #245989](https://github.com/microsoft/vscode/pull/245989)

Contributions to `vscode-css-languageservice`:

- [@AlterNT (NTPS)](https://github.com/AlterNT): Support `@scope` [PR #434](https://github.com/microsoft/vscode-css-languageservice/pull/434)
- [@rviscomi (Rick Viscomi)](https://github.com/rviscomi): Add Baseline status to hovercards [PR #428](https://github.com/microsoft/vscode-css-languageservice/pull/428)

Contributions to `vscode-js-debug`:

- [@mikaelwaltersson (Mikael Waltersson)](https://github.com/mikaelwaltersson): Fix expansion of "floating" WASM variables in repl/watch + readMemory when WASM memory is SharedArrayBuffer [PR #2199](https://github.com/microsoft/vscode-js-debug/pull/2199)

Contributions to `vscode-json-languageservice`:

- [@fengzilong (MO)](https://github.com/fengzilong): feat: make newJSONDocument and JSONDocument consistent [PR #259](https://github.com/microsoft/vscode-json-languageservice/pull/259)

Contributions to `vscode-jupyter`:

- [@alexfanqi (Alex Fan)](https://github.com/alexfanqi): change the scope of excludeUserSitePackages to window [PR #16377](https://github.com/microsoft/vscode-jupyter/pull/16377)
- [@realDuang (Duang)](https://github.com/realDuang): fix: repair python code escaping path in environment service [PR #16518](https://github.com/microsoft/vscode-jupyter/pull/16518)

Contributions to `vscode-mypy`:

- [@tdscheper (Tommy Scheper)](https://github.com/tdscheper): When cwd config option is ${nearestConfig}, look for all of mypy.ini, .mypy.ini, pyproject.toml, setup.cfg [PR #357](https://github.com/microsoft/vscode-mypy/pull/357)

Contributions to `vscode-notebook-renderers`:

- [@marthacryan (Martha Cryan)](https://github.com/marthacryan): Update plotly.js version to 3.0.0 [PR #230](https://github.com/microsoft/vscode-notebook-renderers/pull/230)

Contributions to `vscode-pull-request-github`:

- [@kabel (Kevin Abel)](https://github.com/kabel): Fix merge email confirmation when git config fails [PR #6797](https://github.com/microsoft/vscode-pull-request-github/pull/6797)
- [@timrogers (Tim Rogers)](https://github.com/timrogers): When `copilot-swe-agent` is the author of a comment, render with the Copilot identity [PR #6794](https://github.com/microsoft/vscode-pull-request-github/pull/6794)

Contributions to `vscode-python-debugger`:

- [@rchiodo (Rich Chiodo)](https://github.com/rchiodo): Allow autoReload in attach configurations [PR #676](https://github.com/microsoft/vscode-python-debugger/pull/676)

Contributions to `vscode-python-environments`:

- [@InSyncWithFoo (InSync)](https://github.com/InSyncWithFoo): fix: clarify that `showSkipOption` also applies to uninstallations [PR #288](https://github.com/microsoft/vscode-python-environments/pull/288)

Contributions to `language-server-protocol`:

- [@hippietrail (Andrew Dunbar)](https://github.com/hippietrail): several grammar fixes [PR #2123](https://github.com/microsoft/language-server-protocol/pull/2123)
- [@imbant (imbant)](https://github.com/imbant): Ensure document state synchronization before client requests [PR #2017](https://github.com/microsoft/language-server-protocol/pull/2017)
- [@ocfbnj](https://github.com/ocfbnj): Add thrift-ls for Thrift [PR #2128](https://github.com/microsoft/language-server-protocol/pull/2128)
- [@rtorralba (rtorralba)](https://github.com/rtorralba)
  - Add ZX Basic language server to the implementors list [PR #2121](https://github.com/microsoft/language-server-protocol/pull/2121)
  - Replace ZX Basic with Boriel Basic language server into the implement… [PR #2125](https://github.com/microsoft/language-server-protocol/pull/2125)

Contributions to `monaco-editor`:

- [@RoccoC (Rocco Cataldo)](https://github.com/RoccoC): Update webpack plugin to support module workers [PR #4742](https://github.com/microsoft/monaco-editor/pull/4742)

<a id="scroll-to-top" role="button" title="Scroll to top" aria-label="scroll to top" href="#"><span class="icon"></span></a>
<link rel="stylesheet" type="text/css" href="css/inproduct_releasenotes.css"/>
