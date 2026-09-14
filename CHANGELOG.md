# Changelog

## 2026-09-14

- Added `/table-to-slides/`, a second tool that copies a pasted table to the clipboard as a
  formatted table for Google Slides.
- Restyled that tool from its standalone light-mode original into the dark slate UI used by
  the home page, and added a preview panel so the layout mirrors the input/output split of
  Comma to Column.
- Added a nav link between the two pages.
- Synced the Jost typeface onto the new page after it landed on the home page. The tables
  copied to the clipboard stay on Arial deliberately — Google Slides needs a font it has
  locally, so the preview panel shows Arial too.

- Matched both the placeholder and the Sample button to real Claude Code output: a rule
  between every row, a centred header and left-aligned body cells. Earlier versions showed
  only a header rule, and right-aligned the numeric column, which Claude Code does not do.
- Fixed numeric-column detection for that output. A leading U+2212 minus and trailing
  significance markers (`***`, `ns`) meant cells like `−7.38% ***` failed the numeric test
  and rendered left-aligned on the slide.
- Aligned the page furniture with the home page: buttons read Sample / Convert / Copy, the
  output panel names its artifact ("Google Slides Table", mirroring "SQL IN Statement"), and
  the internal `preview()` became `convert()` to match.

### Notes

- The site is intentionally build-free: one self-contained HTML file per tool, no shared
  assets. Style changes have to be applied to each page. That duplication is the deliberate
  trade for zero tooling.
- Rich-text copy needs `ClipboardItem`, which requires a secure context. On plain `http://`
  (other than localhost) the code falls back to selecting an off-screen `contenteditable`
  and calling `document.execCommand('copy')`.
- Pages link with root-relative paths (`/`, `/table-to-slides/`), so opening a file over
  `file://` breaks the nav. Use a local server.
- The clipboard table is deliberately Arial, not the site's Jost. Jost is a webfont Google
  Slides has no access to, so a table pasted in Jost would fall back to something arbitrary
  on the slide. The preview panel shows Arial for the same reason: it should show what
  lands on the slide, not what matches the page.
- The box-drawing art in the placeholder and Sample is width-sensitive. Regenerate it rather
  than hand-editing — every line must be the same length or the borders visibly stagger.
