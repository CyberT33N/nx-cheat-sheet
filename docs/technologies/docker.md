# Plugins

## Docker

### Docs
- https://nx.dev/docs/reference/nx-json#docker-plugin-options
- https://nx.dev/docs/technologies/build-tools/docker/introduction


```json
{
  "plugins": [
    {
      "plugin": "@nx/docker/plugin",
      "options": {
        "buildTarget": {
          "name": "docker:build",
          // Skip the default --tag argument
          "skipDefaultTag": true,
          // You must provide your own tags via args
          "args": ["--tag myorg/myapp:latest", "--tag myorg/myapp:1.0.0"],
        },
      },
    },
  ],
}
```