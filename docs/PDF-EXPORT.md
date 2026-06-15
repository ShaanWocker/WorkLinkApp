# PDF Export for Technical Build Plan

This repository includes the source document at:

- `docs/technical-build-plan.md`

## Option 1: Export locally in VS Code

Install the **Markdown PDF** extension, then open the markdown file and run:

- `Markdown PDF: Export (pdf)`

This will generate:

- `docs/technical-build-plan.pdf`

## Option 2: Export with Pandoc

Run from the repository root:

```bash
pandoc docs/technical-build-plan.md -o docs/technical-build-plan.pdf
```

## Option 3: GitHub Actions auto-generation

A workflow file has been added at:

- `.github/workflows/generate-plan-pdf.yml`

It generates `docs/technical-build-plan.pdf` on every push that changes the markdown file, then commits the PDF back to the repository.

## Notes

- The workflow requires write permission to commit the generated PDF.
- If your repository has branch protection rules, the workflow may need to run on a PR branch instead of pushing directly to the default branch.
- If you want a more polished PDF later, consider adding a custom Pandoc template, cover page, page numbers, and branding.
