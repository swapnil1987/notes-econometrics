# VS Code + Quarto Quick Reference

## Essential Keyboard Shortcuts

### Quarto-Specific

| Action | Windows/Linux | Mac |
|--------|---------------|-----|
| Render document | `Ctrl+Shift+K` | `Cmd+Shift+K` |
| Preview | `Ctrl+Shift+K` | `Cmd+Shift+K` |
| Insert code chunk | `Ctrl+Alt+I` | `Cmd+Option+I` |

### General VS Code

| Action | Windows/Linux | Mac |
|--------|---------------|-----|
| Command palette | `Ctrl+Shift+P` | `Cmd+Shift+P` |
| Open terminal | `Ctrl+` ` | `Cmd+` ` |
| Save file | `Ctrl+S` | `Cmd+S` |
| Find in file | `Ctrl+F` | `Cmd+F` |
| Find in project | `Ctrl+Shift+F` | `Cmd+Shift+F` |

## Quarto Markdown Syntax

### Headers
```markdown
# Chapter Title
## Section
### Subsection
```

### Math
```markdown
Inline: $y = X\beta + \epsilon$

Display (numbered):
$$
\hat{\beta} = (X^TX)^{-1}X^Ty
$$ {#eq-ols}

Reference: See @eq-ols
```

### Code Blocks

Basic:
````markdown
```{{python}}
import numpy as np
x = np.array([1, 2, 3])
```
````

With options:
````markdown
```{{python}}
#| echo: false
#| warning: false
#| fig-cap: "My figure"
#| label: fig-myplot

import matplotlib.pyplot as plt
plt.plot([1, 2, 3])
```
````

### Callouts

```markdown
::: {.callout-note}
## Optional Title
Content here
:::

Types: note, warning, important, tip, caution
```

### Cross-References

```markdown
See @sec-intro for introduction
As shown in @eq-regression
Figure @fig-plot displays...
Table @tbl-summary shows...
```

### Citations

```markdown
@author2020 showed that...
Multiple [@author2020; @other2021]
```

## Code Chunk Options

Common options (add after `{python}`):

```markdown
#| echo: false          # Hide code, show output
#| eval: false          # Show code, don't run
#| output: false        # Run code, hide output
#| warning: false       # Suppress warnings
#| message: false       # Suppress messages
#| code-fold: true      # Collapsible code
#| label: fig-name      # For cross-references
#| fig-cap: "Caption"   # Figure caption
#| tbl-cap: "Caption"   # Table caption
```

## File Organization

```
chapter.qmd structure:
├── YAML header (optional)
├── Chapter title (# Title)
├── Introduction
├── Sections (## Section)
│   ├── Subsections (### Subsection)
│   ├── Math
│   ├── Code
│   └── Figures
└── Exercises
```

## Terminal Commands

```bash
# Start preview (live reload)
quarto preview

# Render entire book
quarto render

# Render single file
quarto render chapter.qmd

# Check installation
quarto check

# Create new project
quarto create project book mybook

# Get help
quarto --help
```

## Git Workflow

```bash
# See what changed
git status
git diff

# Stage and commit
git add .
git commit -m "Updated chapter 3"

# Push to GitHub (triggers deployment)
git push

# Pull latest changes
git pull
```

## Pro Tips

1. **Live Preview**: Keep `quarto preview` running - it auto-refreshes on save

2. **Execution Caching**: Quarto caches Python outputs. If you want to force re-execution:
   ```bash
   quarto render --execute-dir reset
   ```

3. **Python Environment**: Code runs in the same environment. Set variables in one chunk, use in another:
   ````markdown
   ```{{python}}
   x = 10
   ```
   
   ```{{python}}
   print(x)  # Works!
   ```
   ````

4. **Debug Mode**: If code fails, check the terminal for error messages

5. **Include External Code**:
   ````markdown
   ```{{python}}
   #| file: scripts/analysis.py
   ```
   ````

## Useful Extensions

Install in VS Code:

- **Quarto** (required)
- **Python** (for syntax highlighting)
- **Jupyter** (for notebook support)
- **GitLens** (advanced Git features)

## Troubleshooting

**Preview not updating?**
- Save file (Ctrl+S / Cmd+S)
- Check terminal for errors

**Code not executing?**
- Check Python is installed: `python --version`
- Check packages: `pip list`

**Math not rendering?**
- Check for unmatched `$` symbols
- Use `\\` for backslashes in LaTeX

**Citations not working?**
- Check `references.bib` exists
- Verify BibTeX syntax
- Add to `_quarto.yml`: `bibliography: references.bib`

## Learning Resources

- Quarto Guide: https://quarto.org/docs/guide/
- Markdown Basics: https://quarto.org/docs/authoring/markdown-basics.html
- Python Chunks: https://quarto.org/docs/computations/python.html
- Cross-References: https://quarto.org/docs/authoring/cross-references.html
