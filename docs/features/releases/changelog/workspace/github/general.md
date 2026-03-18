# Changelog (CHANGELOG.md)

## Workspace

## Guides
- https://www.epicweb.dev/tutorials/versioning-and-releasing-npm-packages-with-nx/nx/github-releases-for-package-changelogs

### Docs
- https://nx.dev/docs/guides/nx-release/automate-github-releases

When it comes to releasing packages, you might be familiar with pushing them to a registry like npm. However, there's also the concept of releasing them on GitHub. This usually involves a combination of changelogs.

For example if we go navigate to the Releases tab on the nx repository. You can see a list of releases and their details, including changelogs, authors who contributed to the release, and the source code as a downloadable zip file.

In our current setup, we are using a workspace-level changelog, and GitHub releases are not enabled. To enable them, we can make some adjustments in the nx.json file.
```json
{
	"changelog": {
		"workspaceChangelog": {
			"createRelease": "github"
		}
	}
}
```

This will push the changelog and the source code to your GitHub repository, enabling GitHub releases for your project.

Now usually what you want to do in that case is potentially also to disable the changelog generation in terms of a local file. And so we can disable this to have to be false, which means the local changelog would not be generated in addition to the GitHub release.

```json
{
	"changelog": {
		"workspaceChangelog": {
			"createRelease": "github",
			"file": false
		}
	}
}
```

Now, let's say you have an existing repo and you're experimenting with various options. You can commit the changes as they are for now.

In this example, a new feature "buttons" has been added in the Git history, so it's time to release a new version. To do this, spin up a local development and run the release script. Run npx nx local-registry in one terminal, and in a new one run npm run release

The new release is pushed to the local registry, and the source code is updated on GitHub. There, you'll find the new release, along with information about who published it and the generated changelog.

When you create a release, it's essential to recognize the efforts of the contributors who helped you throughout the development process. Linking contributors in releases not only gives them well-deserved recognition but also sends them a notification, making them aware of the release.

In this way, you can show your gratitude to the contributors and motivate them to continue their valuable contributions to the project.

## Related
- docs\features\releases\general.md