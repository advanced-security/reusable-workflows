# CodeQL Health

Audits the current repository's CodeQL configuration, execution, freshness, and language coverage. The job writes a Markdown table to the workflow run summary and fails when the repository is in an unhealthy state.

```yaml
name: CodeQL Health

on:
  pull_request:
  push:
    branches:
      - main

jobs:
  codeql-health:
    uses: advanced-security/reusable-workflows/.github/workflows/codeql-health.yml@main
    secrets:
      GHAS_AUDIT_APP_ID: ${{ secrets.MY_APP_ID }}
      GHAS_AUDIT_APP_KEY: ${{ secrets.MY_APP_KEY }}
```

The default failure states are `failing`, `stalled`, `stale`, `degraded`, `in-progress`, and `not-configured`. Override them with the `fail-on` input.

The workflow can also be selected directly by an organization ruleset. Ruleset runs use `pull_request` and `merge_group`; fork and Dependabot pull requests are intentionally skipped because GitHub does not expose Actions secrets to them.

Reusable callers map their own secret names to `GHAS_AUDIT_APP_ID` and `GHAS_AUDIT_APP_KEY`. Direct ruleset and manual runs use those names when present, then fall back to the Advanced Security organization defaults, `ADVANCED_SECURITY_APP_ID` and `ADVANCED_SECURITY_APP_KEY`. Make organization secrets available to each target repository.

The GitHub App needs these read permissions:

| Scope | Permission |
| --- | --- |
| Repository | Metadata |
| Repository | Pull requests |
| Repository | Actions |
| Repository | Code scanning alerts |
| Organization | Administration |

Organization Administration access lets the audit verify the attached code security configuration and detect failed rollouts.
