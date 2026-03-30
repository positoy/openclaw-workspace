# simple-hwp2pdf

Convert HWP / HWPX documents to PDF using the `simple-hwp2pdf` Python package.

## When to use

Use this skill when you need to:

- Convert `.hwp` or `.hwpx` files into `.pdf`
- Batch-convert official documents for research
- Build a small local wrapper/CLI around `simple-hwp2pdf`
- Prefer a practical, low-friction conversion path over manual Office exports

## When not to use

- If the source is already a PDF
- If you only need a quick text summary and the document has a published HTML/PDF version
- If the task is unrelated to HWP/HWPX conversion

## Assumptions

- Python 3.9+ is available
- `simple-hwp2pdf` can be installed in the active environment
- For `.hwp`, the `office` method may require Windows + Hancom Office
- For `.hwpx`, `standalone` or `auto` may be enough

## Recommended workflow

1. Identify file type: `.hwp` or `.hwpx`
2. Choose method:
   - `auto` for general use
   - `standalone` for `.hwpx` when you want no Office dependency
   - `office` for `.hwp` when exact layout matters and Hancom Office is available
3. Convert to PDF
4. Verify the output visually or by opening the PDF
5. If needed, extract text from the resulting PDF for downstream summarization

## Minimal Python usage

```python
from simple_hwp2pdf import convert

convert("input.hwp", "output.pdf", method="auto")
```

## Simple CLI wrapper

If you want a shell-friendly command, create a tiny wrapper:

```python
# hwp2pdf-cli.py
import sys
from simple_hwp2pdf import convert

src = sys.argv[1]
dst = sys.argv[2]
method = sys.argv[3] if len(sys.argv) > 3 else "auto"
convert(src, dst, method=method)
```

Run it:

```bash
python hwp2pdf-cli.py input.hwp output.pdf auto
```

## Notes

- `simple-hwp2pdf` is a Python library, so a custom CLI wrapper is often the cleanest way to use it in automation.
- For batch jobs, keep conversions append-only and save the source filename, output filename, method, and timestamp.
- Prefer `hwpx` sources when possible if you want the easiest cross-platform path.
- Known pitfall: some published versions may have dependency resolution issues on macOS / Python 3.9 environments.
- If `pip install simple-hwp2pdf` fails with conflicting dependencies, try:
  - checking whether a newer Python version is needed
  - creating a clean virtualenv
  - pinning a specific known-good version
  - or falling back to LibreOffice-based conversion for PDF output
