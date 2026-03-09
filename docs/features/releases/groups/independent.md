## Independent
- https://nx.dev/docs/guides/nx-release/release-groups#independent

When projectsRelationship is set to "independent":
- Each project in the group maintains its own version
- Projects are versioned only when they have changes (apart from the influence of "updateDependents" configuration, learn more below)
- Changelog entries are generated only when there are direct or indirect ("updateDependents") changes to the project

```json
{
  "release": {
    "groups": {
      "microservices": {
        "projects": ["user-service", "order-service", "inventory-service"],
        "projectsRelationship": "independent",
        // ... other group configuration options ...
      },
    },
  },
}
```