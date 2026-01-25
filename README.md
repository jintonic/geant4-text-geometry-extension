This extension provides support for editing [Geant4 Text Geometry][tg] (.tg) files in [VS Code][], [Cursor][], and [Antigravity][].

## Features

- [Syntax Highlighting](#syntax-overview): Supports tags, parameters, units, math functions, and solid types.
- [Snippets](#available-snippets): Quick snippets for defining solids, logical volumes, placements, materials, colors, and more.
- **Auto-Formatting**: Automatically ensures a final newline and trims trailing whitespace on save.
- **Language Configuration**: Includes comment support and bracket matching.

## Installation

### VSIX Installation

1. Obtain the `.vsix` file from the GitHub [Releases][].
2. Install the `.vsix` file through your editor's "Install from VSIX" link.

## Usage

Simply open any file with the `.tg` extension to enable Geant4 Text Geometry support.

### Syntax Overview

- **Tags**: Start with `:` (e.g., `:solid`, `:volu`, `:mate`).
- **NIST Materials**: Supported with full highlighting and auto-completion for `G4_xxx` materials.
- **Parameters**: Defined with `:p` and referenced with `$`.
- **Units**: Specified with `*` (e.g., `*mm`, `*deg`, `*rad`).
- **Comments**: Start with `//`.
- **Include**: Nest files using `#include`.
- **Solids**: Common types like `BOX`, `TUBE`, `CONS`, `TRD`, `SPHERE`, `ELLIPSOID`, `HYPE`, `TET`, `TWISTEDBOX`, `ELLIPTICALTUBE`, etc.
- **Math**: Support for arithmetic expressions and functions like `sin`, `cos`, `log`.

### Available Snippets

The extension provides several snippets to speed up your geometry definition. Start typing the following prefixes (lowercase) to see suggestions:

- `world`: Expansion for a standard vacuum world setup with an example volume placed in the center
- `:solid`: Define a solid (includes box, tube, etc.)
- `:volu`: Define a logical volume with a already defined solid
- `:vin`: Define a logical volume with inline solid definition
- `:place`: Place a physical volume
- `:place_param`: Place a parameterized physical volume
- `:rotm`: Define a rotation matrix (3 axis angles, 6 polar/azimuthal, or 9 elements)
- `:rotm6`: Shortcut for 6-parameter polar/azimuthal rotation
- `:rotm9`: Shortcut for 9-parameter matrix elements
- `:isot`: Define an isotope
- `:elem`: Define a simple element
- `:elem_from_isot`: Define an element from isotopes
- `:mate`: Define a simple material
- `:mixt`: Define a mixture material
- `:p`: Define a parameter
- `:vis`: Set volume visibility
- `:colour` / `:color`: Set volume color and transparency. Common color names (e.g., `red`, `blue`, `coral`, `khaki`) expand to their normalized RGB values.
- `:div_width`: Divide a volume by width
- `:div_ndiv`: Divide a volume by number of divisions
- `:div_ndiv_width`: Divide a volume by number and width
- `:repl`: Define a replica
- `:volu_assembly`: Define an assembly volume
- `:place_assembly`: Place an assembly volume
- `:check_overlaps`: Enable overlap checking for a volume
- `:prop`: Define optical properties for a material ([GEARS][] extension)
- `:surf`: Define an optical boundary surface ([GEARS][] extension)
- [NIST Materials][]: Over 300+ predefined materials and compounds (e.g., `G4_Pb`, `G4_WATER`). Common names also work as snippet triggers (e.g., typing `water` expands to `G4_WATER`).

## For Developers

### Prerequisites

To build this extension, you need [Node.js][] installed, which includes [npm][] and [npx][].

- **macOS**: `brew install node` (using [Homebrew][]) or use the official installer.
- **Linux**: `sudo apt install nodejs npm` ([Debian][] / [Ubuntu][]) or use [NodeSource][].
- **Windows**: `winget install OpenJS.NodeJS` or download from [Node.js][].

*Tip*: Use [nvm][] (macOS/Linux) or [nvm-windows][] to manage Node versions easily.

### Project Files

#### Core Extension Files
- **[package.json](package.json)**: The manifest file that defines the extension's metadata, contributions (languages, grammars, snippets), and scripts.
- **[language-configuration.json](language-configuration.json)**: Configures language features like comment toggling, bracket matching, and auto-indentation.
- **[syntaxes/geant4-tg.tmLanguage.json](syntaxes/geant4-tg.tmLanguage.json)**: The TextMate grammar file that provides the logic for syntax highlighting.
- **[snippets/snippets.json](snippets/snippets.json)**: Contains all the geometry definition snippets available in the editor.

#### Documentation & Legal
- **[README.md](README.md)**: The main documentation file (this file), providing usage and developer instructions.
- **[LICENSE](LICENSE)**: The legal license for the project (MIT).

#### Development & CI/CD
- **[.vscode/launch.json](.vscode/launch.json)**: Setup for the "Extension Development Host" to test changes locally.
- **[.github/workflows/publish.yml](.github/workflows/publish.yml)**: GitHub Action workflow for automated publishing to Open VSX.
- **[.vscodeignore](.vscodeignore)**: Defines which files should be excluded from the final extension bundle.
- **[.gitignore](.gitignore)**: Lists files and directories that should not be tracked by Git.

### Building the Extension

To build the [VSIX][] package locally, first install dependencies:

```bash
npm install
```

Then run the package script:

```bash
npm run package
```

This will create a `.vsix` file in the root directory. You can inspect its contents or install it manually to test.

### Publishing the Extension

#### Automatic Publishing (Recommended)
This repository is configured with a GitHub Action that automatically publishes to the [Open VSX Registry][] whenever a new version tag is pushed.

1.  **Run the version command**: Instead of manual editing, use `npm version` to bump the version and create an **annotated tag** automatically. 

    | Command | Action | Example (1.0.1 →) | When to use |
    | :--- | :--- | :--- | :--- |
    | `npm version patch` | Increments 3rd digit | **1.0.2** | Bug fixes / minor tweaks |
    | `npm version minor` | Increments 2nd digit | **1.1.0** | New features (non-breaking) |
    | `npm version major` | Increments 1st digit | **2.0.0** | Breaking changes / major overhaul |

    ```bash
    # Example: bump patch and add a message
    npm version patch -m "Release version %s"
    ```
2.  **Push the changes and tags**:
    ```bash
    git push origin main --tags
    ```
*Note: Ensure your working directory is clean before running `npm version`. This command will update `package.json`, commit the change, and create an annotated tag for you.*

#### Manual Publishing
You can also publish manually from your terminal using the local version of `ovsx`:

```bash
# Using the local project scripts
npm run publish -- -p <YOUR_OVSX_TOKEN>

# Or using npx
npx ovsx publish -p <YOUR_OVSX_TOKEN>
```

### Managing `ovsx` Versions

This project pins a specific version of the `ovsx` publisher in `package.json` to ensure consistent builds.

*   **To try a different version (one-time):**
    ```bash
    npx ovsx@latest publish
    ```
*   **To permanently update the version:**
    ```bash
    npm install ovsx@latest --save-dev
    ```

[tg]: https://geant4-userdoc.web.cern.ch/UsersGuides/ForApplicationDeveloper/html/Detector/Geometry/geomASCII.html
[VS code]: https://code.visualstudio.com/
[Cursor]: https://cursor.com/
[Antigravity]: https://antigravity.google/
[Releases]: https://github.com/jintonic/geant4-text-geometry-extension/releases
[Node.js]: https://nodejs.org/
[npm]: https://www.npmjs.com/
[npx]: https://www.npmjs.com/package/npx
[Homebrew]: https://brew.sh/
[Debian]: https://www.debian.org/
[Ubuntu]: https://ubuntu.com/
[NodeSource]: https://github.com/nodesource/distributions
[nvm]: https://github.com/nvm-sh/nvm
[nvm-windows]: https://github.com/coreybutler/nvm-windows
[vsce]: https://github.com/microsoft/vscode-vsce
[VSIX]: https://code.visualstudio.com/api/working-with-extensions/publishing-extension#packaging-extensions
[NIST Materials]: https://geant4-userdoc.web.cern.ch/UsersGuides/ForApplicationDeveloper/html/Appendix/materialNames.html
[GEARS]: https://github.com/jintonic/gears/tree/master/tutorials/detector/optical
[Open VSX Registry]: https://open-vsx.org/
[ovsx]: https://www.npmjs.com/package/ovsx