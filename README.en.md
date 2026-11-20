# Windows shortcuts for Mac

[Português (Brasil)](README.md) · English

Control-based shortcuts for macOS using Karabiner-Elements. The configuration includes navigation, text selection, copy, cut, and paste, plus a custom Ctrl+Y shortcut to delete the current line.

## Shortcuts

| Keys | Action |
|---|---|
| Ctrl+X | Cut |
| Ctrl+C | Copy |
| Ctrl+V | Paste |
| Ctrl+A | Select all |
| Ctrl+Z | Undo |
| Ctrl+Shift+Z | Redo |
| Ctrl+Backspace | Delete a word to the left |
| Ctrl+Delete | Delete a word to the right |
| Ctrl+← | Move one word to the left |
| Ctrl+→ | Move one word to the right |
| Ctrl+Shift+← | Select one word to the left |
| Ctrl+Shift+→ | Select one word to the right |
| Ctrl+Shift+↑ | Select to the beginning of the paragraph |
| Ctrl+Shift+↓ | Select to the end of the paragraph |
| Home | Beginning of the line |
| End | End of the line |
| Ctrl+Home | Beginning of the document |
| Ctrl+End | End of the document |
| Shift+End | Select to the end of the line |
| Ctrl+Shift+End | Select to the end of the document |
| Ctrl+Shift+Home | Select to the beginning of the document |
| Ctrl+Y | Delete the current line |
| Ctrl+click | Toggle file selection in Finder |

## Installation

For an AI agent with access to the Mac, use the [automated setup procedure](SETUP-WITH-AI.en.md).

1. Install [Karabiner-Elements from its official website](https://karabiner-elements.pqrs.org/).
2. Complete the steps in Setup for background services, Accessibility, and the virtual keyboard extension.
3. Select the desired profile and open Complex Modifications → Add your own rule.
4. Paste the contents of `atalhos-windows-karabiner.json` and save.
5. If a rule with the same name already exists, edit that rule to update its contents.
6. Test the shortcuts in a temporary document.

The file contains a single rule. Merge it into the existing profile and preserve the other settings. Back up `~/.config/karabiner/karabiner.json` before editing that file.

## Behavior and verification

Both left and right Control and Shift keys are supported. Remappings apply to the combinations in the table.

Word selection uses Option+Shift+←/→, and paragraph selection uses Option+Shift+↑/↓. Selection preserves the editor's anchor, allowing the selected range to expand or shrink. Word deletion uses Option+Backspace and Option+Delete. Redo uses Command+Shift+Z. Word and paragraph boundaries follow the editor's behavior.

The mappings were checked in the JSON and synchronized with the active profile. On November 19, 2026, automated testing in TextEdit did not confirm word deletion. Verification with a physical keyboard remains pending.

Ctrl+Y sends Command+←, Command+Shift+→, Shift+→, and Backspace to select and delete the line and its following line break, when present. Line navigation depends on the application and may follow visual lines in wrapped text. Application behavior still requires practical validation.

To validate the JSON and detect duplicate entries, run this command from the project directory

```sh
ruby -rjson -e 'r = JSON.parse(File.read("atalhos-windows-karabiner.json")); m = r.fetch("manipulators"); abort "Duplicate entries" unless m.map { |x| x.fetch("from") }.uniq.size == m.size; puts "#{m.size} valid shortcuts"'
```

## Maintenance

Edit the versioned rule, validate it, and apply the updated contents in Karabiner. Record changes in Git commits. To disable the remappings, disable or remove the rule in Complex Modifications.

For Control+click, enable Modify events for the mouse in Devices. The rule applies to Finder. Apple pointing devices, including the built-in trackpad, are unsupported by this Karabiner remapping.
