# nx.json
- docs\reference\nx-json.md

## release
- docs\features\releases\nx-json.md

### version
- https://nx.dev/docs/reference/nx-json#version
- docs\features\releases\version\nx-json.md

#### generatorOptions
https://nx.dev/docs/reference/nx-json#version

```json
{
	"release": {
		"version": {
			"conventionalCommits": true,
			"generatorOptions": {
				"packageRoot": "build/{projectRoot}",
				"currentVersionResolver": "git-tag",
				"skipLockFileUpdate": true
			}
		}
	}
}

```