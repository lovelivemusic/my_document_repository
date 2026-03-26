# Formatting Showcase

This document demonstrates the full range of **Git-flavoured Markdown** formatting supported by GITMD2PDF. Use it as a visual reference when reviewing PDF output quality.

---

## Text Styles

Here is **bold text**, *italic text*, ***bold and italic***, and ~~strikethrough text~~. You can also use `inline code` within a sentence.

For emphasis within a word: un**frigging**believable, or a*]partially*italic word.

---

## Blockquotes

> Simple blockquote — a single level of indentation.

> **Multi-paragraph blockquote:**
>
> First paragraph inside the quote. This tests whether paragraph breaks within blockquotes are preserved in the PDF.
>
> Second paragraph. Still inside the same blockquote block.

> Nested blockquotes:
>> Level two — indented further.
>>> Level three — the deepest nesting most renderers support.

> Blockquote with other elements:
>
> - A list item inside a blockquote
> - Another item
>
> ```python
> # Code inside a blockquote
> print("Hello from a blockquote!")
> ```

---

## Lists — Every Variation

### Unordered (Bullets)

- Apple
- Banana
  - Cavendish
  - Plantain
    - Cooking plantain
    - Dessert plantain
- Cherry

### Ordered (Numbered)

1. Preheat the oven to 180C
2. Mix dry ingredients
3. Add wet ingredients
   1. Eggs (2 large)
   2. Milk (200ml)
   3. Butter (50g, melted)
4. Bake for 25 minutes

### Task Lists

- [x] Write the formatting showcase
- [x] Include every markdown element
- [ ] Review PDF output
- [ ] Get stakeholder sign-off
  - [x] Design team
  - [ ] Engineering team
  - [ ] Product team

### Definition-style (using bold + indent)

**Markdown**
: A lightweight markup language for creating formatted text using a plain-text editor.

**PDF**
: Portable Document Format — a file format for presenting documents independent of software, hardware, or operating systems.

---

## Tables

### Basic Table

| Feature       | Supported | Notes                     |
|---------------|:---------:|---------------------------|
| Bold          |    Yes    | `**text**`                |
| Italic        |    Yes    | `*text*`                  |
| Strikethrough |    Yes    | `~~text~~`                |
| Subscript     |    No     | Not standard Markdown     |
| Superscript   |    No     | Not standard Markdown     |

### Alignment Demo

| Left         |   Centre   |        Right | Default     |
|:-------------|:----------:|-------------:|-------------|
| Left-aligned | Centred    |  Right-aligned | No alignment |
| Text         |   Text     |         Text | Text        |
| 123          |    456     |          789 | 012         |

### Table with Long Content

| Parameter               | Type     | Required | Description                                                                 |
|-------------------------|----------|----------|-----------------------------------------------------------------------------|
| `input_file`            | `string` | Yes      | Path to the input Markdown file or directory containing `.md` files         |
| `output_file`           | `string` | Yes      | Path where the generated PDF will be saved                                  |
| `theme`                 | `string` | No       | Name of the CSS theme to apply (default: `github`)                          |
| `table_of_contents`     | `bool`   | No       | Whether to generate a table of contents from headings (default: `true`)     |
| `page_numbers`          | `bool`   | No       | Whether to include page numbers in the footer (default: `true`)             |
| `syntax_highlighting`   | `string` | No       | Syntax highlighting theme for code blocks (default: `monokai`)              |

---

## Code Blocks

### With Syntax Highlighting

```python
import json
from pathlib import Path

def load_config(path: str) -> dict:
    """Load and validate a JSON configuration file."""
    config_path = Path(path)
    if not config_path.exists():
        raise FileNotFoundError(f"Config not found: {path}")

    with open(config_path) as f:
        config = json.load(f)

    required_keys = {"input", "output", "theme"}
    missing = required_keys - config.keys()
    if missing:
        raise ValueError(f"Missing required keys: {missing}")

    return config
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GITMD2PDF Demo</title>
    <style>
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
            line-height: 1.6;
            max-width: 800px;
            margin: 0 auto;
            padding: 2rem;
        }
        code { background: #f4f4f4; padding: 0.2em 0.4em; border-radius: 3px; }
    </style>
</head>
<body>
    <h1>Hello, World!</h1>
    <p>This is a <code>HTML</code> code block example.</p>
</body>
</html>
```

```sql
-- Top 10 most active users in the last 30 days
SELECT
    u.username,
    u.email,
    COUNT(a.id) AS activity_count,
    MAX(a.created_at) AS last_active
FROM users u
JOIN activities a ON a.user_id = u.id
WHERE a.created_at >= NOW() - INTERVAL '30 days'
GROUP BY u.id, u.username, u.email
ORDER BY activity_count DESC
LIMIT 10;
```

```go
package main

import (
    "fmt"
    "net/http"
    "log"
)

func handler(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintf(w, "Hello from GITMD2PDF API, %s!", r.URL.Path[1:])
}

func main() {
    http.HandleFunc("/", handler)
    log.Println("Server starting on :8080")
    log.Fatal(http.ListenAndServe(":8080", nil))
}
```

### Inline Code References

Use `git clone` to copy a repo. The config lives in `~/.gitmd2pdf/config.json`. Run `npm run build` to compile.

---

## Links

- [External link](https://example.com)
- [Link with title](https://example.com "Example Website")
- [Relative link to another file](../Projects/Project%201.md)
- [Anchor link to Tables section](#tables)
- Bare URL: https://example.com/auto-detected
- [Reference-style link][ref1]

[ref1]: https://example.com/reference "Reference Style Link"

---

## Images

### Local Image (Relative Path)

![GITMD2PDF conversion pipeline](../images/diagram-pipeline.svg)

*Figure 1: Conversion pipeline — SVG loaded from a relative path*

### Local PNG Image

![Sample banner image](../images/sample-blue.png)

*Figure 2: A solid-colour PNG banner from the images directory*

### Image with Title

![Logo placeholder](../images/logo-placeholder.png "Placeholder for a company logo")

For a comprehensive set of image tests, see [Image Examples](Image%20Examples.md).

---

## Horizontal Rules

Three different syntaxes that all produce horizontal rules:

---

***

___

---

## Footnotes

Markdown supports footnotes[^1] for adding supplementary information. They can contain multiple paragraphs[^2] and even code.

[^1]: This is a simple footnote. It appears at the bottom of the document.

[^2]: This is a longer footnote with multiple lines.

    It can span paragraphs if indented properly.

    ```
    Even code blocks work inside footnotes.
    ```

---

## HTML Fallback

Some Markdown renderers support inline HTML. This tests whether GITMD2PDF handles it:

<details>
<summary>Click to expand (collapsible section)</summary>

This content is inside a `<details>` tag. In a PDF, it should either render expanded or be clearly indicated.

- Item inside collapsible
- Another item

</details>

<dl>
  <dt>Term One</dt>
  <dd>Definition for term one — using HTML definition list.</dd>
  <dt>Term Two</dt>
  <dd>Definition for term two.</dd>
</dl>

---

## Special Characters & Escaping

These characters have special meaning in Markdown and should render literally when escaped:

\* asterisk \\ backslash \` backtick \_ underscore \{ \} braces \[ \] brackets \( \) parentheses \# hash \+ plus \- minus \. dot \! exclamation

Ampersands & angle brackets < > should render correctly in normal text.

The pipe character | appears in tables but should render normally in paragraphs.

---

*This document is part of the GITMD2PDF test repository.*
