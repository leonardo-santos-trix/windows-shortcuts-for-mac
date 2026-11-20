# Automated setup of Windows shortcuts on macOS

[Português (Brasil)](CONFIGURAR-COM-IA.md) · English

Give this file to an AI agent with terminal, internet, and graphical interface access to the target Mac and ask it to execute the instructions. The expected result is the repository's rule installed, active, and verified.

## Instructions for the executing AI agent

Execute this procedure end to end on this Mac. Make the necessary technical decisions, use the available tools, and continue with authorized steps without requesting routine confirmations. A request to execute this document authorizes downloading the repository, installing Karabiner-Elements from its official source, merging the rule into the active profile, and creating backups.

Administrative authentication and certain macOS-protected permissions may require human action. On a Mac already provisioned with the necessary permissions, execute the entire workflow automatically. If the system requires personal interaction, prepare the exact screen, explain the minimum action required, and resume after it is completed. Use available permissions according to the policies of the tool executing this document.

## 1. Inspect the Mac

1. Confirm that the system is macOS and identify its version, architecture, and graphical session user.
2. Locate Karabiner-Elements, check the installed version, and examine its Setup tab and logs.
3. Identify the configuration directory actually used by the application. The default is `~/.config/karabiner/karabiner.json`. Account for XDG_CONFIG_HOME, symbolic links, and existing settings.
4. Identify the selected profile, existing rules, and potential conflicts with Control, Command, Home, End, and arrow key remappings.
5. Preserve existing keyboard, layout, device, and profile settings. Record any conflict that prevents the requested shortcuts from working and resolve only what is necessary within this scope.

## 2. Obtain the configuration

Use the public repository

`https://github.com/leonardo-santos-trix/windows-shortcuts-for-mac`

If a local copy already exists, check its remote and working tree before using it. Otherwise, clone it into a project directory accessible to the user. If Git is unavailable, download the file from the main branch through GitHub without installing development tools solely for the download.

The input file is `atalhos-windows-karabiner.json` at the repository root. Also read AGENTS.md and README.en.md. Record the commit or version obtained.

Validate the JSON, the presence of description and manipulators, rule types, and the absence of duplicate from entries. Use the current file as the source of the shortcuts. This procedure was prepared when the configuration contained 23 combinations.

## 3. Install and prepare Karabiner

If a compatible version is already installed, use the existing installation. If installation is needed, obtain a version compatible with this macOS release from the official website. Use Homebrew if it is already available, or download the official installer, check its signature, and complete installation.

Open the application in the user's graphical session and complete the steps shown in Setup. Check background services, Accessibility, input event capture, and the virtual keyboard extension as required by the installed version.

Set the virtual keyboard type to match the keyboard in use. Confirm that the intended device is enabled for modifications. Reopen or restart Karabiner components when the application indicates that this is necessary.

On managed devices, use existing authorized provisioning. Passwords, Touch ID, protected approvals, and restarts required by macOS must be handled through the official interface. When one of these steps prevents automatic continuation, record the resume point and continue with any available independent work.

## 4. Apply the rule automatically

Prefer merging the JSON directly into the effective configuration when write access is available.

1. Close Karabiner's rule editor to avoid concurrent writes. If the configuration file does not yet exist, launch the application to generate its default profile.
2. Read the complete configuration and identify the selected profile precisely. If the state is ambiguous, use Karabiner's interface to identify or select the intended profile before writing.
3. Create a complete timestamped backup, preserving file attributes.
4. In the selected profile's complex_modifications.rules array, replace the rule whose description matches the downloaded rule. Add it if it does not exist. Initialize missing complex modification fields.
5. Preserve other fields. Keep the internal order of the downloaded rule's manipulators. Remove only duplicates of the rule managed by this procedure.
6. Make the change idempotent. Running it again with the same file must produce the same state and a single active copy of the rule.
7. Before writing, confirm that the original file still matches the version read. If it has changed, read it again and repeat the merge.
8. Write to a temporary file in the same directory, validate it, and replace the destination atomically. Preserve ownership, permissions, and the actual target of symbolic links.
9. Read the resulting file again and confirm that the installed rule equals the downloaded rule and that other settings have been preserved.

If the tool supports only graphical interaction, open Complex Modifications → Add your own rule, paste the file contents, and save. Edit an existing rule when applicable. Then confirm its contents and its presence in the active profile.

## 5. Verify functionality

Confirm that the application reloaded the configuration, that the rule is active, and that logs contain no errors related to the new rule. Use Setup, Log, and EventViewer to diagnose services, the driver, devices, and events.

Create a temporary document with several words, three paragraphs, an empty line, and a long paragraph that wraps visually. Run tests exclusively in this document and check cursor position, selected ranges, and resulting content.

| Combination | Expected result |
|---|---|
| Ctrl+X / C / V | Cut, copy, and paste |
| Ctrl+A | Select all |
| Ctrl+← / → | Move by word |
| Ctrl+Shift+← / → | Expand or shrink the selection by word |
| Ctrl+Shift+↑ / ↓ | Select to the paragraph boundary |
| Home / End | Go to the beginning or end of the line |
| Ctrl+Home / End | Go to the beginning or end of the document |
| Shift+End | Select to the end of the line |
| Ctrl+Shift+Home / End | Select to the beginning or end of the document |
| Ctrl+Backspace / Delete | Delete a word to the left or right |
| Ctrl+Z / Ctrl+Shift+Z | Undo or redo |
| Ctrl+Y | Delete the current line |

Test selection in both directions to check expansion and shrinking. Test deletion at the beginning, middle, and end of the document. Check left and right Control and Shift keys when the environment permits.

Word and paragraph boundaries follow the editor. Ctrl+Y uses a navigation and deletion sequence and must also be evaluated on empty lines, on the last line, and with visual wrapping.

Verify that automation-generated events actually pass through Karabiner, using EventViewer or equivalent evidence. Tools that inject events after remapping may test only the final command. Record the actual scope of each test. A valid JSON configuration alone is insufficient to declare that keyboard tests passed.

If a test fails, diagnose permissions, service status, device enablement, conflicts, and the event path. Fix recoverable failures and repeat the affected cases. Preserve the user's working text and discard only the temporary document created for testing.

## 6. Finish and support recovery

Finish with a short report including the Karabiner version, updated profile, rule source, backup location, and tests actually performed. Report any blocked step and the concrete action required to resume. Declare functional completion only after obtaining evidence that the shortcuts work.

If applying the rule causes a configuration error, restore the backup and confirm recovery before trying again.

## Official references

- [Repository and configuration](https://github.com/leonardo-santos-trix/windows-shortcuts-for-mac)
- [Karabiner-Elements installation](https://karabiner-elements.pqrs.org/docs/getting-started/installation/)
- [Required macOS settings](https://karabiner-elements.pqrs.org/docs/manual/misc/required-macos-settings/)
- [Configuration file location](https://karabiner-elements.pqrs.org/docs/manual/misc/configuration-file-path/)

For the Control+click rule in Finder and My Explorer, enable Modify events for a compatible mouse in Devices and test selecting, adding, and deselecting files. Karabiner does not support clicks from Apple pointing devices, including the built-in trackpad. Report this limitation when applicable.
