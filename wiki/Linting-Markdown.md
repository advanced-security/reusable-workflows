# Markdown - Linting

## Overview

Lint markdown files in your repository using [`markdownlint-cli`](https://github.com/igorshubovych/markdownlint-cli).

The workflow only runs when a pull request modifies `**.md` files.

## Usage

**Simple:**

```yaml
uses: advanced-security/reusable-workflows/.github/workflows/markdown-lint.yml@v0.2.0
secrets: inherit
```

## Default rules

The `MD013` (line-length) rule is disabled by default to avoid failures in repositories with long lines. All other [default markdownlint rules](https://github.com/DavidAnson/markdownlint/blob/main/doc/Rules.md) apply.

## Customising rules

To override or extend the default rules, add a `.markdownlint.json` (or `.markdownlint-cli2.jsonc`) file at the root of your repository. `markdownlint-cli` picks this up automatically.

Example `.markdownlint.json` to also disable the `MD033` (inline HTML) rule:

```json
{
  "MD013": false,
  "MD033": false
}
```
