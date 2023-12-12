# Membrane Framework precompiled

This organization serves a purpose of hosting precompiled builds of packages and libraries required by [Membrane](https://github.com/membraneframework) plugins. The builds are created by installing packages with [homebrew](https://brew.sh/) on different CircleCI execution environments.

### Adding new precompiled builds

To add a new package repository using the automated method (homebrew on CircleCI) follow these steps:
* make sure it's is available in homebrew
* create a repository called `precompiled_<package>`, e.g. `precompiled_portaudio` from `precompiled_template` template
* in `.circleci/config.yml` replace `PACKAGE_NAME_HERE` with the package name (same as in repository name)

To trigger precompilation push a tag matching the latest version of your package, but prefixed with 'v'. To check this run `brew info <package>` or see `https://formulae.brew.sh/formula/<package>`. For example to trigger precompilation of a package with the latest version being 1.2.3 you would need to push a `v1.2.3` tag. After CircleCI pipeline finishes precompiling and publishing there should be a new release created from the pushed tag containing the precompiled builds of the package.
