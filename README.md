This extension provides support for editing Geant4 Text Geometry (.tg) files in [VS Code](https://code.visualstudio.com/), [Cursor](https://cursor.com/), and [Antigravity](https://antigravity.google/).

## Features

- **Syntax Highlighting**: Supports tags, parameters, units, math functions, and solid types.
- **Snippets**: Quick snippets for defining solids, logical volumes, placements, materials, and more.
- **Language Configuration**: Includes comment support and bracket matching.

## Installation

### VSIX Installation

1. Obtain the `.vsix` file from the [GitHub Releases](https://github.com/jintonic/geant4-text-geometry-extension/releases).
2. Install the `.vsix` file through your editor's "Install from VSIX" command.

### Manual Installation

1. Copy this folder to your extensions directory:
   - **VS Code**: `~/.vscode/extensions/geant4-tg`
   - **Cursor**: `~/.cursor/extensions/geant4-tg`
   - **Antigravity**: `~/.antigravity/extensions/geant4-tg`
2. Restart your editor.

## Usage

Simply open any file with the `.tg` extension to enable Geant4 Text Geometry support.

## Syntax Overview

- **Tags**: Start with `:` (e.g., `:SOLID`, `:VOLU`, `:MATE`).
- **Parameters**: Defined with `:P` and referenced with `$`.
- **Units**: Specified with `*` (e.g., `*mm`, `*deg`, `*rad`).
- **Comments**: Start with `//`.
- **Include**: Nest files using `#include`.
- **Solids**: Common types like `BOX`, `TUBE`, `TRD`, `SPHERE`, etc.
- **Math**: Support for arithmetic expressions and functions like `sin`, `cos`, `log`.

## For Developers

### Prerequisites

To build this extension, you need [Node.js](https://nodejs.org/) installed, which includes [npm](https://www.npmjs.com/) and [npx](https://www.npmjs.com/package/npx).

- **macOS**: `brew install node` (using [Homebrew](https://brew.sh/)) or use the official installer.
- **Linux**: `sudo apt install nodejs npm` ([Debian](https://www.debian.org/)/[Ubuntu](https://ubuntu.com/)) or use [NodeSource](https://github.com/nodesource/distributions).
- **Windows**: `winget install OpenJS.NodeJS` or download from [nodejs.org](https://nodejs.org/).

*Pro Tip: Use [nvm](https://github.com/nvm-sh/nvm) (macOS/Linux) or [nvm-windows](https://github.com/coreybutler/nvm-windows) to manage Node versions easily.*

### Building the Extension

To install the [Visual Studio Code Extension Manager (`vsce`)](https://github.com/microsoft/vscode-vsce) globally, run:

```bash
npm install -g @vscode/vsce
```

Once installed, you can build the [VSIX](https://code.visualstudio.com/api/working-with-extensions/publishing-extension#packaging-extensions) package using:

```bash
npx @vscode/vsce package
```
