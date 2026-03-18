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