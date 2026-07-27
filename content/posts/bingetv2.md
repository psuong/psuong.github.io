---
title: "BinGet v2.x.x"
date: 2026-07-27T09:20:28-04:00
draft: false
summary: "Binget received a glowup!"
tags:
    - cli
    - c#
---

So last year, I wrote my own little package manager called binget. You can check the blog post [here](/posts/binget). A 
year later, binget received a major glow up since I wanted it to be more of a "proper" command line app with help messages 
and a more appealing UI.

As a result, I used libraries such as
* [ConsoleAppFramework](https://github.com/Cysharp/ConsoleAppFramework)
* [Spectre.Console](https://github.com/spectreconsole/spectre.console)

So, when you list the help, it looks like this during in the console.

```sh
binget -h

Usage: [command] [-h|--help] [--version]

Commands:
  clean, c                 Removes any local packages that are not listed in the config file. Your config file is effectively your primary list.
  install, update, i, u    Installs/updates packages from a configuration file.
  list, l                  Displays all packages in the destination directory and the config file.
```

And...running an install or update command produces the following output in your console.

```sh
➜ binget install --config .\config2.toml

  √ omnisharp-linux ----------------------------------------100%
√ omnisharp-windows ----------------------------------------100%
              √ lua ----------------------------------------100%
              √ nvy ----------------------------------------100%

Installed: 4, Failed: 0, Skipped: 0
┌───────────────────┬───────────────┐
│ Package           │ Status        │
├───────────────────┼───────────────┤
│ omnisharp-linux   │ √ - Installed │
│ omnisharp-windows │ √ - Installed │
│ lua               │ √ - Installed │
│ nvy               │ √ - Installed │
└───────────────────┴───────────────┘
```

# Summary of the new changes
## New Commands
- list - lists all installed packages and diffs them with your configuration toml file.
- clean - removes any installed packages that are not listed in your configuration toml file.
- install/update - can use either as they're aliases of each other.

## Downloading Woes
One of my biggest gripes with my v1 version was that, it was always fetching new packages whether or not there was an update. 
For example, OmniSharp Roslyn is on v1.39.15 as of today (07-26-2026). Let's say I make a tiny configuration locally in 
the downloaded package. If I ran `binget config.toml` (the old v1 version), it will download v1.39.15 again and overwrite 
everything locally.

This was _annoying_ as it meant I had to remove the entry from my configuration toml file just to avoid it from updating. The 
entire point of my configuration toml file was just to serve as a main list of packages to download and "install" locally. 

> I use the word "install" loosely as the packages are _not_ installed like a traditional installer. The packages are just 
downloaded and/or extracted.

Now, binget will write a `manifest.toml` to any extracted package locally. The `manifest.toml` file will list the following info:
* package - the name of the package (this is user defined in your configuration toml)
* repository - the unique identifier of the repository on Github
* tag - this is really the version number and will try to parse semantic versioning
* asset - the actual package downloaded
* checksum - the cryptographic hash of the downloaded asset
* installed - the date the package was downloaded and "installed"

The main field that binget cares about is the **tag** entry. If the fetched package is the _same_ version or an _older_ 
version, binget does not proceed with the download and skips that package. This now prevents unnecessary download and 
disk operations.

If the version is _newer_, then binget will proceed to indiscriminately overwrite your existing package with the new version. 
This will error out if an installed package is _currently_ in use.

## Some Security Measures
Okay, so how can I tell if the package you downloaded is the correct package? Github's API provides a field called `digest` in 
its json response. The `digest` field will typically include the hash type and it's hash value, however there are cases where 
the digest can be empty.

For now, assuming that the `digest` field is valid, I parse the hash type and and its hash value. The package is **already** 
downloaded, but **not* extracted yet. Based on the hash type, I hash the downloaded archive locally and compare it to the 
`digest`'s hash value. If they are not the same, the package "installation" effectively fails.

Additionally, I use [FileTypeChecker](https://github.com/AJMitev/FileTypeChecker), to ensure that whatever 
is downloaded is either an archive or an executable. 

You can set the security level in your configuration toml file to 
* 0 - none, effectively no checks will be performed
* 1 - laxed, checks will be performed if available (e.g. if the `digest` field is not empty, then a hash checksum will occur)
* 2 - strict, all checks will be performed. Any package that fails these basic checks will fail the "installation."

# Updates?
Updates will come as I have more needs to fill. Otherwise, feel free to fork this [repo](https://github.com/psuong/binget) 
and add some more updates! For now, I am very content with the current state of it as it fits my needs. I do want to axe 
Spectre.Console in favor of an imgui styled console UI from scratch (but that is a side project for another day).

> At the very least, a Linux release will drop very soon\u2122.