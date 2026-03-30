---
name: kordoc-parse
description: Parse local HWP, HWPX, and PDF documents into Markdown using kordoc CLI or library. Use when converting Korean office documents, extracting text from local files, batching document conversion, or working with repository documents that should become Markdown or JSON.
---

# kordoc-parse

Use `kordoc` for local Korean document parsing.

## Workflow

1. Find the source file locally.
2. Prefer the installed `kordoc` CLI.
3. Parse the file to Markdown or JSON.
4. Save the result with the same base filename.
5. Use page/section ranges when the user wants partial extraction.
6. Keep outputs deterministic and file-based.

## CLI reference

- Convert one or more files:
  - `kordoc <files...>`
- Single-file output:
  - `kordoc file.pdf -o output.md`
- Multiple files to a directory:
  - `kordoc *.pdf -d ./converted/`
- Page/section range:
  - `kordoc file.pdf -p 1-3`
- JSON output:
  - `kordoc file.hwp --format json`
- Quiet mode:
  - `kordoc file.pdf --silent`
- Watch a directory:
  - `kordoc watch ./incoming`

## Use kordoc when

- Converting `.hwp`, `.hwpx`, or `.pdf` to Markdown
- Extracting metadata or page ranges from local documents
- Parsing government or public-sector Korean documents
- Batch converting a local folder of documents

## Notes

- Prefer the repository's own parser or CLI over ad-hoc text scraping.
- Keep original filenames for derived Markdown unless the user asks otherwise.
- If a document is image-heavy, use the repo’s OCR/fallback path when available.
