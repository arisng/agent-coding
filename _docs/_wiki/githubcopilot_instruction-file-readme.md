# All about custom instructions for GitHub Copilot

- [All about custom instructions for GitHub Copilot](#all-about-custom-instructions-for-github-copilot)
  - [Prompt and instructions files](#prompt-and-instructions-files)
    - [Key Differences](#key-differences)
    - [Practical Use Cases](#practical-use-cases)
    - [Instructions files](#instructions-files)
    - [Improvements and notes](#improvements-and-notes)
  - [Can I apply multiple instructions file in a single chat?](#can-i-apply-multiple-instructions-file-in-a-single-chat)
  - [Specify settings for each type of custom instruction](#specify-settings-for-each-type-of-custom-instruction)
  - [Custom instructions example](#custom-instructions-example)
    - [Tips for defining custom instructions](#tips-for-defining-custom-instructions)

## Prompt and instructions files

You can tailor your AI experience in VS Code to your specific coding practices and technology stack by using Markdown-based instructions and prompt files. We've aligned the implementation and usage of these two related concepts, however they each have distinct purposes.

### Key Differences

| Aspect | Prompt Files | Instruction Files |
|-------|---------------|---------------------|
| **Purpose** | Standalone chat requests for specific tasks | Context-based guidelines for code style, frameworks, etc. |
| **File Type** | `.prompt.md` | `.instructions.md` |
| **Metadata** | `mode`, `tools` | `applyTo`, `description` |
| **Usage** | Run via `/` command, play button | Manually attached or auto-included via `applyTo` |
| **Examples** | Generate release notes (agent mode) | Code style rules for TypeScript files |
| **Execution** | Immediate execution | Automatic inclusion for matching file patterns |

### Practical Use Cases

**Prompt Files**  

- prioritize task-specific execution (e.g., `agent` mode).
- Use `/` to run pre-defined chat requests (e.g., `~/prompt-files/generate-release-notes.prompt.md`).  
- Ideal for reusable tasks like code generation or security reviews.  

**Instruction Files**  

- focus on contextual guidelines, enabling AI to adapt to your coding style.
- Define rules (e.g., brace formatting) via `applyTo` glob patterns.  
- Automatically applied to files matching the pattern (e.g., `**/*.ts`).

### Instructions files

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

### Improvements and notes

- Instructions and prompt files now have their own language IDs, configurable in the _language mode_ dialog for any file open document ("Prompt" and "Instructions" respectively). This allows, for instance, using untitled documents as temporary prompt files before saving them as files to disk.
- We renamed the **Chat: Use Prompt** command to **Chat: Run Prompt**. Furthermore, the command now runs the selected prompt _immediately_, as opposed to attaching it as chat context as it did before.
- Both file types now also support the `description` metadata in their headers, providing a common place for short and user-friendly prompt summaries. In the future, this header is planned to be used along with the `applyTo` header as the rule that determines if the file needs to be auto-included with chat requests (for example, `description: 'Code style rules for front-end components written in TypeScript.'`)

## Can I apply multiple instructions file in a single chat?

Yes! You can apply multiple `.instructions.md` files in a single chat session. Here’s how it works:

- **Manual Attachment**: In the Chat view, select **Add Context > Instructions** and pick multiple instruction files.
- **Command Palette**: Use `Chat: Attach Instructions` (`Ctrl+Shift+P`) and select multiple files.
- **Automatic Inclusion**: If the `.instructions.md` files have an `applyTo` property matching the file you’re working on, they will automatically be included.
- **Workspace & User Instructions**: You can combine workspace-level instructions (`.github/instructions`) and user-level instructions (stored in your VS Code profile).

If multiple instruction files are applied, there’s no specific priority order, so **ensure they don’t conflict** with each other.

Would you like help organizing multiple instruction files efficiently? 🚀

## Specify settings for each type of custom instruction

You can also configure custom instructions in your user or workspace settings. There are specific settings for different scenarios. The instructions are automatically applied for the specific task.

The following table lists the settings for each type of custom instruction.

| Type of instruction | Setting name |
|----------------------|--------------|
| Code generation | `setting(github.copilot.chat.codeGeneration.instructions)` |
| Test generation | `setting(github.copilot.chat.testGeneration.instructions)` |
| Code review | `setting(github.copilot.chat.reviewSelection.instructions)` |
| Commit message generation | `setting(github.copilot.chat.commitMessageGeneration.instructions)` |
| Pull request title and description generation | `setting(github.copilot.chat.pullRequestDescriptionGeneration.instructions)` |

You can define the custom instructions as text in the settings value or reference an external file in your workspace.

The following code snippet shows how to define a set of instructions in the `settings.json` file. To define instruction directly in settings, configure the `text` property. To reference an external file, configure the `file` property.

```json
  "github.copilot.chat.codeGeneration.instructions": [
    {
      "text": "Always add a comment: 'Generated by Copilot'."
    },
    {
      "text": "In TypeScript always use underscore for private field names."
    },
    {
      "file": "general.instructions.md" // import instructions from file `general.instructions.md`
    },
    {
      "file": "db.instructions.md" // import instructions from file `db.instructions.md`
    }
  ],
```

## Custom instructions example

The following example demonstrates custom instructions for code generation:

- Define general coding guidelines in a `.github/instructions/general-coding.instructions.md` file that apply to all code:

    ```markdown
    ---
    applyTo: "**"
    ---
    # Project general coding standards

    ## Naming Conventions
    - Use PascalCase for component names, interfaces, and type aliases
    - Use camelCase for variables, functions, and methods
    - Prefix private class members with underscore (_)
    - Use ALL_CAPS for constants

    ## Error Handling
    - Use try/catch blocks for async operations
    - Implement proper error boundaries in React components
    - Always log errors with contextual information
    ```

- Define TypeScript and React coding guidelines in a `.github/instructions/typescript-react.instructions.md` file that apply to TypeScript and React code, general coding guidelines are inherited:

    ```markdown
    ---
    applyTo: "**/*.ts,**/*.tsx"
    ---
    # Project coding standards for TypeScript and React

    Apply the [general coding guidelines](./general-coding.instructions.md) to all code.

    ## TypeScript Guidelines
    - Use TypeScript for all new code
    - Follow functional programming principles where possible
    - Use interfaces for data structures and type definitions
    - Prefer immutable data (const, readonly)
    - Use optional chaining (?.) and nullish coalescing (??) operators

    ## React Guidelines
    - Use functional components with hooks
    - Follow the React hooks rules (no conditional hooks)
    - Use React.FC type for components with children
    - Keep components small and focused
    - Use CSS modules for component styling
    ```

### Tips for defining custom instructions

- Keep your instructions short and self-contained. Each instruction should be a single, simple statement. If you need to provide multiple pieces of information, use multiple instructions.

- Don't refer to external resources in the instructions, such as specific coding standards.

- Split instructions into multiple files. This approach is useful for organizing instructions by topic or type of task.

- Make it easy to share custom instructions with your team or across projects by storing your instructions in instruction files. You can also version control the files to track changes over time.

- Use the `applyTo` property in the instruction file header to automatically apply the instructions to specific files or folders.

- Reference custom instructions in your prompt files to keep your prompts clean and focused, and to avoid duplicating instructions for different tasks.
