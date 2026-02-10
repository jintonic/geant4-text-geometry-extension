This extension provides support for editing [Geant4 Text Geometry][tg] (.tg) files in [VS Code][], [Cursor][], and [Antigravity][].

## Features

- [Syntax Highlighting](#syntax-overview): Supports tags, parameters, units, math functions, and solid types.
- [Snippets](#available-snippets): Quick snippets for defining solids, logical volumes, placements, materials, colors, and more.
- **Auto-Formatting**: Automatically ensures a final newline and trims trailing whitespace on save.
- **Language Configuration**: Includes comment support and bracket matching.

## Installation

### Open VSX (Antigravity, VSCodium, Cursor, etc.)

Search for **"Geant4 Text Geometry"** in your editor's extension marketplace and click **Install**. This extension is hosted on the [Open VSX Registry][ovsx_page].

### VS Code (Standard)

Standard VS Code uses the Microsoft Marketplace and does not search Open VSX by default. **VS Code users should use the [VSIX Installation](#vsix-installation) method below.**

### VSIX Installation

1. Obtain the `.vsix` file from the territory GitHub [Releases][].
2. Install the `.vsix` file through your editor's **"Install from VSIX..."** command (found in the Extensions view `...` menu).

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

[tg]: https://geant4-userdoc.web.cern.ch/UsersGuides/ForApplicationDeveloper/html/Detector/Geometry/geomASCII.html
[VS code]: https://code.visualstudio.com/
[Cursor]: https://cursor.com/
[Antigravity]: https://antigravity.google/
[Releases]: https://github.com/jintonic/geant4-text-geometry-extension/releases
[ovsx_page]: https://open-vsx.org/extension/jintonic/geant4-tg
[NIST Materials]: https://geant4-userdoc.web.cern.ch/UsersGuides/ForApplicationDeveloper/html/Appendix/materialNames.html
[GEARS]: https://github.com/jintonic/gears/tree/master/tutorials/detector/optical
