# Language Toolchains and Extensions

VSCodroid separates **runtimes/compilers** from **editor extensions**. Installing one does not automatically install the other.

## 1. Install a runtime or compiler

Open the Android launcher and touch and hold the VSCodroid app icon, then choose **Manage toolchains**. You can also open the VS Code Command Palette with `Ctrl+Shift+P` and run **VSCodroid: Manage Toolchains**.

The manager supports installing, monitoring, retrying, cancelling, and removing the available optional toolchains:

| Toolchain | What it enables |
| --- | --- |
| Ruby | Run Ruby scripts and use Ruby tooling |
| Java 21 | Compile and run Java programs; Java language-server extensions may need this |
| C/C++ | Compile and run C/C++ programs with the bundled Clang toolchain |

**Python 3 and Node.js/npm are included in the base installation**; they do not need a separate toolchain download. Git, Bash, SSH, and other command-line utilities are included too.

Downloads use the app's supported delivery/download path. Keep enough free storage for both the downloaded archive and the extracted toolchain. The manager displays the relevant size and progress, and provides retry/cancel/remove actions where applicable. Internet access is required to download a toolchain.

### Run a program

Open a supported source file and use its Run action when available, or run it in the integrated terminal:

```bash
python3 hello.py
node app.js
ruby hello.rb
javac Main.java && java Main
clang hello.c -o hello && ./hello
clang++ main.cpp -o main && ./main
```

Ruby, Java, and C/C++ require their corresponding optional toolchain to be installed first. Python and Node.js are ready in the base environment.

## 2. Install language extensions from Open VSX

VSCodroid's editor uses the VS Code Extensions view, with Open VSX as the extension registry.

1. Open the editor.
2. Press `Ctrl+Shift+X` to open **Extensions**. On a touch screen, open the Command Palette with `Ctrl+Shift+P` and search for **Extensions: Focus on Extensions View**, or tap the Extensions icon in the activity bar if it is visible.
3. Search for the language or tool you need (for example, Python, Java, C/C++, ESLint, or Prettier).
4. Open the result and choose **Install**. Follow any extension-specific setup instructions.

Extensions can provide syntax highlighting, completion, diagnostics, formatting, debugging, and language-server support, but those capabilities depend on the extension and the required runtime. For example, Java language support requires the Java toolchain; installing only the extension is not a JDK.

Open VSX is a separate registry, so not every extension from Microsoft's Visual Studio Marketplace is available there. Extension downloads require internet access. Some extensions may not support this app's bundled VS Code version or Android/ARM64 environment; check compatibility before relying on them.

## Android 7 (API 24) note

The app's minimum SDK setting is API 24, but that setting alone does not prove every bundled native binary, extension, or language server works on Android 7. Native toolchains and extensions can have their own Android, ABI, or VS Code-version requirements. Treat a language as supported on Android 7 only after installing it and testing a real compile/run and editor diagnostics on an Android 7 device or emulator.

## Troubleshooting

- **Toolchain install fails:** check internet access and free storage, then use **Retry** in Manage toolchains.
- **Language has no completion or diagnostics:** install a compatible language extension and its required runtime/compiler.
- **Extension will not install or activate:** check its VS Code engine requirement and whether it supports Android/ARM64; try another Open VSX release compatible with the bundled editor.
- **Compiler command not found:** confirm the toolchain is installed, then open a new terminal.
