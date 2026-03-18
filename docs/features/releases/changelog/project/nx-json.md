# nx.json

## releases

### changelog

#### projectChangelogs
- https://nx.dev/docs/reference/nx-json#project-changelogs
- boolean | object

```json
{
  "release": {
    "changelog": {
      // This enables project changelogs with the default options
      "projectChangelogs": true,
    },
  },
}
```

```json
{
  "release": {
    "changelog": {
      "projectChangelogs": {
        // This will create one GitHub release per project containing
        // the project changelog contents
        "createRelease": "github",
        // This will disable creating any project level CHANGELOG.md
        // files
        "file": false,
      },
    },
  },
}
```


#### Format
- https://nx.dev/docs/guides/nx-release/configure-changelog-format
```json
{
  "release": {
    "changelog": {
      "projectChangelogs": {
        "renderOptions": {
          "authors": true,
          "applyUsernameToAuthors": true,
          "commitReferences": true,
          "versionTitleDate": true
        }
      }
    }
  }
}
```



##### render (Custom Changelog Renderer )
- https://nx.dev/docs/guides/nx-release/configure-changelog-format#custom-changelog-renderer

```json
{
  "release": {
    "changelog": {
      "projectChangelogs": {
        "renderer": "./tools/custom-changelog-renderer.ts",
      },
    },
  },
}
```