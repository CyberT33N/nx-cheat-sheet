# Releases
- Also, wenn ich das richtig verstanden habe, kann man NX Release auch ohne Monorepo als eigenständiges Feature benutzen?

## Docs
- docs\guides\nx-release
- https://nx.dev/docs/features/manage-releases
- https://nx.dev/docs/guides/nx-release/release-npm-packages
- https://nx.dev/docs/guides/nx-release/release-docker-images
- https://nx.dev/docs/guides/nx-release/automate-github-releases
- https://nx.dev/docs/guides/nx-release/automate-gitlab-releases

## Commands
- docs\features\releases\commands.md

## Typescript
- docs\features\releases\typescript.md

## Changelog
- docs\features\releases\changelog.md

## Programmatic API
- docs\features\releases\programmatic-api\general.md
















# Workflows








<br><br>



## Dry Run
- Bevor ich das Release wirklich erstelle, egal ob lokal oder beim Publishen, sollte ich vorher immer einen Dry Run machen, um die Änderungen zu sehen.
  - docs\features\releases\commands.md#dry-run
```shell
nx release --dry-run
```










<br><br>



## First release
- Wenn man `nx-release` zum ersten Mal ausführt, hat man noch keinen Git-Tag. Daher sollte man bitte das Argument `first-release` verwenden; dann wird auch ein Git-Tag erstellt.

```shell
npx nx release --first-release
```
- Will create CHANGELOG.md
- Creates git tag











<br><br>










### Default release example
- **Notice nx use as default `fixed` project**


#### Dependency Knowledge
- docs\features\releases\version\conventional-commits.md
- docs\features\releases\version\version-plans.md
- docs\features\releases\groups\general.md


1. Run release
```shell
npx nx release
```

2. Dependens on which architecture you work for versioning

Mit conventional-commits:
- Basierend auf der Conventional-Chomits-Anleitung kommt, wenn wir es aktivieren, kein interaktiver Prozess. Das heißt, über die Git-Commits bzw. die Commit-Convention wurde festgelegt, wo sich etwas geändert hat und wie die Inkrementierung erfolgt.


Ohne conventional-commits:
- Danach kommt ein interaktives Terminal, in dem man auswählen kann, was man inkrementieren möchte. Hier kann man zum Beispiel „major“ wählen. Das wäre die erste Version, also ein „breaking change“.
 -  Hier kann man sehen, was sich alles ändert. Das ist sehr gut, wenn man sehen will, wie es wirklich aussehen würde, wenn man das Release erstellt.











