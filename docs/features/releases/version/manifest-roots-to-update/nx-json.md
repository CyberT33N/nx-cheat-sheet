
# nx.json

## manifestRootsToUpdate
```json
{
  "release": {
    // Ensure that versioning works in both the source and dist directories
    "version": {
      // path structures for both the source and dist directories, where {projectRoot} and {projectName} are available placeholders that will be interpolated by Nx
      "manifestRootsToUpdate": [
        "{projectRoot}",
        // We use the object form of the manifestRootsToUpdate to specify that we want to update the dist package.json files and not preserve the local dependency references (if not using pnpm or bun)
        {
          "path": "dist/packages/{projectName}",
          "preserveLocalDependencyProtocols": false, // (NOT NEEDED WHEN USING pnpm or bun) because we need to ensure our dist package.json files are valid for publishing and the local dependency references such as "workspace:" and "file:" are removed
        },
      ],
    },
  },
  "targetDefaults": {
    // Ensure that publishing works from the dist directory
    // The nx-release-publish target is added implicitly behind the scenes by Nx Release, and we can therefore configure it in targetDefaults
    "nx-release-publish": {
      "options": {
        // the packageRoot property is specific the TS/JS nx-release-publish implementation, other ecosystem plugins may have different options
        "packageRoot": "dist/packages/{projectName}", // path structure for your dist directory, where {projectRoot} and {projectName} are available placeholders that will be interpolated by Nx
      },
    },
  },
}
```