# nx.json
- docs\reference\nx-json.md

## release
- docs\features\releases\nx-json.md

#### releaseTagPattern
- https://nx.dev/docs/reference/nx-json#release-tag


NX > 22
```json
{
  "release": {
    "releaseTag": {
      "pattern": "release/{version}"
    },
    "git": {
      "commitMessage": "chore(release): {version}"
    }
  }
}
```


