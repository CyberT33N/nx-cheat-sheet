# nx.json
- https://github.com/nrwl/nx/blob/master/packages/nx/src/config/nx-json.ts

## release
- docs\features\releases\nx-json.md

### groups

#### apps

##### docker
- https://nx.dev/docs/guides/nx-release/release-docker-images#install-nx-docker-plugin
```json
{
  "release": {
    "releaseTag": {
      "pattern": "release/{projectName}/{version}",
    },
    "groups": {
      "apps": {
        "projects": ["api"],
        "projectsRelationship": "independent",
        "docker": {
          // This should be true to skip versioning with other tools like NPM or Rust crates.
          "skipVersionActions": true,
          // You can also use a custom registry like `ghcr.io` for GitHub Container Registry.
          // `docker.io` is the default so you could leave this out for Docker Hub.
          "registryUrl": "docker.io",
          // The pre-version command is run before versioning, useful for verifying the Docker image.
          "groupPreVersionCommand": "echo BEFORE VERSIONING",
        },
        "changelog": {
          "projectChangelogs": true,
        },
      },
    },
  },
}
```





