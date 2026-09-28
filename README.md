# AseBuilder

A lightweight GitHub Actions workflow for building **Aseprite from source** on Windows, Linux, and macOS.

> This repository contains build automation only. It does **not** include or redistribute Aseprite binaries.

## Features

- Manual **Run workflow** button from GitHub Actions
- Build the latest Aseprite release with `latest`
- Build a specific **tag**, **branch**, or **commit SHA**
- Supported targets:
  - Windows x64
  - Linux x64
  - macOS
  - All platforms in one run
- Build modes:
  - `Release`
  - `RelWithDebInfo`
- Build artifacts are kept temporarily by GitHub Actions

## Usage

1. Fork or clone this repository.
2. Open the **Actions** tab.
3. Select **Build Aseprite**.
4. Click **Run workflow**.
5. Configure the build:
   - `aseprite_ref`: `latest`, a release tag, branch, or commit SHA
   - `platform`: `windows`, `linux`, `macos`, or `all`
   - `build_type`: `Release` or `RelWithDebInfo`
6. Wait for the build to finish.
7. Download the generated artifact from the workflow run.

### Recommended Windows build

For a normal Windows build, use:

```text
aseprite_ref: latest
platform: windows
build_type: Release
```

After downloading the artifact, extract the entire archive before launching `aseprite.exe`. Keep the `data` directory and other generated files beside the executable.

## Automatic builds

Scheduled checking/building is intentionally disabled for now.

The workflow still contains a commented example for enabling scheduled builds later. If enabled, it can be extended to check upstream releases and build only when a new Aseprite version appears.

## Windows portability

The Windows configuration explicitly uses:

```text
CURL_USE_SCHANNEL=ON
CURL_USE_OPENSSL=OFF
ENABLE_OPENSSL=OFF
ENABLE_CNG=ON
```

The workflow also checks the generated executable and fails the build if `aseprite.exe` still depends on `libcrypto-3-x64.dll`.

This helps ensure that downloaded Windows artifacts do not rely on OpenSSL DLLs that only happen to exist on the GitHub-hosted runner.

## Repository scope

AseBuilder is intended to be a reusable build workflow and reference implementation for compiling Aseprite from its public source repository.

It does not contain Aseprite source code. During a workflow run, the source is checked out directly from the official upstream repository.

Upstream project:

https://github.com/aseprite/aseprite

## License and distribution notice

Aseprite is developed and licensed by the Aseprite project and its contributors.

Before compiling or using Aseprite, review the official license/EULA in the upstream repository:

https://github.com/aseprite/aseprite/blob/main/EULA.txt

In particular, Aseprite's license places restrictions on redistribution of compiled copies. This repository is therefore provided as **build automation**, not as a binary distribution channel.

If you use this workflow, you are responsible for ensuring that your use of the generated artifacts complies with Aseprite's license.

## Disclaimer

This project is not affiliated with, endorsed by, or maintained by the Aseprite team.

Aseprite and related names are trademarks or project names belonging to their respective owners.
