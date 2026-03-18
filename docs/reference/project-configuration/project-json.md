# project.json

## Docs
- https://nx.dev/docs/reference/project-configuration#when-to-use-packagejson-vs-projectjson


### When to Use package.json vs project.json
Both package.json and project.json can be used to configure Nx targets, and both support the same configuration options including executors:

package.json: Use the "nx" property to define targets with executors, options, and other Nx-specific configuration
project.json: A dedicated Nx configuration file that keeps your package.json focused on package metadata
The choice between package.json and project.json is primarily a matter of preference. The package.json is standard for JavaScript projects, so you may prefer to use that over the Nx-specific project.json file.

The following configuration creates build and test targets for Nx.


project.json
```json
{
  "root": "libs/mylib/",
  "sourceRoot": "libs/mylib/src",
  "projectType": "library",
  "tags": ["scope:myteam"],
  "implicitDependencies": ["anotherlib"],
  "namedInputs": {
    "default": ["{projectRoot}/**/*"],
    "production": ["!{projectRoot}/**/*.spec.tsx"]
  },
  "targets": {
    "test": {
      "inputs": ["default", "^production"],
      "outputs": [],
      "dependsOn": ["build"],
      "executor": "@nx/jest:jest",
      "options": {}
    },
    "build": {
      "inputs": ["production", "^production"],
      "outputs": ["{workspaceRoot}/dist/libs/mylib"],
      "dependsOn": ["^build"],
      "executor": "@nx/js:tsc",
      "options": {}
    }
  }
}
```



package.json
```json
{
  "name": "mylib",
  "scripts": {
    "test": "jest",
    "build": "tsc -p tsconfig.lib.json", // the actual command here is arbitrary
    "ignored": "exit 1",
  },
  "nx": {
    "namedInputs": {
      "default": ["{projectRoot}/**/*"],
      "production": ["!{projectRoot}/**/*.spec.tsx"],
    },
    "targets": {
      "build": {
        "inputs": ["production", "^production"],
        "outputs": ["{workspaceRoot}/dist/libs/mylib"],
        "dependsOn": ["^build"],
      },
      "test": {
        "inputs": ["default", "^production"],
        "outputs": [],
        "dependsOn": ["build"],
      },
    },
    "includedScripts": ["test", "build"], // If you want to limit the scripts Nx sees, you can specify a list here.
  },
}
```