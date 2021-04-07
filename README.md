# qgis-plugins.xml

```yaml
name: Publisz plugin

on:
  push:
    tags:
      - '*'
  release:
    types: [published]
  workflow_dispatch:
jobs:
  zip-files:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: thedoctor0/zip-release@master
        with:
          filename: PluginName.zip

      - name: Upload Release
        uses: svenstaro/upload-release-action@v2
        with:
          file: PluginName.zip
          repo_token: ${{ secrets.GITHUB_TOKEN }}
          tag: ${{ github.ref }}
          overwrite: true
```
