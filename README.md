# ReaPackLab

**ReaPackLab** is the distribution repository for the REAPER extension in the [ReaLab](https://github.com/rockumk) project. It is based on [ReaPack](https://reapack.com/), the package manager created by Christian Fillion.

The distribution edition is designed for managed REAPER installations. Its intended policy is **permanently restricted operation**, with one approved repository compiled into the extension and **no Teacher Mode**. This is distinct from [ReaPackLabDev](https://github.com/rockumk/ReaPackLabDev), which contains the full development and centrally managed classroom edition.

> **Development status:** Packaging is being prepared. No ReaPackLab distribution binary is published or supported yet. The presence of an index does not mean an extension is available for installation.

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

The index is generated automatically by [reapack-index](https://github.com/cfillion/reapack-index) after package metadata is added. Do not edit generated package entries in `index.xml` by hand. Until a verified release is available, the index may contain no installable packages.

## Extension packaging

Native REAPER extensions are described by a metadata file such as `Extensions/ReaPackLab.ext`. The `@provides` entries tell ReaPack which binary to download for each operating system and architecture. Their target filenames are installed into REAPER's `UserPlugins` directory.

See [Extensions/README.md](Extensions/README.md) for the release metadata template and conventions based on [ReaTeam/Extensions](https://github.com/ReaTeam/Extensions), including `darwin-arm64`, `darwin64`, `win64`, and `linux64`.

A package version must never be published before all URLs in its active `@provides` entries point to verified release assets. GitHub Actions build artifacts are not the same as stable release assets.

## Relationship to ReaPackLabDev

| Project | Role |
| --- | --- |
| [ReaPackLab](https://github.com/rockumk/ReaPackLab) | Public distribution repository and restricted distribution extension |
| [ReaPackLabDev](https://github.com/rockumk/ReaPackLabDev) | Development, central management, Teacher Mode and multi-repository synchronization |
| ReaLab | Umbrella name for the broader software project |

The two extension variants should be tested in separate REAPER resource directories to avoid competing over package files.

## License and acknowledgments

ReaPackLab is derived from ReaPack by Christian Fillion. ReaPack is licensed under the GNU Lesser General Public License, version 3 or later. Derived source and binaries must retain the applicable license and attribution notices. Packaging tools and repository-format documentation are provided by the [ReaPack](https://github.com/cfillion/reapack-index) ecosystem.

ReaPackLab is an independent project and is not affiliated with Cockos, Inc.
