<div align="center">

# Pseudocode (.psdc) for VS Code

**Clean, forgiving syntax highlighting for pseudocode.**
Write it the way you think it: `IF`, `if`, `end if`, `<-`, `:=`, `→`. It all just works.
</div>

---

## Why?

Pseudocode has no standard. Every course, book and person writes it a little differently: `IF ... THEN ... END IF`, `if ... then ... fi`, `x <- 5`, `x := 5`, `x = 5`. Most highlighters either don't know the language or get confused when the code isn't perfectly formed.

This extension is built around one idea: **never be wrong about what you meant, and never break because of a typo.** It highlights what it recognizes and quietly ignores the rest.

## Features

- **Case-insensitive keywords.** `IF`, `If` and `if` are all highlighted the same way.
- **Wide keyword coverage.** Control flow (`if`, `else`, `for each`, `while`, `repeat`, `until`, `switch`, `try`/`catch`, `end if`, `endfor`, ...), declarations (`function`, `class`, `let`, `const`, ...), modules (`import`, `from`, `use`, ...), async keywords and more.
- **Error-tolerant strings.** An unclosed quote only affects its own line, never the rest of the file.
- **Three comment styles.** `// line`, `# line` and `/* block */`.
- **Many operator styles.** Assignment with `<-`, `:=`, `=`; comparison with `==`, `!=`, `<>`; plus unicode `←`, `→`, `≠`, `≤`, `≥`; word operators like `and`, `or`, `not`, `mod`, `div`.
- **Smart names.** Function and class names are highlighted at their definition and at call sites. `UPPER_CASE` names are treated as constants.
- **Editor comfort.** Bracket matching, auto-closing quotes and brackets, comment toggling (`Ctrl+/`) and automatic indentation after blocks like `then`, `do`, `else`.

## Example

```
// Find the maximum value in an array
FUNCTION findMax(arr: int[]) RETURNS int
    max <- arr[0]

    FOR EACH x IN arr DO
        IF x > max THEN
            max <- x
        END IF
    END FOR

    RETURN max
END FUNCTION

PRINT("Max is: " + findMax([3, 9, 4]))
```

<!-- Add a screenshot of the highlighting here:
![Screenshot](images/screenshot.png)
-->

## Installation

The extension is installed straight from this repository. No build tools and no accounts are needed.

### 1. Download

Pick one:

- **Download ZIP:** open the [Releases](https://github.com/Alexukk/PseudoCodeLinter/releases) page, choose the latest release and download **Source code (zip)**. Then unzip it.
- **Or clone with Git:**
  ```bash
  git clone https://github.com/Alexukk/PseudoCodeLinter.git
  ```

You should end up with a folder that contains `package.json`, `language-configuration.json` and a `syntaxes` folder directly inside it.

### 2. Copy the folder into VS Code's extensions directory

Copy that folder into the extensions directory and rename it to **`alexukk.vscode-psdc-0.1.0`**.

| System | Extensions directory |
|---|---|
| Windows | `%USERPROFILE%\.vscode\extensions` |
| macOS / Linux | `~/.vscode/extensions` |

> **Windows tip:** press `Win+R`, paste `%USERPROFILE%\.vscode\extensions` and press Enter to open the folder.

The result should look like this:

```
.vscode/extensions/
└── alexukk.vscode-psdc-0.1.0/
    ├── package.json
    ├── language-configuration.json
    └── syntaxes/
        └── pseudocode.tmLanguage.json
```

### 3. Restart VS Code

Close **all** VS Code windows and open it again. Create or open any file with the `.psdc` extension and highlighting turns on automatically. The language indicator in the bottom right corner should say **Pseudocode**.

### Updating

Delete the old `alexukk.vscode-psdc-*` folder from the extensions directory, copy the new version in the same way, and restart VS Code.

### Uninstall

Close VS Code, delete the `alexukk.vscode-psdc-0.1.0` folder from the extensions directory, and start VS Code again.

### Try it without installing

If you only want to test it or work on the grammar, run VS Code with the extension loaded directly from the folder:

```bash
code --extensionDevelopmentPath="/full/path/to/PseudoCodeLinter"
```

A new VS Code window opens with the extension active. After editing the grammar, press `Ctrl+R` in that window to reload it.

## Troubleshooting

| Problem | What to do |
|---|---|
| Nothing is highlighted | Check that the file ends with `.psdc`. Click the language indicator in the bottom right corner of VS Code and choose **Pseudocode** manually. Make sure `package.json` sits directly inside `alexukk.vscode-psdc-0.1.0`, not in a nested folder. |
| The extension doesn't show up after copying | Close **every** VS Code window (check the system tray too) and start it again. |
| Colors look wrong or some words stay white | Highlight colors come from your color theme. Put the cursor on a word and run **Developer: Inspect Editor Tokens and Scopes** to see which scope it got. Some themes simply don't color certain scopes. |
| Old behavior after an update | Make sure only one `alexukk.vscode-psdc-*` folder exists in the extensions directory. |

## Roadmap

- [ ] Snippets for common blocks (`if`, `for`, `while`, `function`)
- [ ] A forgiving linter: unmatched blocks (`if` without `end if`), unclosed brackets, and other gentle warnings
- [ ] More comment styles and keyword sets

Ideas and bug reports are welcome. Open an [issue](https://github.com/Alexukk/PseudoCodeLinter/issues) with a small `.psdc` example that doesn't look right.

## Contributing

1. Fork the repository.
2. Edit `syntaxes/pseudocode.tmLanguage.json` (highlighting rules) or `language-configuration.json` (brackets, comments, indentation).
3. Test with `code --extensionDevelopmentPath=...` as shown above.
4. Open a pull request with a short description and an example of the code your change affects.
