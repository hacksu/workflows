```yml
jobs:
  versioning:
    name: Versioning
    runs-on: ubuntu-latest
    steps:
      - uses: hacksu/workflows/packages/versioning@main
  publish:
    name: Publish
    runs-on: ubuntu-latest
    if: github.event_name == 'workflow_dispatch' || needs.versioning.outputs.run_publish == 'true'
    permissions:
      contents: read
      packages: write
    steps:
      - uses: hacksu/workflows/packages/publish@main

```