---
sidebar_position: 2
sidebar_label: Quickstart
---

# Eternity Quickstart

## Commands:

### Build

Optional arguments:

- `-o <path>`: Specify an output to store the built package.
- `-d` OR ` --disk`: Build EPK on disk instead of in memory. This is useful for large EPKs.

Build the project using the specified configuration.

```sh
eternity build
```

### Convert

Convert an rpm into an epk.

```sh
eternity convert </path/to/rpm> </path/to/output/epk>
```

### Repo

Build/Generate repositories.

:::note
The difference between build and generate in the `eternity help build` output is unclear.

`build` creates a repo from projects in a directory, while `generate` creates the repo directly from EPK's in a folder.
:::

Options:

- `build`: Build a repository from a directory containing EPK project directories.
- `generate`: Generate a repository from a directory containing EPKs.

```sh
eternity repo <build/generate> <directory>
```

### Package

Unclear, help commands outputs nothing. This will be fixed later

:::danger
Do not use command, unknown behaviour
:::

```sh
eternity package <epk>
```
