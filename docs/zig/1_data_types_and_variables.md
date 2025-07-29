# 1. Data Types and Variables in Zig

In this lecture, we'll explore the fundamental building blocks of any programming language: data types and variables. Understanding these concepts is crucial for storing and manipulating information in your Zig programs.

## Variables: Storing Data

In Zig, you declare variables using `var` for mutable variables (whose values can change) and `const` for immutable variables (whose values cannot change after initialization).

### Declaring Mutable Variables (`var`)

```zig
// mutable_variables.zig
const std = @import("std");

pub fn main() !void {
    var age: u8 = 30; // Declare a mutable variable 'age' of type u8 and initialize it to 30
    std.debug.print("Initial age: {d}\n", .{age});

    age = 31; // You can change the value of 'age'
    std.debug.print("New age: {d}\n", .{age});

    var name: []const u8 = "Alice"; // A mutable string (slice of constant bytes)
    std.debug.print("Name: {s}\n", .{name});

    name = "Bob"; // Change the name
    std.debug.print("New Name: {s}\n", .{name});
}
```

**Explanation:**
*   `var age: u8 = 30;`: This declares a variable named `age`.
    *   `var`: Keyword for a mutable variable.
    *   `age`: The name of the variable.
    *   `: u8`: This specifies the type of the variable. `u8` means an unsigned 8-bit integer (can hold values from 0 to 255).
    *   `= 30;`: Initializes the variable with the value 30.
*   `[]const u8`: This is the type for a string literal in Zig, representing a slice of constant unsigned 8-bit integers (bytes).

### Declaring Immutable Variables (`const`)

```zig
// immutable_variables.zig
const std = @import("std");

pub fn main() !void {
    const PI: f32 = 3.14159; // Declare an immutable constant 'PI' of type f32
    std.debug.print("Value of PI: {f}\n", .{PI});

    // PI = 3.0; // This line would cause a compile-time error!
    // std.debug.print("New PI: {f}\n", .{PI});

    const GREETING = "Hello"; // Type inference: Zig infers []const u8
    std.debug.print("Greeting: {s}\n", .{GREETING});
}
```

**Explanation:**
*   `const PI: f32 = 3.14159;`: Declares an immutable constant `PI`.
    *   `const`: Keyword for an immutable variable (constant).
    *   `f32`: A 32-bit floating-point number.
*   Once a `const` variable is initialized, its value cannot be changed. Trying to reassign it will result in a compile-time error, which is a great safety feature!
*   Zig can often infer the type of a `const` variable if you initialize it immediately, like `const GREETING = "Hello";`.

## Basic Data Types

Zig has a rich set of built-in data types. Here are some of the most common ones:

### Integers

Zig provides fixed-width integers, both signed (`i`) and unsigned (`u`). The number after `i` or `u` indicates the number of bits.

*   `u1`, `u8`, `u16`, `u32`, `u64`, `u128`: Unsigned integers (0 and positive values).
*   `i1`, `i8`, `i16`, `i32`, `i64`, `i128`: Signed integers (positive, negative, and zero values).
*   `usize`, `isize`: Integer types whose size matches the pointer size of the target architecture (e.g., 32-bit on a 32-bit system, 64-bit on a 64-bit system). Useful for sizes and indices.

```zig
// integers.zig
const std = @import("std");

pub fn main() !void {
    var small_num: u8 = 255; // Max value for u8
    std.debug.print("Small num: {d}\n", .{small_num});

    var big_num: i32 = -123456;
    std.debug.print("Big num: {d}\n", .{big_num});

    var index: usize = 100; // Good for array indices
    std.debug.print("Index: {d}\n", .{index});
}
```

### Floating-Point Numbers

*   `f16`, `f32`, `f64`, `f128`: Floating-point numbers with different precision. `f32` is single-precision, `f64` is double-precision.

```zig
// floats.zig
const std = @import("std");

pub fn main() !void {
    var temperature: f32 = 25.5;
    std.debug.print("Temperature: {f}\n", .{temperature});

    var gravity: f64 = 9.80665;
    std.debug.print("Gravity: {f}\n", .{gravity});
}
```

### Booleans

*   `bool`: Represents truth values, either `true` or `false`.

```zig
// booleans.zig
const std = @import("std");

pub fn main() !void {
    var is_active: bool = true;
    std.debug.print("Is active: {any}\n", .{is_active});

    var has_permission: bool = false;
    std.debug.print("Has permission: {any}\n", .{has_permission});
}
```

### Pointers

*   `*T`: A pointer to a value of type `T`. Zig has explicit pointers, which is a key feature for low-level control.

```zig
// pointers.zig
const std = @import("std");

pub fn main() !void {
    var x: i32 = 10;
    var ptr_x: *i32 = &x; // ptr_x now points to the memory location of x

    std.debug.print("Value of x: {d}\n", .{x});
    std.debug.print("Value pointed to by ptr_x: {d}\n", .{ptr_x.*}); // Dereference the pointer

    ptr_x.* = 20; // Change the value through the pointer
    std.debug.print("New value of x: {d}\n", .{x});
}
```

**Explanation:**
*   `&x`: The address-of operator, which gives you a pointer to `x`.
*   `ptr_x.*`: The dereference operator, which gives you the value stored at the memory location pointed to by `ptr_x`.

## Type Inference

While explicit type declarations are common and often recommended for clarity, Zig can infer types in many situations, especially with `const` declarations.

```zig
// type_inference.zig
const std = @import("std");

pub fn main() !void {
    const inferred_int = 100; // Inferred as i32 by default
    std.debug.print("Inferred int: {d}\n", .{inferred_int});

    const inferred_float = 3.14; // Inferred as f64 by default
    std.debug.print("Inferred float: {f}\n", .{inferred_float});

    const inferred_bool = true; // Inferred as bool
    std.debug.print("Inferred bool: {any}\n", .{inferred_bool});
}
```

## Next Steps

In the next lecture, we'll explore control flow, including `if` statements, `while` loops, and `for` loops, to make your programs more dynamic.
