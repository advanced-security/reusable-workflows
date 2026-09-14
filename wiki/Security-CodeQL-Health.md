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
      GHAS_AUDIT_TOKEN: ${{ secrets.GHAS_AUDIT_TOKEN }}
```

The default failure states are `failing`, `stalled`, `stale`, `degraded`, `in-progress`, and `not-configured`. Override them with the `fail-on` input.

Configure `GHAS_AUDIT_TOKEN` as an organization Actions secret and make it available to each caller repository. The token needs access to the repository being audited with these read permissions:

| Scope | Permission |
| --- | --- |
| Repository | Metadata |
| Repository | Pull requests |
| Repository | Actions |
| Repository | Code scanning alerts |
| Organization | Administration |

Organization Administration access lets the audit verify the attached code security configuration and detect failed rollouts.
