# nx.json
- https://github.com/nrwl/nx/blob/master/packages/nx/src/config/nx-json.ts

## release
- docs\features\releases\nx-json.md

### groups

#### shared-libraries

##### projectsRelationship
- https://nx.dev/docs/guides/nx-release/release-groups#projects-relationship
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





