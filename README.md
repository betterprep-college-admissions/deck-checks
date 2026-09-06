# deck-checks

Reusable GitHub Actions workflow that checks Pandoc fenced-div balance in
BetterPrep slide-deck repos.

## Why this repo is public

GitHub does not let a workflow in one organization call a private reusable
workflow that lives in another organization. The Mini Ivy content repos call
the copy in `mini-ivy/pandoc_template`, which is private and scoped to the
`mini-ivy` org. BetterPrep repos live in `betterprep-college-admissions`, so
they need a copy they are allowed to reach. This repo holds nothing but the
validator, so it is safe to publish.

## Keep the two copies identical

`.github/workflows/check-markdown-reusable.yml` here must stay byte-for-byte
identical to
`mini-ivy/pandoc_template/.github/workflows/check-markdown-reusable.yml`.
When one changes, copy it to the other and commit both.

## How a content repo calls it

`.github/workflows/check-markdown.yml` in each BetterPrep deck repo:

```yaml
jobs:
  validate:
    uses: betterprep-college-admissions/deck-checks/.github/workflows/check-markdown-reusable.yml@main
```
