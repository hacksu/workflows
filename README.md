## Workflows for GitHub Actions

This repository contains reused HacKSU GitHub Actions workflows.

### Example Usage

```yml
jobs:
    publish:
        runs-on: ubuntu-latest
        uses: hacksu/workflows/packages/publish
```