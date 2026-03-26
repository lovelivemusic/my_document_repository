# Edge Cases

This document tests boundary conditions and unusual Markdown constructs that may challenge PDF converters.

---

## Empty Sections

### This Section Is Intentionally Empty

### So Is This One

---

## Very Long Heading That Exceeds What Would Normally Fit on a Single Line in a PDF Document and Should Wrap Gracefully

Content after a very long heading.

---

## Single-Character Content

a

---

## Very Long Unbroken String

`aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa`

And a long URL: https://example.com/very/long/path/that/goes/on/and/on/and/should/eventually/wrap/or/truncate/gracefully/in/the/pdf/output/document

---

## Deeply Nested Lists

- Level 1
  - Level 2
    - Level 3
      - Level 4
        - Level 5
          - Level 6
            - Level 7
              - Level 8

1. Level 1
   1. Level 2
      1. Level 3
         1. Level 4
            1. Level 5

---

## Large Table

| Row | A | B | C | D | E | F | G | H | I | J |
|-----|---|---|---|---|---|---|---|---|---|---|
| 1   | a | b | c | d | e | f | g | h | i | j |
| 2   | k | l | m | n | o | p | q | r | s | t |
| 3   | u | v | w | x | y | z | 1 | 2 | 3 | 4 |
| 4   | 5 | 6 | 7 | 8 | 9 | 0 | a | b | c | d |
| 5   | e | f | g | h | i | j | k | l | m | n |
| 6   | o | p | q | r | s | t | u | v | w | x |
| 7   | y | z | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
| 8   | 9 | 0 | a | b | c | d | e | f | g | h |
| 9   | i | j | k | l | m | n | o | p | q | r |
| 10  | s | t | u | v | w | x | y | z | ! | @ |

---

## Table with Empty Cells

| Name    | Email              | Phone          | Notes |
|---------|--------------------|----------------|-------|
| Alice   | alice@example.com  | +1-555-0101    |       |
| Bob     |                    | +1-555-0102    | No email on file |
|         | charlie@example.com|                | Name unknown |
| Diana   | diana@example.com  |                |       |

---

## Adjacent Code Blocks

```python
# First code block
x = 1
```
```javascript
// Second code block — immediately after the first
const y = 2;
```
```bash
# Third code block — no gap
echo "z = 3"
```

---

## Code Block Inside a List

1. First, create the config file:

   ```json
   {
     "input": "./docs",
     "output": "./output.pdf"
   }
   ```

2. Then run the conversion:

   ```bash
   gitmd2pdf --config config.json
   ```

3. Check the output in `./output.pdf`

---

## Mixed Inline Formatting

This sentence has **bold**, *italic*, `code`, ~~strikethrough~~, [a link](https://example.com), and ***bold italic*** all in one line.

What about **bold with `code` inside**? Or *italic with `code` inside*? Or ~~strikethrough with **bold** inside~~?

---

## Consecutive Blockquotes

> First blockquote — standalone.

> Second blockquote — should be separate from the first.

> Third blockquote — also separate.

---

## Blockquote Followed by Code

> Here is a quote about configuration.

```json
{ "this": "is code right after a blockquote" }
```

---

## Unicode and Special Characters

| Character Type   | Examples                                    |
|------------------|---------------------------------------------|
| Accented         | cafe, naive, resume, cliche                 |
| Currency         | $ EUR GBP JPY                               |
| Arrows           | up, down, left, right, bidirectional        |
| Math             | plus-minus, not-equal, less-or-equal, greater-or-equal, approximately |
| Dashes           | en-dash (--), em-dash (---), minus          |
| Quotes           | single quotes, double quotes, guillemets    |

---

## Paragraph Stress Test

Short paragraph.

A medium-length paragraph that contains enough text to demonstrate normal line wrapping behaviour in the PDF output. It should flow naturally across multiple lines.

A much longer paragraph designed to test how the PDF renderer handles substantial blocks of continuous text. This paragraph intentionally goes on for quite a while to simulate real-world documentation that contains detailed explanations, technical descriptions, and other verbose content that a user might include in a Markdown document that is being converted to PDF format. The text should wrap cleanly, maintain consistent line spacing, and not overflow the page margins under any circumstances. If this paragraph causes any rendering issues, it likely indicates a problem with the PDF engine's text layout algorithm or margin calculation logic that should be investigated and resolved before the tool is considered production-ready.

---

## Line Breaks

This line has two trailing spaces
to force a line break (soft break).

This line uses a backslash\
for a line break instead.

---

## Escaped Pipe in Table

| Expression       | Result |
|------------------|--------|
| `a \| b`         | a or b |
| `x \|\| y`       | x or y |

---

*End of edge cases document.*
