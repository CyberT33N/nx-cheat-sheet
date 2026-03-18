

# Release Tag
- The releaseTag property controls how git tags are parsed and generated. By default tags conform to semantic version and are validated as such.
- **Default is `v{version}`**

## Dependency Knowledge
- docs\features\releases\general.md
- docs\features\releases\groups\general.md
- docs\features\releases\version\general.md


### Guides
- https://www.epicweb.dev/tutorials/versioning-and-releasing-npm-packages-with-nx/nx/customizing-nx-release-tags-and-commit-messages







<br><br>

## nx.json

### releaseTagPattern
- docs\features\releases\tags\nx-json.md
- https://nx.dev/docs/reference/nx-json#release-tag




### Customizing Nx Release Tags
- **NOTE** Wenn man bisher mit der normalen Default-Versionierung gearbeitet hat und das dann beim ersten NX-Release ändert, das man ausführt, erhält man einen Fehler. `No git tags matching pattern "releases/v{version}"`

```json
{
	"release": {
		"version": {
			"conventionalCommits": true
		},
		"releaseTagPattern": "releases/v{version}"
	}
}

```


To fix this, check out that previous commit, and then change the tag to something that fits the pattern.
```shell
git checkout v1.2.0
git tag releases/v1.2.0
git checkout main
npx nx release
```

Now if you run npx nx release again, you'll see that it works with the new tag pattern and commit message.