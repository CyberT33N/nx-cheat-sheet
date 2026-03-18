# Troubleshooting

You might have noticed an error in the script, stating that there is no such file or directory as the build/package.json.

This is because the package.json file is being picked up as a potential project to publish. However, we don't want to publish or version the root level project. You can see that it's being set up as a version, which is not what we want.

There are different ways to handle this issue:

Define the project as private: Since this is the root level project, which we just need for our monorepo, we can define it as private. If we run npm run release again, the error should disappear.
```json
"private": true
```

Use nx.json to configure projects: Another way is to go into the nx.json file and define which projects should be included in the publishing, releasing, and versioning process. You can define a project array that specifies which projects to version.
```json
"projects": ["packages/*"]
```

You can also use glob patterns to exclude certain packages from the versioning process.

If you have certain files, like documentation or end-to-end packages, you might want to exclude them from the packaging process. This can help in reducing the size of your final package and make the process more efficient.