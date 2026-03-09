# nx.json
- docs\reference\nx-json.md

## release
- docs\features\releases\nx-json.md

#### conventionalCommits
- https://nx.dev/docs/guides/nx-release/customize-conventional-commit-types
```json
{
  "release": {
    "conventionalCommits": {
      "types": {
        // disable the docs type for versioning and in the changelog
        "docs": false,
        ...
      }
    }
  }
}
```


#### types

##### changelog
- https://nx.dev/docs/guides/nx-release/customize-conventional-commit-types#renaming-the-changelog-section-for-a-commit-type

```json
{
  "release": {
    "conventionalCommits": {
      "types": {
        ...
        "docs": {
          ...
          "changelog": {
            "title": "Documentation Changes"
          }
        },
        ...
      }
    }
  }
}
```