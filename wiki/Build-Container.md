# Container - Build / Publish

## Overview

This workflow will build and publish a container image to the GitHub Container Registry.
This workflow does the following:

- Setup Docker / Buildx
- Configure GitHub Container Registry and tagging image
- Build and push the container image
- Generate a SBOM (Software Bill of Materials) for the container image and upload them to GitHub

## Usage

**Simple:**

```yaml
uses: advanced-security/reusable-workflows/.github/workflows/container.yml@v0.2.0
secrets: inherit
with:
  # This is used for tagging the container image.
  # It will automatically also set `latest` / `main` + major version `v1` tags.
  version: v1.0.0
```

**With Settings:**

```yaml
uses: advanced-security/reusable-workflows/.github/workflows/container.yml@v0.2.0
secrets: inherit
with:
  # This is used for tagging the container image
  version: v1.0.0
  # Select the Dockerfile to use
  container-file: Dockerfile     # Defaults to `Dockerfile`
```
