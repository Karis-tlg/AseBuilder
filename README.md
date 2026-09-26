# AseBuilder

Private GitHub Actions builder for compiling Aseprite for personal use.

## Features

- Manual **Run workflow** button.
- Choose Aseprite source ref: `latest`, tag, branch, or commit SHA.
- Choose platform: **Windows**, **Linux**, **macOS**, or **all**.
- Choose `Release` or `RelWithDebInfo`.
- Build output is stored as a GitHub Actions artifact for 7 days.
- Automatic scheduled checking/building is currently disabled and left commented in the workflow.

## How to build

1. Open **Actions**.
2. Select **Build Aseprite**.
3. Click **Run workflow**.
4. Choose `aseprite_ref`, platform, and build type.
5. Download the artifact after the workflow succeeds.

## License note

Aseprite's EULA allows compiling/modifying the source for your own personal purpose or for proposing a contribution, and restricts distributing compiled copies to third parties.

Keep this repository private and do not republish its compiled artifacts.

Source: https://github.com/aseprite/aseprite
