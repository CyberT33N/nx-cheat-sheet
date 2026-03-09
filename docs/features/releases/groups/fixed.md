
## Fixed
- https://nx.dev/docs/guides/nx-release/release-groups#fixed


When projectsRelationship is set to "fixed" (the default):
- All projects in the group share the same version number
- When one project requires a version bump, all projects in the group are versioned together
- Dependencies between projects in the group are always automatically updated
- Each project will receive a changelog entry, with a specific (configurable) message for those projects that were only bumped to align with the group version

```json
{
  "release": {
    "groups": {
      "shared-libraries": {
        "projects": ["ui-components", "utils", "data-access"],
        // this is also the default and can be omitted
        "projectsRelationship": "fixed",
        // ... other group configuration options ...
      },
    },
  },
}
```
