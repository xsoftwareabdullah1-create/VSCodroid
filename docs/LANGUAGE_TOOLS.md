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

## Language coverage

VSCodroid uses the VS Code editor and Open VSX extensions, so its language coverage is extensible rather than limited to a fixed list. The base editor provides editing and syntax highlighting for many common formats; install a language extension when you need richer completion, diagnostics, formatting, or debugging.

| Language / format | Editor support and what is needed to run it |
| --- | --- |
| JavaScript, TypeScript, HTML, CSS, JSON, Markdown | Core editing support; Node.js is bundled for JavaScript execution. TypeScript can use the bundled Node.js runtime, while project-specific packages may need installing. |
| Python | Python 3 is bundled. Install the Python extension from Open VSX for richer language features. |
| Java | Install the optional Java 21 toolchain and a compatible Java extension. |
| C and C++ | Install the optional C/C++ toolchain. Use a compatible extension for language-server features. |
| Ruby | Install the optional Ruby toolchain and a compatible Ruby extension. |
| PHP, Go, Rust, C#, Kotlin, Dart/Flutter, Swift, SQL, YAML, XML, Shell/Bash, Dockerfiles and other formats | Search Open VSX for a compatible language extension. A syntax extension does not itself install a compiler, SDK, debugger, or runtime; those must be installed separately and may not be available or usable on Android/ARM64. |

This is broad language-editor support, **not a promise that every programming language has a working on-device compiler**. Some ecosystems (for example, .NET, Flutter, Android SDK builds, Swift, or Rust targets) need large SDKs, unsupported native components, or platform-specific setup. Check the extension's VS Code engine requirement and Android/ARM64 support before relying on it.

## Android 8.0 / 8.1 compatibility

Android 8.0 is API 26 and Android 8.1 is API 27. The app's current minimum SDK is API 24, so both versions are within the declared range. Android 8.x compatibility still depends on the bundled VS Code server, native ARM64 binaries, WebView provider, and any installed extensions/toolchains. The app should be verified on API 26 and API 27 devices or emulators before calling those versions fully tested.

The app's minimum SDK setting alone does not prove every bundled native binary, extension, or language server works on Android 8.x. Treat a language as supported for compile/run and diagnostics only after installing it and testing those features on the target Android version.

## Troubleshooting

- **Toolchain install fails:** check internet access and free storage, then use **Retry** in Manage toolchains.
- **Language has no completion or diagnostics:** install a compatible language extension and its required runtime/compiler.
- **Extension will not install or activate:** check its VS Code engine requirement and whether it supports Android/ARM64; try another Open VSX release compatible with the bundled editor.
- **Compiler command not found:** confirm the toolchain is installed, then open a new terminal.
