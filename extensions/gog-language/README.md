# GOG Language Support

Syntax highlighting and starter snippets for files ending in `.gog`.

## Features

- Recognizes `.gog` files as GOG.
- Highlights strings, numbers, comments, keywords and common GOG commands.
- Adds snippets for output, simple app windows, buttons, and proposed 3D/AI structures.
- Works as an editor extension; it does not install a GOG runtime.

## Example

```gog
show("Hello World!")

Window("My App") {
    Background("Light Blue")
    ShowHeading("Welcome!")
}
```

Colour names are written as words such as `"Light Blue"`; hexadecimal colour codes are not required.

## Install in VSCodroid

1. Open Extensions in VSCodroid.
2. Search for **GOG Language Support** once it is available in the Open VSX registry.
3. Install it, then open or create a `.gog` file.

If the extension is not yet listed, install the packaged `.vsix` using **Extensions: Install from VSIX...**.

## Current limits

This release provides editor syntax highlighting and snippets only. A complete GOG interpreter/compiler, UI toolkit, 3D engine and AI runtime are separate projects and are not claimed to be implemented by this extension.

## Development

The repository workflow checks the manifest and packages a VSIX. Publishing to Open VSX additionally requires a registered publisher namespace and an Open VSX access token.
