# Guides

## NX Release

### CI-CD

#### Docker
- https://nx.dev/docs/guides/nx-release/release-docker-images
- https://www.youtube.com/watch?v=TOPxKJXUaqw

#### Plugins
- docs\technologies\docker.md
- https://nx.dev/docs/technologies/build-tools/docker/introduction



##### Install Nx Docker plugin
```shell
nx add @nx/docker
```

Example:
```docker
// apps/api/Dockerfile
FROM docker.io/node:lts-alpine

ENV HOST=0.0.0.0
ENV PORT=3000

WORKDIR /app

RUN addgroup --system api && \
adduser --system -G api api

COPY dist app/
COPY package.json app/
RUN chown -R api:api .

# You can remove this install step if you build with `--bundle` option.
# The bundled output will include external dependencies.
RUN npm --prefix api --omit=dev -f install

CMD [ "node", "app" ]
```





## Create docker image
```shell
nx build api
nx docker:build api
```




## Set up a new release group

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









## Related
- docs\features\releases\general.md