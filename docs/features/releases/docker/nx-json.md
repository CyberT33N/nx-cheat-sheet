# nx.json
- https://github.com/nrwl/nx/blob/master/packages/nx/src/config/nx-json.ts

## release
- docs\features\releases\nx-json.md

### docker
- https://nx.dev/docs/reference/nx-json#docker

```json
{
  "release": {
    "docker": {
      // Run this command before versioning Docker images
      "preVersionCommand": "npx nx run-many -t docker:build",

      // Define versioning schemes for different environments
      "versionSchemes": {
        "production": "{currentDate|YYMM.DD}.{shortCommitSha}",
        "hotfix": "{currentDate|YYMM.DD}.{shortCommitSha}-hotfix",
        "staging": "{currentDate|YYMM.DD}-staging",
        "development": "{currentDate|YYMM.DD}-dev-{shortCommitSha}",
      },

      // Skip Docker versioning for these projects to prevent versioning with other tools like NPM
      // Only set this if you are not using {versionActionsVersion} in your docker version scheme
      "skipVersionActions": ["api"],

      // Default Docker repository name (can be overridden per project)
      "repositoryName": "myorg",

      // Docker registry URL
      "registryUrl": "docker.io",
    },
  },
}
```





