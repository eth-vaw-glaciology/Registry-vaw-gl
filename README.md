# VAW-GL's Julia package registry

This registry contains packages we develop for internal use, packages
of potentially general interest but not universal enough to be
registered officially as well as some packages which maybe registered
officially in the future.

This registry is tended to with https://github.com/GunnarFarneback/LocalRegistry.jl

## Usage notes

To use this repository it needs to be added (once per computer).  For ssh-access:
```julia
using Pkg
Pkg.Registry.add("git@github.com:eth-vaw-glaciology/Registry-vaw-gl.git")
```
or for html-access:
```
Pkg.Registry.add("https://github.com/eth-vaw-glaciology/Registry-vaw-gl.git")
```
When collaborating with external people, tell them to do the same.
I.e. they should add the registry before instantiating a project using
vaw-gl registered packages.

We do not currently tag releases for these packages, this means to use them they
need to be `dev`ed.  For example

```julia
Pkg.develop("GlacioTools")
```
do not just `add` them as they will be in a outdated state.  Maybe we
get more fancy with some packages in the future and tag releases.

### Instructions to get a Julia environment with vaw-gl deps running [TODO]

- clone the code

It contains a Manifest.toml
- start `julia --project`
- `] instantiate`
- `dev` the packages in vaw-gl registry


**TODO:** find out how this works on another computer & another user
with a private package registered in vaw-gl

## Adding a new package to the registry

Only packages developed by vaw-gl members or closely associated people
should be added to this registry.

Both private and public packages can be added to the registry.  Note
that adding private package will make their name public, but nothing
else.

To add a package:
```
using LocalRegistry, ThePackageIWantToAdd
register("ThePackageIWantToAdd"; registry = "vaw-gl")
```

( If you where to tag releases, then a new release could be added to
the registry with `register("ThePackageIWantToAdd")` )
