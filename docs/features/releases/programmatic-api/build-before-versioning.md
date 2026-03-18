## Build Before Versioning
- Normalerweise kann man das Pre-Version-Command-Property nehmen, um seine Dependencies vorher zu bauen.

Wenn man aber diese programmatische API hier benutzt, ist es schon zu spät.
  - docs\features\releases\version\pre-version-command\general.md

This way, when the version starts, it will run the build before applying the version, and then run the publishing and everything else.

However, in our case, using the `preVersionCommand` is too late. Our release script copies everything from the `packages` folder over to a custom `build` folder and then runs a version on top of that. Unfortunately, the build specified in the `preVersionCommand` still happens on the package, which means we're missing out on that.

So basically in our case, we need to run it beforehand.

Now we could either run the actual `npx nx run-many -t build` inside the package, or we could also just go to the `package.json` and combine it in there.

```bash
{
	"scripts": {
		"release": "npx nx run-many --target=build && tsx tools/release.ts"
	}
}
```
