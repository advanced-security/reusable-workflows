<div align="center">
<h1>reusable-workflows</h1>

[![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)][github]
[![GitHub Issues](https://img.shields.io/github/issues/advanced-security/reusable-workflows?style=for-the-badge)][github-issues]
[![GitHub Stars](https://img.shields.io/github/stars/advanced-security/reusable-workflows?style=for-the-badge)][github]
[![License](https://img.shields.io/github/license/Ileriayo/markdown-badges?style=for-the-badge)][license]

</div>

## Overview

This repository contains a number of Reusable [GitHub Actions][github-actions] Workflows used by the [Advanced Security organisation][advanced-security-org].

## ✨ Features

[Checkout the Wiki for more information on each workflow.][github-wiki].

## Inputs

### `cooldown-days`

Available on all Python workflows (`python-build.yml`, `python-linting.yml`, `python-release.yml`, `python-testing.yml`, `python-vendor.yml`) as well as `container.yml` and `self-release.yml`.

| Input            | Type       | Default |
|------------------|------------|---------|
| `cooldown-days`  | `number`   | `3`     |

Number of days to use as the dependency cooldown window. Packages published more recently than this threshold are excluded from installs, ensuring only stabilised releases are used.

Internally the workflows pass `--exclude-newer "$(date -u -d "<cooldown-days> days ago" +%Y-%m-%dT%H:%M:%SZ)"` to their `uv`-managed installs. For hash-pinned installs the `--require-hashes` flag is also applied; callers should generate a hash-pinned `requirements.txt` using:

```bash
uv pip compile requirements.in --generate-hashes -o requirements.txt
```

## Maintainers / Contributors

- Advanced Security OSS Maintainers Team

## Support

Please create [GitHub Issues][github-issues] if there are bugs or feature requests.

## License

This project is licensed under the terms of the MIT open source license.
Please refer to [MIT][license] for the full terms.

<!-- Resources -->
[github]: https://github.com/advanced-security/reusable-workflows
[github-issues]: https://github.com/advanced-security/reusable-workflows/issues
[github-wiki]: https://github.com/advanced-security/reusable-workflows/wiki
[advanced-security-org]: https://github.com/advanced-security
[github-actions]: https://docs.github.com/en/enterprise-cloud@latest/actions
[license]: ./LICENSE
