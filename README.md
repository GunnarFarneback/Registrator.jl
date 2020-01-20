# Important

**This fork is now discontinued. Users should move to
[LocalRegistry](https://github.com/GunnarFarneback/LocalRegistry.jl)
instead.**

# Registrator

See https://github.com/JuliaComputing/Registrator.jl for the real Registrator.

~~This fork, adding minor fixes to
https://github.com/adamslc/Registrator.jl/tree/refactor, has the sole
purpose of enabling creation and manual updates of small private
registries until Registrator proper supports that.~~ See message above.

## Compatibility

This package requires Julia 1.1 or later.

## Installation

```
] add https://github.com/GunnarFarneback/Registrator.jl
```

## Create Registry

```
using Registrator
create_registry(<local path>, <repository url>, description = "My private registry")
```
This prepares a registry in the given directory, which must previously
not exist. Review the result and `git push` it manually.

## Add a Package

```
using Registrator
using MyPackage
register(MyPackage, <registry path>)
```

This assumes that you have a clean working copy of your registry at
`<registry path>` and adds `MyPackage` to the working copy. Review the
result and `git push` it manually. With the keyword argument
`commit = false`, the changes are made to the working copy but are not
committed.

Notes:
* The package must be stored as a git working copy, e.g. using
  `Pkg.develop`.
* The package must have a `Project.toml` file.
* There is no checking that the dependencies are available in any
  registry.

## Add a New Version of a Package

This is done in exactly the same way as adding a package. The only
requirement is that the `version` field of the package's
`Project.toml` is updated to a new version that is not already in the
registry.
