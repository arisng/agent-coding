# Profiles in Visual Studio Code



## Common Questions

### Where are profiles kept?

Profiles are stored under your User configurations similar to your user settings and keyboard shortcuts.

* **Windows** `%APPDATA%\Code\User\profiles`
* **macOS** `$HOME/Library/Application\ Support/Code/User/profiles`
* **Linux** `$HOME/.config/Code/User/profiles`

If you are using the [Insiders](/insiders) version, the intermediate folder name is `Code - Insiders`.

### What is a Temporary Profile?

A Temporary Profile is a profile that is not saved across VS Code sessions. You create a Temporary Profile via the **Profiles: Create a Temporary Profile** command in the Command Palette. The Temporary Profile starts as an Empty Profile and has an automatically generated name (such as **Temp 1**). You can modify the profile settings and extensions, use the profile for the lifetime of your VS Code session, but it will be deleted once you close VS Code.

Temporary Profiles are useful if you want to try a new configuration or test an extension without modifying your default or existing profile. Restarting VS Code reenables the current profile for your workspace.

### Can I inherit settings from another profile?

Currently, it's not possible to inherit settings from another profile, where you override specific settings and keep the rest of the settings from the other profile. We're tracking this [feature request in the vscode repo](https://github.com/microsoft/vscode/issues/188612).

When you create a new profile, you can choose to copy the settings from another or the default profile. This creates a copy of the settings in the new profile but does not maintain a link to the profile you used as a source.

### How can I remove the profile from my project?

You can set your project back to the Default Profile. If you'd like to remove all profile workspace associations, you can use the **Developer: Reset Workspace Profiles Associations**, which will set all local folders currently assigned a profile back to the Default Profile. **Reset Workspace Profiles Associations** does not delete any existing profiles.

### Why are some settings not exported when exporting a profile?

When exporting profiles, machine-specific settings are not included because these settings would not be applicable on another machine. For example, settings that point to local paths are not included.

### Why are templates not available when creating a new profile?

Profile templates are hosted externally by VS Code and you can only download and apply a template when you are connected to the internet. Make sure to check your internet connection if you notice that profile templates are not available.