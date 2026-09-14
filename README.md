# commatocolumn.com

Small, dependency-free browser tools. Each page is a single static HTML file with inline
CSS and JS, served by GitHub Pages. Nothing is uploaded anywhere — all work happens in the
browser.

## Tools

| Path                 | Tool             | What it does                                                                         |
| -------------------- | ---------------- | ------------------------------------------------------------------------------------ |
| `/`                  | Comma to Column  | Turns a column of pasted values into a SQL `IN (...)` list, quoting and escaping each. |
| `/table/`            | Table to Slides  | Turns a pasted table into a formatted table on the clipboard, ready to paste into Google Slides. |

Table to Slides accepts Claude Code box-drawing tables, Markdown, CSV and TSV. It infers
column alignment (right for numeric columns, or from a Markdown `:---:` separator row),
renders inline Markdown (bold, italic, code, links, strikethrough), and writes both
`text/html` and `text/plain` to the clipboard so the paste target can pick the richer one.

Claude Code prints a rule between every row, centres the header and left-aligns every body
cell. The parser drops those rules, and the numeric check tolerates what that output
contains: a real minus sign (U+2212, not an ASCII hyphen) and trailing significance markers
such as `***` or `ns`. So `−7.38% ***` counts as numeric and its column comes out
right-aligned on the slide, even though Claude Code rendered it left-aligned in the terminal.

## Local development

No build step. Open the HTML file directly, or serve the directory so the root-relative
links between pages resolve:

```
python3 -m http.server 8000
```

## Deployment

Pushing to `main` publishes via GitHub Pages. `CNAME` holds the custom domain.
