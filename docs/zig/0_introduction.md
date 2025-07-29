# 0. Introduction to Zig

Welcome to the world of Zig! This series of lectures will guide you through learning Zig, a powerful and modern programming language.

## What is Zig?

Zig is a general-purpose programming language and toolchain for maintaining robust, optimal, and reusable software. It's known for its focus on:

*   **Simplicity:** Zig aims to be a simple language, avoiding hidden control flow and allocations.
*   **Performance:** It compiles to native code, offering performance comparable to C or C++.
*   **Safety:** While it's a low-level language, Zig provides features to help prevent common programming errors.
*   **Comptimes:** A unique feature that allows code to be executed at compile time, enabling powerful metaprogramming.

## Why Learn Zig?

*   **System Programming:** Excellent for operating systems, embedded systems, and high-performance applications.
*   **C/C++ Interoperability:** Seamlessly integrates with C and C++ codebases, making it a great "better C" option.
*   **Toolchain:** Zig comes with its own build system and package manager, simplifying project setup.

## Your First Zig Program: Hello, World!

Let's start with the classic "Hello, World!" program.

First, create a file named `hello_world.zig` in your `docs/zig` directory.

```zig
// hello_world.zig
const std = @import("std");

pub fn main() !void {
    std.debug.print("Hello, World!\n", .{});
}
```

### Explanation:

*   `const std = @import("std");`: This line imports the Zig standard library, which provides many useful functions. `std` is a common alias for it.
*   `pub fn main() !void { ... }`: This defines the `main` function, which is the entry point of every executable Zig program.
    *   `pub`: Means the function is public.
    *   `fn`: Keyword for defining a function.
    *   `main`: The name of the function.
    *   `() `: Indicates that the function takes no arguments.
    *   `!void`: This is a return type. `void` means the function doesn't return any value. The `!` indicates that the function can return an error. In Zig, errors are handled explicitly.
*   `std.debug.print("Hello, World!\n", .{});`: This line calls the `print` function from the `std.debug` module.
    *   The first argument is the format string. `\n` is for a new line.
    *   The second argument, `.{}` (an empty anonymous struct), is for any arguments you want to substitute into the format string. Since we have no placeholders like `{}` in our string, it's empty.

### How to Run It:

1.  Save the `hello_world.zig` file.
2.  Open your terminal or command prompt.
3.  Navigate to the `docs/zig` directory:
    ```bash
    cd docs/zig
    ```
4.  Compile and run the program using the Zig compiler:
    ```bash
    zig run hello_world.zig
    ```

You should see "Hello, World!" printed in your terminal!

This is just the beginning. In the next lectures, we'll dive deeper into Zig's syntax, data types, control flow, and more.
