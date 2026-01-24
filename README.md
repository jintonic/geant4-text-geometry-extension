# Geant4 Text Geometry Extension

This extension provides support for editing Geant4 Text Geometry (.tg) files in VS Code, Cursor, and Antigravity.

## Features

- **Syntax Highlighting**: Supports tags, parameters, units, math functions, and solid types.
- **Snippets**: Quick snippets for defining solids, logical volumes, placements, materials, and more.
- **Language Configuration**: Includes comment support and bracket matching.

## Installation

### Manual Installation

1. Copy this folder to your extensions directory:
   - **VS Code**: `~/.vscode/extensions/geant4-tg`
   - **Cursor**: `~/.cursor/extensions/geant4-tg`
   - **Antigravity**: `~/.antigravity/extensions/geant4-tg` (or follow the specific Antigravity extension installation guide)
2. Restart your editor.

### VSIX Installation

1. Build the VSIX package (if you have `vsce` installed):
   ```bash
   npx @vscode/vsce package
   ```
2. Install the `.vsix` file through your editor's "Install from VSIX" command.

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
