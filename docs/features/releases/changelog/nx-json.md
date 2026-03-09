# nx.json


## changelog


## Format
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





<br><br>

## Custom Changelog Renderer 
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