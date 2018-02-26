# Update/Upgrade

As new releases of libraries become available, it becomes inevitable to use the newest version of these libraries in our project. Using the latest versions may provide us with distinct advantages, from whole new features to security patches to better abstraction and easier way of doing things.

However they are not with their downsides. Changing library and dependency versions may break the existing code and in some extreme cases make our existing code base unusable.

Therefore it is imperative to know and understand which dependency versions to upgrade.

### How do I do it?

#### yarn upgrade

To update a package or dependency, we can use this command.

```
yarn upgrade [package | package@tag | package@version | @scope/]... [--ignore-engines] [--pattern]
```

This command updates dependencies to their latest version based on the version range specified in the `package.json` file. The `yarn.lock` file will be recreated as well.

### Gotchas

When no package names are specified with `yarn upgrade`, all dependencies are upgraded. This may lead to inconsistent behavior, undesired side effects  or may break something in the existing system. 

It is recommended that while upgrading any dependency, the package name is specified.

### Migration from React 15 to React 16
TBA
