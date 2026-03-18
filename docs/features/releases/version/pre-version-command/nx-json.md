# nx.json
- docs\reference\nx-json.md

## release
- docs\features\releases\nx-json.md

### version
- https://nx.dev/docs/reference/nx-json#version
- docs\features\releases\version\nx-json.md

#### preVersionCommand
- In order to ensure that projects are built before the new version is applied to their package manifest, you can use the preVersionCommand property in nx.json:
- https://nx.dev/docs/guides/nx-release/build-before-versioning#_top
```json
{
  "release": {
    "version": {
      "preVersionCommand": "npx nx run-many -t build"
    }
  }
}
```