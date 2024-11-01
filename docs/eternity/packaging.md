---
sidebar_position: 3
sidebar_label: Packaging
---

# Packaging with Eternity

Packages are built based on a configuration file and the `eternity build` command.

## Simple steps:

Before attempting any of this, please read this entire page if you haven't before.

:::note
Soon, a simple `eternity init` command will create the folders and a simple `eternity.json` for you, and even allow you to specify a git containing the source code.
:::

1. Create a folder for your package configuration, this will be a git later pushed to Oreon's packages.
2. Clone the projects code from a git into a folder named `resources`.
3. Build an `eternity.json` adhering to the eternity config structure [here](#the-eternityjson-structure).
4. Test it with the `eternity build` command.
5. Ensure the build was completed succesfully by checking for the built .epk and reading the logs.
6. For an extra safety precaution, you can attempt to install your newly built package with eon.
    1. Install eon if haven't
    2. Run `eon install /path/to/package.epk`
    3. Ensure the command runs as expected, and shows when you run `eon list`
7. Create a package repository in [Oreon Packages](https://git.oreonproject.org/packages).
8. Add the remote for that package and push your changes.

:::warn
Please do not directly push .epk files to the repos. This is can be solved simply by adding them to your `.gitignore`
:::

## The `eternity.json` structure

Currently, everything is inside of a `"metadata"` section in the JSON file. This is really uneccessary and will be removed soon.

### Options

Inside of this, you have:

- `"name"`: The name of the package.
- `"desc"`: A short description of the packages purpose/contents.
- `"longDesc"`: A lengthier version of the short description that should include more details.
- `"version"`: The packages current version you are building.
- `"author"`: The author of the package. This should match the applications creator when official, and be the actual author of the package if unofficial/community.
- `"license"`: The applications license, this should always match the license the code is available under.
- `"arch"`: Specifies the target architecture for your package. Common values include "x86_64" for 64-bit Intel and AMD systems, "arm64" for 64-bit ARM systems, and "aarch64" for ARM processors on devices like the Raspberry Pi.
- `"deps"`: An array of dependencies your package needs to be built and ran. Eon will attempt to install everything in this section before building and installing your package.
- `"specialFiles"`: Nested special configuration for the files in your build environment. The following are available:
    - `"noDelete"`: Array of files you don't want automatically deleted after build.
    - `"noReplace"`: Array of files you don't want replace during/after the build.
- `"build"`: Rules/steps for the actual build process.
    - `"type"`: The only supported type currently is `"host"` where the package is built inside of a `bwrap` (Bubble wrap) container.
    - `"deps"`: Build only dependencies, removed after build unless installed by the user previously.
    - `"steps"`: Commands to run in order to build the code into a binary/exectuable format. See steps section on this page for more details.
    - `"root"`: The name of the folder everything will be built in, commonly just called `"build"`.
    - `"files"`: The folder containing the actual source code, commonly `"src"` but should be changed to fit the project.
    - `"hooks"`: An important configuration for a folder containing something to actually install the package with eon. This isn't fully ready, but will run when users `eon install <package>`.

### Example

:::danger
The example package incorrectly installs during the build phase as of writting this. This warning will be removed once it's fixed.
:::

Rather than craming the json code into this page, a maintained and working package is available [here](https://git.oreonproject.org/fluffy/test-package) to see a basic configuration.

