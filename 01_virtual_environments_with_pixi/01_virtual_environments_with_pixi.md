## Setup

### Installation

#### Visual Studio Code (VSCode)

[Download Link](https://code.visualstudio.com/download)

#### Pixi

Pixi is available for all major operating systems and provides a consistent way to define, reproduce, and run development environments. It can be installed quickly and works seamlessly with the `conda-forge` ecosystem.

1. [Installation instructions](https://pixi.sh/latest/#installation)
   1. If you have a windows machine
   ```bash
   winget install prefix-dev.pixi
   ```
2. Testing installation
   ```bash
   pixi --version
   ```


In this unit, we will learn how to use **Pixi** to manage packages and environments. Pixi is a modern package manager built on top of Conda ecosystem principles, but with improved performance, reproducibility, and cross-platform support. It uses a `pixi.toml` file to define environments and supports tasks for automation. This unit includes instructions for installing Pixi and covers core Pixi commands for creating, managing, and sharing environments.

## Creating and Managing Environments

With Pixi, environments are defined via a `pixi.toml` file. This ensures that your environment is reproducible and version-controlled. Pixi uses workspaces (directories with a `pixi.toml`) and automatically activates environments when you enter them.

| Code           | Description                                       |
| ----------------- | ------------------------------------------------- |
| `pixi init`       | Initialize a new Pixi project with a `pixi.toml`  |
| `pixi add python` | Add Python to your environment                    |
| `pixi run`        | Run commands inside the environment               |
| `pixi shell`      | Start a shell with the Pixi environment activated |
| `pixi info`       | Show details about the environment                |
| `pixi list`       | List all packages in the environment              |

**Exercises**


1. Use `pixi init` to initialize a new project.

2. Open the `pixi.toml` file and inspect its contents.

3. Use `pixi add` to add `python` to the environment.
4. Use `pixi add` to add `pip` to the environment
5. Start a `pixi shell`
6. Verify python is available by typing `python --version`
7. Verify pip is available by typing `pip --help`

## Installing Python Packages with Pixi

In this section, you'll learn how to install Python packages into a Pixi-managed environment. Pixi supports two main ways of adding packages:

* **Conda-style installation** (via `conda-forge`): By default.
* **PyPI-style installation** (via `pip`): Useful for packages not available on `conda-forge`.

You can combine both methods in the same environment. This gives you access to a wide range of scientific and general-purpose Python tools.

| Code                      | Description                                                 |
| ---------------------------- | ----------------------------------------------------------- |
| `pixi add numpy`             | Install `numpy` from `conda-forge`                          |
| `pixi add matplotlib pandas` | Install multiple packages from `conda-forge`                |
| `pixi add --pypi package_name`  | Install package from PyPI                               |
| `pixi add pip`               | Add `pip` support to the environment                        |
| `pixi shell`                 | Enter the environment to run or install additional packages |
| `pip install seaborn`        | Use `pip` inside Pixi shell for PyPI-only packages          |
| `pixi remove <package>`      | Remove a package from the environment                       |
| `pixi list`                  | View all currently installed packages                       |

**Exercises**

1. Use `pixi add` to add `numpy` and `matplotlib`.

2. Run `pixi info` to verify they are installed.
3. Install `streamlit` from `--pypi`.
4. Verify `streamlit` is installed.
5. Install `pandas` with `--pypi` and verify it is installed.
6. Use `pixi remove` to remove `pandas` and verify that it is gone.

## Exporting, Sharing, and Reproducing Environments

Unlike Conda, Pixi manages environments via `pixi.toml` and `pixi.lock` files. These files define your environment in a reproducible format. Sharing these files with collaborators ensures they can recreate the exact same environment on any platform.

| File           | Purpose                                                          |
| -------------- | ---------------------------------------------------------------- |
| `pixi.toml`    | Human-editable file that specifies dependencies                  |
| `pixi.lock`    | Auto-generated file that pins exact versions for reproducibility |
| `pixi install` | Sync the environment to the lock file                            |

**Exercises**

1. Copy only `pixi.toml` and `pixi.lock` to the new location.

2. `pixi install` the environment in your new folder 
3. Confirm that `numpy` is available and version matches the lock file.