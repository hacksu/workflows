```yml
name: Publish

on:
  push:
      branches: [ main ]
  release:
    types: [created]
  workflow_dispatch:

jobs:

  versioning:
    name: Versioning
    runs-on: ubuntu-latest
    steps:
      - uses: hacksu/workflows/packages/versioning@main

  publish:
    name: Publish
    runs-on: ubuntu-latest
    needs: versioning
    if: github.event_name == 'workflow_dispatch' || needs.versioning.outputs.run_publish != 'false'
    permissions:
      contents: read
      packages: write
    steps:
      - uses: hacksu/workflows/packages/publish@main
        with:
          NPM_TOKEN: ${{ secrets.NPM_TOKEN }}
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

```