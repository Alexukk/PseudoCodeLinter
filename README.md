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

### Option 1: From a release (recommended)

1. Go to the [**Releases**](https://github.com/Alexukk/PseudoCodeLinter/releases) page and download the latest `vscode-psdc-x.y.z.vsix` file.
2. Install it in one of two ways:

   **From the VS Code interface**
   1. Open VS Code and go to the **Extensions** view (`Ctrl+Shift+X`).
   2. Click the **`···`** menu in the top right corner of the Extensions panel.
   3. Choose **Install from VSIX...** and select the downloaded file.

   **From the terminal**
   ```bash
   code --install-extension vscode-psdc-0.1.0.vsix
   ```
3. Reload VS Code if it asks you to.
4. Create or open any file with the `.psdc` extension. Highlighting turns on automatically.

### Option 2: Build it yourself

You need [Node.js](https://nodejs.org/) installed.

```bash
git clone https://github.com/Alexukk/PseudoCodeLinter.git
cd PseudoCodeLinter
npx @vscode/vsce package
code --install-extension vscode-psdc-0.1.0.vsix
```

### Option 3: Run without installing (for development)

```bash
git clone https://github.com/Alexukk/PseudoCodeLinter.git
code --extensionDevelopmentPath="/full/path/to/PseudoCodeLinter"
```

A new VS Code window opens with the extension loaded straight from the folder. After editing the grammar, press `Ctrl+R` in that window to reload it.

### Uninstall

Open the **Extensions** view, find **Pseudocode (.psdc)**, and click **Uninstall**. Or run:

```bash
code --uninstall-extension alexukk.vscode-psdc
```

## Troubleshooting

| Problem | What to do |
|---|---|
| Nothing is highlighted | Check that the file ends with `.psdc`. Look at the language indicator in the bottom right corner of VS Code; it should say **Pseudocode**. If not, click it and choose it manually. |
| Colors look wrong or some words stay white | Highlight colors come from your color theme. Put the cursor on a word and run **Developer: Inspect Editor Tokens and Scopes** to see which scope it got. Some themes simply don't color certain scopes. |
| Old behavior after an update | Uninstall the previous version, then restart VS Code and install the new one. |

## Roadmap

- [ ] Snippets for common blocks (`if`, `for`, `while`, `function`)
- [ ] A forgiving linter: unmatched blocks (`if` without `end if`), unclosed brackets, and other gentle warnings
- [ ] More comment styles and keyword sets
- [ ] Marketplace release

Ideas and bug reports are welcome. Open an [issue](https://github.com/Alexukk/PseudoCodeLinter/issues) with a small `.psdc` example that doesn't look right.

## Contributing

1. Fork the repository.
2. Edit `syntaxes/pseudocode.tmLanguage.json` (highlighting rules) or `language-configuration.json` (brackets, comments, indentation).
3. Test with `code --extensionDevelopmentPath=...` as shown above.
4. Open a pull request with a short description and an example of the code your change affects.

## License

[MIT](LICENSE)
