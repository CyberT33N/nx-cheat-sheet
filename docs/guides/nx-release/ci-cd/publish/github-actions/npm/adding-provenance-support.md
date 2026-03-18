

## Adding Provenance Support
- https://www.epicweb.dev/tutorials/versioning-and-releasing-npm-packages-with-nx/nx/adding-provenance-support
- https://docs.npmjs.com/generating-provenance-statements

Everything is now nicely set up and automated to publish from our GitHub repo to an npm registry. However, there's one more thing we can add: provenance support. Provenance support allows users to see where specific releases originated from.

For instance, let's take a look at how the Nx package itself is published on NPM. When you scroll down to the version, you'll see a checkmark next to it. By clicking on it, it displays information about the build and signing process on GitHub actions. This provides details about the commit the specific release originated from, the build file that triggered it, and some transparency log entries.

To set up provenance support for our design system package repository, we need to follow these steps:

Review the npm.js docs on publishing provenance.

Ensure that you're using the minimum required CLI version mentioned in the docs.

Make sure the package is configured with a public repository that matches the case-sensitive location where publishing provenance comes from.

Currently, our package.json file doesn't have a repository entry. To add one, include the following lines:

```json
"repository": {
  "type": "git",
  "url": "<your-repo-url>",
  "directory": "package/forms"
}
```

Replace <your-repo-url> with the URL of your GitHub repository. This should now properly set up provenance support for your package.

---

## Setting up Package Automation
In this final lesson, we'll be setting up automation for our packages using CI/CD.



### Verifying Repository Configuration
First, let's make sure our repository configuration is satisfied:

Check the packages button to ensure there are no duplicate entries.
Verify that the forms package has been added.
Ensure that the slate core and themes packages are properly configured.



### Setting up CI/CD with GitHub Actions
Next, we'll set up automation using GitHub Actions:

1. Obtain an ID token and add the necessary permissions to your publish workflow file.

```json
id_token: write
```

2. Make sure to pass the --provenance flag in your configuration.

```json
env:
  NPM_CONFIG_PROVENANCE: true
```

3. Commit and push your changes to the repository.

4. Check the Actions tab in GitHub to ensure that the workflow runs successfully.

5. Once the workflow has succeeded, verify that the new version (e.g., 1.9.0) has been committed.

6. Go to the Packages tab and confirm that the new version is reflected there.

7. Navigate to one of the packages and scroll down to see the checkmark, indicating a successful commit.

8. Click on More details to see the specific commit associated with the package update.

And that's it! You've successfully set up package automation using CI/CD.