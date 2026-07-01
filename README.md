# Created using the Lean 4 Project Template:

[![License: Apache 2.0](https://img.shields.io/badge/License-Apache_2.0-lightblue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Zulip : Topic](https://img.shields.io/badge/Zulip-Topic-%237E57C2.svg?logo=zulip&logoColor=white)](https://leanprover.zulipchat.com/#narrow/channel/113488-general/topic/Tutorial.3A.20Getting.20Started.20with.20Blueprint-Driven.20Projects)
[![YouTube : Tutorial](https://img.shields.io/badge/YouTube-Tutorial-%23FF0000.svg?logo=youtube&logoColor=white)](https://youtu.be/KyuyTsLgkMY)


## Install Lean 4

Ensure that you have a functioning Lean 4 installation. If you do not, please follow
the [Lean installation guide](https://leanprover-community.github.io/get_started.html).

## Clone this Repository

To clone this repository to your local machine, please refer to the relevant section of the
GitHub documentation [here](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository).


## Configure GitHub Pages

To set up GitHub Pages for your repository, follow these steps:

1. Go to the **Settings** tab of your repository.
2. In the left sidebar, click on the **Pages** section.
3. In the **Source** dropdown, select `GitHub Actions`.

The workflow [`deploy-pages.yml`](.github/workflows/deploy-pages.yml) builds the Jekyll site in
[`website`](website), runs the
[`upstreaming-dashboard-action`](https://github.com/leanprover-community/upstreaming-dashboard-action),
and deploys the result to GitHub Pages.

## Repository Layout

The template repository is organized as follows (listing the main folders and files):

- [`.github`](.github) contains GitHub-specific configuration files and workflows.
    - [`workflows`](.github/workflows) contains GitHub Actions workflow files.
        - [`build-project.yml`](.github/workflows/build-project.yml) defines the workflow for building
        the Lean project on pushes, pull requests, and manual triggers. This is a minimalistic build
        workflow which is not necessary if you decide to generate a blueprint (see instructions below)
        and can be manually disabled by clicking on the **Actions** tab, selecting **Build Project**
        in the left sidebar, then clicking the horizontal triple dots (⋯) on the right,
        and choosing **Disable workflow**.
        - [`deploy-pages.yml`](.github/workflows/deploy-pages.yml) defines the workflow for building
        and deploying the GitHub Pages site, including generation of the upstreaming dashboard.
        - [`create-release.yml`](.github/workflows/create-release.yml): defines the workflow for creating a new Git tag and GitHub release when the `lean-toolchain` file is updated in the `main` branch. Ensure the following settings are configured under **Settings > Actions > General > Workflow permissions**: "Read and write permissions" and "Allow GitHub Actions to create and approve pull requests".
        - [`update.yml`](.github/workflows/update.yml) is the dependency
        update workflow to be triggered manually by default. [It's not documented yet, but it will be soon.]
    - [`dependabot.yml`](.github/dependabot.yml) is the configuration file to automate CI dependency updates.
- [`.vscode`](.vscode) contains Visual Studio Code configuration files
    - [`extensions.json`](.vscode/extensions.json) recommends VS Code extensions for the project.
    - [`settings.json`](.vscode/settings.json) defines the project-specific settings for VS Code.
- [`Project`](Project) should contain the Lean code files.
    - [`Mathlib`](Project/Mathlib) should contain `.lean` files with declarations missing from the
    current version of Mathlib.
    - [`Example.lean`](Project/Example.lean) is a sample Lean file.
- [`scripts`](scripts) contains scripts to update Mathlib ensuring that the latest version is
fetched and integrated into the development environment.
- [`website`](website) contains the Jekyll files for the GitHub Pages homepage that displays the
upstreaming dashboard.
- [`.gitignore`](.gitignore) specifies files and folders to be ignored by Git.
and environment.
- [`CODE_OF_CONDUCT.md`](CODE_OF_CONDUCT.md) should contain the code of conduct for the project.
- [`CONTRIBUTING.md`](CONTRIBUTING.md) should provide the guidelines for contributing to the
project.
- [`lakefile.toml`](lakefile.toml) is the configuration file for the Lake build system used in
Lean projects.
- [`lean-toolchain`](lean-toolchain) specifies the Lean version and toolchain used for the project.


