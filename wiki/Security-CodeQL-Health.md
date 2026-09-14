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
    permissions:
      actions: read
      contents: read
      security-events: read
    uses: advanced-security/reusable-workflows/.github/workflows/codeql-health.yml@main
```

The default failure states are `failing`, `stalled`, `stale`, `degraded`, `in-progress`, and `not-configured`. Override them with the `fail-on` input.
