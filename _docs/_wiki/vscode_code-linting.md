# how to configure code formatting for .razor file in blazor project

VS Code: To configure code formatting for `.razor` files in a Blazor project, you can use the following settings:

1. Enable or disable the default Razor formatter using the **razor.format.enable** setting.
2. Optionally, choose to use the new Razor formatting engine with the **razor.languageServer.useNewFormattingEngine** setting.
3. You can also configure if braces for `@code` or `@functions` blocks appear on the next line using **razor.format.codeBlockBraceOnNextLine**.
4. To automatically format `.razor` files on save, enable the **editor.formatOnSave** setting.
5. To automatically format the line after typing, enable the **editor.formatOnType** setting.
6. If you have multiple formatters installed, you can set a default formatter for all files using **editor.defaultFormatter**. For Razor files specifically, ensure that the C# extension (which provides Razor tooling) is selected or that no other formatter is overriding it for Razor files.

```json
{
  "razor.format.enable": "true",
  "razor.languageServer.useNewFormattingEngine": "true",
  "razor.format.codeBlockBraceOnNextLine": "false",
  "editor.formatOnSave": "true",
  "editor.formatOnType": "false",
  "editor.defaultFormatter": "ms-dotnettools.csharp"
}
```

To format a selection, use the **Format Selection** command. The default keybinding is `Ctrl+K Ctrl+F`.
