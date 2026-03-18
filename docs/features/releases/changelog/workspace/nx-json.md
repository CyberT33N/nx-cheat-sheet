# nx.json

## releases

### changelog

#### workspaceChangelog
- https://nx.dev/docs/reference/nx-json#workspace-changelog


##### createRelease
```json
{
  "release": {
    "changelog": {
      "workspaceChangelog": {
        // This will create a GitHub release containing the workspace
        // changelog contents
        "createRelease": "github",
        // This will disable creating a workspace CHANGELOG.md file
        "file": false,
      },
    },
  },
}
```