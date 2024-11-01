---
sidebar_position: 2
sidebar_label: Quickstart
---

# Eon Quickstart

Jump right into using the package manager with this short, simple guide.

## Commands:

### Help

To display help information:

```sh
eon help
```

### Install

To install a package:

```sh
eon install <package-name>
```

### List

Usage: eon list (repo/local)

:::warning
Choose either repo or local, you cannot list both at the same time.
:::

- repo: lists packages available in repositories.
- local: lists installed packages.

To list all available packages:

```sh
eon list (repo/local)
```

### Info

Usage: eon info \<package> (repo/local) \<repository>

**Package**: The package you want information about
**Repo/Local**: Whether to use the local or repostiory database
**Repository**: ??? (Do not use, unknown)

To get information about a specific package:

```sh
eon info <package> [(repo/local)] [<repository>]
```

### Remove

Simply uninstalls/removes a package.

To remove a package:

```sh
eon remove <package-name>
```

### Clean

Used to remove all the unused packages that were not manually installed or depended on by another package.

To clean remove unused dependencies:

```sh
eon clean
```

### Repo

Sub-commands:

- `add <packageUrl>:` adds a repository.
- `del <name>`: removes a repository.
- `list`: lists repositories.

To manage repositories:

```sh
eon repo (add/del/list) [...options]
```
