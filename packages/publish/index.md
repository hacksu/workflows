```yml
name: Publish

on:
  push:
      branches: [ main ]
  release:
    types: [created]
  workflow_dispatch:

jobs:

  publish:
    name: Publish
    runs-on: ubuntu-latest
    permissions:
      contents: read
      packages: write
    steps:
      - uses: hacksu/workflows/packages/publish@main
        with:
          NPM_TOKEN: ${{ secrets.NPM_TOKEN }}
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

```