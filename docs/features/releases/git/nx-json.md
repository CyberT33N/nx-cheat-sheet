# nx.json
- docs\reference\nx-json.md

## release
- docs\features\releases\nx-json.md

#### git
- The git property configures the automated git operations that take place as part of the release process.
  - https://nx.dev/docs/reference/nx-json#git

```json
{
  "release": {
    "git": {
      // This will enable committing any changes (e.g. package.json
      // updates, CHANGELOG.md files) to git
      "commit": true,
      // This will enable create a git for the overall release, or
      // one tag per project for independent project releases
      "tag": false,

	 "commitMessage": "chore: we just released v{version} 🎉"
    },
  },
}
```

##### commitMessage
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