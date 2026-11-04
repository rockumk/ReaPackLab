# Publishing the ReaPackLab extension

This directory is for the ReaPackLab distribution package metadata.

## Release checklist

1. Build and test the **distribution** extension (not the centrally managed ReaPackLabDev binary).
2. Verify every released binary has the correct extension filename, architecture, behavior and embedded build identity.
3. Sign/notarize macOS releases when appropriate and test them on a clean REAPER installation.
4. Upload the binaries to a permanent **GitHub Release** in `rockumk/ReaPackLab`, using a tag matching the metadata version.
5. Add `Extensions/ReaPackLab.ext` with the metadata below, replacing `0.1.0` with the actual tested release version and including **only platforms with real assets**.
6. Allow the `reapack-index` workflow to generate `index.xml`, then inspect the generated `<source>` entries.
7. Install and update through ReaPack in a clean test REAPER instance before publicizing the index.

## Example metadata — **not an installable package**

Do not create an active `ReaPackLab.ext` package from this example until the binaries exist. The platform tags and the release-asset approach follow real packages in [ReaTeam/Extensions](https://github.com/ReaTeam/Extensions), such as `API/reaper_imgui.ext`.

```text
@description ReaPackLab: restricted REAPER package distribution
@author ReaLab
@version 0.1.0
@provides
  [darwin-arm64] reaper_reapacklab-arm64.dylib https://github.com/rockumk/ReaPackLab/releases/download/v$version/$path
  [darwin64] reaper_reapacklab-x86_64.dylib https://github.com/rockumk/ReaPackLab/releases/download/v$version/$path
  [win64] reaper_reapacklab-x64.dll https://github.com/rockumk/ReaPackLab/releases/download/v$version/$path
  [linux64] reaper_reapacklab-x86_64.so https://github.com/rockumk/ReaPackLab/releases/download/v$version/$path
@link
  Source repository https://github.com/rockumk/ReaPackLabDev
  Distribution repository https://github.com/rockumk/ReaPackLab
@about
  ReaPackLab is the restricted distribution edition of the ReaLab package manager.

  Unlike ReaPackLabDev, it has no Teacher Mode or editable central repository list.
```

**Important:** Filenames and URLs are proposed conventions, **not confirmed output names**. Adjust these to match the actual compiled, tested assets before release. For example, GitHub Actions development artifacts are not suitable permanent package URLs.

Only one `.ext` package should own each target plugin filename. Do not simultaneously install both ReaPackLab and ReaPackLabDev into the same REAPER resource directory.

This distribution extension's intended single hardcoded repository URL is an independent runtime choice. It should not be confused with this repository's own `index.xml`, which is the package feed used for distribution.
