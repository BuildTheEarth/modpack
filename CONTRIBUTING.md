# Contributing to the BuildTheEarth Modpack

Thanks for contributing to the BuildTheEarth modpack!

This guide explains how to set up a development environment, make changes, and submit a pull request.

## Requirements

### Required

* [Git] — version control
* [Pakku] — dependency management and modpack building
* Java 17 or newer — required by Pakku

### Recommended

* [PrismLauncher] — for running the development instance
* [Visual Studio Code] — for editing files and working with Git
* [GitHub Desktop] — optional graphical Git client
* [GitHub Pull Requests] — recommended VS Code extension for managing pull requests

## Setup

### 1. Create a PrismLauncher instance

1. Open [PrismLauncher] and select **Add Instance**.
2. Name the instance `BuildTheEarth`.
3. Select Minecraft `26.2`.
4. Select the latest compatible Fabric version.

> [!TIP]
> Example instance setup:
> ![Creating a new PrismLauncher instance](https://github.com/TerraFirmaGreg-Team/.github/blob/main/wiki/new_instances.png?raw=true)

### 2. Find the instance folder

Open the instance folder from PrismLauncher by right-clicking the instance and selecting **Folder**.

The Minecraft directory should be located inside the instance at:

```text
BuildTheEarth/minecraft
```

> [!TIP]
> ![PrismLauncher instance folder](https://github.com/TerraFirmaGreg-Team/.github/blob/main/wiki/prism_folder.png?raw=true)

### 3. Fork the repository

1. Open the [BuildTheEarth/modpack] repository on GitHub.
2. Select **Fork**.
3. Create the fork under your GitHub account.

You will make your changes in this fork and submit them back to the main repository with a pull request.

### 4. Clone your fork

Create a separate development folder outside your PrismLauncher instance.

This prevents Minecraft from modifying files that should remain under version control.

#### Visual Studio Code

1. Open VS Code and sign in to GitHub.
2. Press <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd>.
3. Select **Git: Clone**.
4. Choose **Clone from GitHub**.
5. Select your fork, for example `YourName/modpack`.
6. Choose your development folder.

#### GitHub Desktop

1. Open GitHub Desktop.
2. Select **File → Clone repository**.
3. Select your fork or enter:

```text
https://github.com/YourName/modpack.git
```

4. Choose your development folder and select **Clone**.

#### Terminal

```bash
git clone https://github.com/YourName/modpack.git
```

## Connect the development files to PrismLauncher

Keep your Git repository and PrismLauncher instance separate.

Copy the required project files into the PrismLauncher `minecraft` folder, then replace folders you intend to edit with symbolic links pointing back to your development repository.

On Windows, this can be done with `mklink`:

```text
mklink Link Target
```

> [!TIP]
> This setup allows you to edit files in the Git repository without Minecraft modifying unrelated tracked files.
>
> Developing directly inside the PrismLauncher instance is possible, but discouraged. If you do, consider using `.git/info/exclude` for local files that should not be committed.

## Install modpack dependencies

Open a terminal in the PrismLauncher instance folder and run:

```bash
pakku fetch
```

This downloads the files required by the modpack.

> [!WARNING]
> `pakku fetch` does not update the BuildTheEarth modpack itself.

## Branches

The repository uses the following branch structure:

### `main`

The stable, tested, and released version of the modpack.

Changes should normally reach `main` only after being tested in `dev`.

### `dev`

The main development branch.

New features, fixes, and other changes should normally be submitted here first.

### Feature and bugfix branches

Create a separate branch for each change, based on `dev`.

Examples:

```text
feature/add-custom-quest
bugfix/fix-launch-crash
```

You can create branches freely in your own fork.

## Making a contribution

Before starting, make sure your local `dev` branch is up to date.

If you have configured the main repository as the `upstream` remote:

```bash
git checkout dev
git pull upstream dev
```

Create a new branch:

```bash
git checkout -b feature/name-of-feature
```

Make and test your changes, then commit them:

```bash
git add .
git commit -m "Brief description of the change"
```

Push the branch to your fork:

```bash
git push origin feature/name-of-feature
```

You can perform the same operations through VS Code or GitHub Desktop if you prefer a graphical interface.

## Creating a Pull Request

After pushing your branch:

1. Open your fork on GitHub.
2. Create a new pull request.
3. Set the main repository's `dev` branch as the target.
4. Give the pull request a clear title.
5. Explain what you changed and why.
6. Link related issues when applicable.
7. Submit the pull request.

> [!TIP]
> If you use the [GitHub Pull Requests] VS Code extension, you can create and manage the pull request directly from VS Code.

If you are unsure about the correct target branch or PR format, check the project documentation or ask the team on [Discord].

## Review and merging

After submitting a pull request:

1. A member of the Minecraft team will review it.
2. Reviewers may leave comments or request changes.
3. Make requested changes on the same branch and push them normally. The pull request will update automatically.
4. At least one approval from the Minecraft team is required before merging.
5. An authorized maintainer will merge the pull request according to the project's merge rules.
6. Once merged, the branch can usually be deleted.

## Testing

Before submitting a pull request:

* Make sure the modpack works before applying your changes.
* Test your changes in PrismLauncher.
* Check PrismLauncher logs for errors.
* Verify that your changes do not break existing functionality.

## Git guidelines

* Use a separate branch for each feature or fix.
* Keep your fork synchronized with the main repository.
* Write clear, descriptive commit messages.
* Avoid including unrelated changes in the same pull request.

## Versioning

The project follows [Semantic Versioning](https://semver.org/):

* **Patch:** bug fixes and small changes (`1.0.0` → `1.0.1`)
* **Minor:** new backwards-compatible features (`1.0.0` → `1.1.0`)
* **Major:** breaking changes (`1.0.0` → `2.0.0`)

## Questions

If you need help:

* Check the repository's Issues and Discussions.
* Ask the team on [Discord].
* Review existing pull requests for examples of previous contributions.

## Video guide

A related setup guide is available here:

https://www.youtube.com/watch?v=vLL7jTtuOuw

> [!NOTE]
> Some steps in the video are specific to TerraFirmaGreg and are not required for this modpack.
