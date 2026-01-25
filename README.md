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

To build this extension, you need [Node.js][nodejs] installed, which includes [npm][npm] and [npx][npx].

- **macOS**: `brew install node` (using [Homebrew][homebrew]) or use the official installer.
- **Linux**: `sudo apt install nodejs npm` ([Debian][debian]/[Ubuntu][ubuntu]) or use [NodeSource][nodesource].
- **Windows**: `winget install OpenJS.NodeJS` or download from [nodejs.org][nodejs].

*Tip*: Use [nvm][nvm] (macOS/Linux) or [nvm-windows][nvm-windows] to manage Node versions easily.

### Building the Extension

To install the Visual Studio Code Extension Manager ([vsce][]) globally, run:

```bash
npm install -g @vscode/vsce
```

Once installed, you can build the [VSIX][] package using:

```bash
npx @vscode/vsce package
```

[tg]: https://geant4-userdoc.web.cern.ch/UsersGuides/ForApplicationDeveloper/html/Detector/Geometry/geomASCII.html
[VS code]: https://code.visualstudio.com/
[Cursor]: https://cursor.com/
[Antigravity]: https://antigravity.google/
[Releases]: https://github.com/jintonic/geant4-text-geometry-extension/releases
[nodejs]: https://nodejs.org/
[npm]: https://www.npmjs.com/
[npx]: https://www.npmjs.com/package/npx
[homebrew]: https://brew.sh/
[debian]: https://www.debian.org/
[ubuntu]: https://ubuntu.com/
[nodesource]: https://github.com/nodesource/distributions
[nvm]: https://github.com/nvm-sh/nvm
[nvm-windows]: https://github.com/coreybutler/nvm-windows
[vsce]: https://github.com/microsoft/vscode-vsce
[VSIX]: https://code.visualstudio.com/api/working-with-extensions/publishing-extension#packaging-extensions
[NIST Materials]: https://geant4-userdoc.web.cern.ch/UsersGuides/ForApplicationDeveloper/html/Appendix/materialNames.html
[GEARS]: https://github.com/jintonic/gears/tree/master/tutorials/detector/optical
