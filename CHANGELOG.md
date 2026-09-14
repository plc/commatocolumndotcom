# Changelog

## 2026-09-14

- Added `/table-to-slides/`, a second tool that copies a pasted table to the clipboard as a
  formatted table for Google Slides.
- Restyled that tool from its standalone light-mode original into the dark slate UI used by
  the home page, and added a preview panel so the layout mirrors the input/output split of
  Comma to Column.
- Added a nav link between the two pages.

### Notes

- The site is intentionally build-free: one self-contained HTML file per tool, no shared
  assets. Style changes have to be applied to each page. That duplication is the deliberate
  trade for zero tooling.
- Rich-text copy needs `ClipboardItem`, which requires a secure context. On plain `http://`
  (other than localhost) the code falls back to selecting an off-screen `contenteditable`
  and calling `document.execCommand('copy')`.
- Pages link with root-relative paths (`/`, `/table-to-slides/`), so opening a file over
  `file://` breaks the nav. Use a local server.
