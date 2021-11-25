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
    needs: versioning
    if: needs.versioning.outputs.run_publish == 'true'

```