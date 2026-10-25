# GOG: Beginner to Advanced Tutorial

> GOG is an early-stage language design. The editor extension currently provides syntax highlighting and snippets, not a complete compiler or runtime. Examples marked **planned syntax** describe the intended language and will not run until the corresponding runtime features exist.

## 1. Your first program

Create a file named `hello.gog`:

```gog
show("Hello World!")
```

This is the first GOG command: `show(...)` displays a message. The current Python starter interpreter supports this command; the editor extension only colours it.

## 2. Text and values

Use quotes for text:

```gog
show("Welcome to GOG")
show("I am learning to code")
```

Planned variable syntax:

```gog
name = "Alex"
score = 10
show(name)
show(score)
```

Variables and displaying variable values require runtime support beyond the current starter interpreter.

## 3. Comments

Use `//` for a single-line comment:

```gog
// This line explains the next command
show("Hello!")
```

Comments help you and other people understand your code.

## 4. Basic maths

Planned expression examples:

```gog
show(2 + 3)
show(10 * 4)
show(20 / 5)
```

The starter interpreter supports safe basic arithmetic expressions inside `show(...)`.

## 5. Create a window

**Planned UI syntax** — requires a future GOG UI runtime:

```gog
Window("My App") {
    Background("Light Blue")
    ShowHeading("Welcome!")
}
```

- `Window("My App")` names the app window.
- `Background("Light Blue")` uses a human-readable colour name.
- `ShowHeading("Welcome!")` adds a heading.

Use names like `"Red"`, `"Blue"`, `"Light Blue"`, `"Dark Green"`, `"Black"`, or `"White"`. Hex values such as `"#176528"` are not required by this intended syntax.

## 6. Buttons and actions

**Planned UI syntax:**

```gog
Window("Counter App") {
    Background("Dark Blue")
    ShowHeading("Tap the button")

    Button("Click Me") {
        show("Button Clicked!")
    }
}
```

The block inside `Button(...)` describes what should happen when the button is clicked. A UI runtime still needs to implement it.

## 7. Conditions

**Planned syntax:**

```gog
age = 18

If age >= 18 {
    show("Adult")
} Else {
    show("Under 18")
}
```

Conditions let a program choose which instructions to run. Exact grammar and execution are still being designed.

## 8. Repeating work

**Planned syntax:**

```gog
Repeat(5) {
    show("Hello again")
}
```

A loop repeats a block of instructions. Loop execution is not yet implemented in the starter interpreter.

## 9. Functions

**Planned syntax:**

```gog
Function greet(name) {
    show("Hello")
}

greet("Alex")
```

Functions group reusable instructions. Parameter interpolation and function calls need a proper parser/runtime.

## 10. Web pages and app interfaces

**Planned direction:**

```gog
Window("Portfolio") {
    Background("White")
    ShowHeading("My Portfolio")
    Text("I build apps and games.")
    Button("Contact Me") {
        show("Thanks for visiting!")
    }
}
```

A future UI toolkit could translate this structure into native UI or HTML/CSS. That translation is not included in the current extension.

## 11. 3D games

**Planned direction:**

```gog
Game3D("My World") {
    CreateWorld()
    CreatePlayer("Hero")
    AddCamera()
    AddLight()
}
```

A real 3D engine would need to implement world creation, player movement, camera controls, lighting, assets, physics and rendering. These commands are examples of the proposed API, not working 3D features yet.

## 12. AI features

**Planned direction:**

```gog
AI("My Assistant") {
    Learn("data.txt")
    Answer("Hello")
}
```

A real AI module needs a defined model/runtime interface, data handling, and clear offline/online behaviour. This sample does not train a model or connect to an AI service.

## 13. Use the GOG snippets in VSCodroid

1. Install the GOG Language Support extension from Open VSX when published, or install its VSIX package.
2. Create or open a file ending in `.gog`.
3. Type a snippet prefix such as `show`, `window`, `button`, `game3d`, or `ai`.
4. Select the suggestion and replace the placeholder text.

## 14. Build and test the extension

From this folder:

```bash
npx --yes @vscode/vsce package --no-dependencies
```

This should create a `.vsix` package. The GitHub Actions workflow validates the JSON files and packages the extension on pushes, pull requests and manual runs.

## 15. Advanced roadmap

The intended development order is:

1. Formal grammar and parser with useful error messages.
2. Stable types, variables, expressions, conditions, loops and functions.
3. Standard library and file operations with safe defaults.
4. UI runtime for windows, layouts, text, colours and buttons.
5. Web output/compiler for HTML/CSS/JavaScript.
6. Game integration or a small 2D/3D runtime.
7. AI adapters with explicit local/remote configuration.
8. Unit tests, compatibility guarantees, documentation and versioned releases.

Do not treat the planned examples as implemented features until the matching runtime and tests have been released.
