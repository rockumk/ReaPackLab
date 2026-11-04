# ReaPackLab

**ReaPackLab** is the release repository for the REAPER extension in the [ReaLab](https://github.com/rockumk) project. It is based on [ReaPack](https://reapack.com/), the package manager created by Christian Fillion.

The published v0.14.0 binary is a development-era **centrally managed** ReaPackLab build, with hosted configuration and Teacher Mode. [ReaPackLabDev](https://github.com/rockumk/ReaPackLabDev) is its source and development repository. The planned permanently restricted, single-repository bootstrap variant is a separate project, **ReaPackLabSetup**, and is not included here.

> **Initial release:** [v0.14.0](https://github.com/rockumk/ReaPackLab/releases/tag/v0.14.0) provides a macOS Apple Silicon (`darwin-arm64`) binary. It should be tested in an isolated REAPER installation before wider deployment; other platforms are not yet listed.

## Repository

This repository follows the standard `reapack-index` layout:

```text
ReaPackLab/
├── index.xml             # Generated ReaPack index
├── Extensions/           # Extension package metadata (.ext)
├── README.md             # Repository description
└── .github/workflows/    # Index checks and generation
```

**Repository index URL:**

```text
https://raw.githubusercontent.com/rockumk/ReaPackLab/master/index.xml
```

The index is generated automatically by [reapack-index](https://github.com/cfillion/reapack-index) after package metadata is added. Do not edit generated package entries in `index.xml` by hand. Currently, the index has a macOS Apple Silicon package for v0.14.0.

## Extension packaging

Native REAPER extensions are described by a metadata file such as `Extensions/ReaPackLab.ext`. The `@provides` entries tell ReaPack which binary to download for each operating system and architecture. Their target filenames are installed into REAPER's `UserPlugins` directory.

See [Extensions/README.md](Extensions/README.md) for the release metadata template and conventions based on [ReaTeam/Extensions](https://github.com/ReaTeam/Extensions), including `darwin-arm64`, `darwin64`, `win64`, and `linux64`.

A package version must never be published before all URLs in its active `@provides` entries point to verified release assets. GitHub Actions build artifacts are not the same as stable release assets.

## Relationship to ReaPackLabDev

| Project | Role |
| --- | --- |
| [ReaPackLab](https://github.com/rockumk/ReaPackLab) | Release repository for the managed extension |
| [ReaPackLabDev](https://github.com/rockumk/ReaPackLabDev) | Source and development of the managed extension |
| ReaLab | Umbrella name for the broader software project |

The two extension variants should be tested in separate REAPER resource directories to avoid competing over package files.

## License and acknowledgments

ReaPackLab is derived from ReaPack by Christian Fillion. ReaPack is licensed under the GNU Lesser General Public License, version 3 or later. Derived source and binaries must retain the applicable license and attribution notices. Packaging tools and repository-format documentation are provided by the [ReaPack](https://github.com/cfillion/reapack-index) ecosystem.

ReaPackLab is an independent project and is not affiliated with Cockos, Inc.
