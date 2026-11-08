# ReaPackLab

**ReaPackLab** is the release repository for the centrally managed REAPER package manager in the ReaLab project, based on ReaPack by Christian Fillion.

**Current stable release: [v0.14.2](https://github.com/rockumk/ReaPackLab/releases/tag/v0.14.2)** — macOS 15.0 or later, Apple Silicon (ARM64). The binary embeds version **0.14.2** and is Developer ID Application signed, securely timestamped, and built with hardened runtime. Other platforms are not listed in this distribution.

The separate [ReaPackLabSetup](https://github.com/rockumk/ReaPackLabSetup) bootstrap companion has its own version and feed. It is not included in the main binary.

## Security and verification

**Signed, not notarized.** Signing does not establish Apple notarization or Gatekeeper acceptance; macOS warnings may still occur. Do not assume that this release validates all deployment or recovery workflows. Test in an isolated REAPER resource directory before classroom or wider deployment.

Each new release includes the dylib, `ReaPackLab-SHA256SUMS.txt`, and `ReaPackLab-provenance.json`, recording the final signed-byte hash and build identity. Existing releases remain unchanged. The binaries in older release tags retain their original signatures and embedded versions.

## Repository / installation

ReaPack repository index URL:

```text
https://raw.githubusercontent.com/rockumk/ReaPackLab/master/index.xml
```

Native extension metadata is maintained in `Extensions/ReaPackLab.ext`. Its active `@provides` entry selects the verified, versioned ARM64 release asset and installs it into REAPER's `UserPlugins` directory. Restart REAPER after installing or updating native extensions.

The index is generated automatically with [reapack-index](https://github.com/cfillion/reapack-index) after verified assets and package metadata are published. Generated package entries are not edited by hand; historical versions are retained. See [Extensions/README.md](Extensions/README.md) for packaging conventions. Documented platform examples are not a claim that those platforms have release assets.

## Development and scope

[ReaPackLabDev](https://github.com/rockumk/ReaPackLabDev) is the development repository (access restricted). This distribution repository and its automatic source archives contain packaging metadata, not the development source tree. Public provenance records identify the exact development commit and Actions build without publishing private source or logs.

ReaPackLab is the managed package manager; ReaPackLabSetup is a separate bootstrap companion. Test installation and upgrades in isolated REAPER resources before using them with an existing managed installation.

## License and acknowledgments

ReaPackLab is derived from ReaPack by Christian Fillion. ReaPack is licensed under the GNU Lesser General Public License, version 3 or later. Derived source and binaries must retain the applicable license and attribution notices. Packaging tools and repository-format documentation are provided by the [ReaPack](https://github.com/cfillion/reapack-index) ecosystem.

ReaPackLab is an independent project and is not affiliated with Cockos, Inc.
