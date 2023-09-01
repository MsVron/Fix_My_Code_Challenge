# Square-Printing JavaScript Implementation - Issue and Fix

## Introduction

This JavaScript program prints a square using the character `#`. The size of the square is determined by the first argument passed to the program when run in the terminal.

## Issue in Original Implementation

The original implementation had an issue with the way it parsed the input argument to determine the size of the square. Specifically, the line responsible for this was:

```javascript
size = parseInt(process.argv[2], 16);
```

Here, the `parseInt` function is used with a radix of 16, which means it converts the input to an integer using base-16 (hexadecimal). As a result, when the user inputs `10`, it is interpreted as `16` in decimal, leading to a square larger than expected.

## Fix

The fix is simple: change the radix in the `parseInt` function to 10 for decimal conversion. The corrected line of code is:

```javascript
size = parseInt(process.argv[2], 10);
```

With this change, the program will correctly interpret the input as a decimal number, and the square will be printed with the expected size.

## Corrected Code

Here's the corrected code snippet:

```javascript
if (process.argv.length <= 2) {
    process.stderr.write("Missing argument\n");
    process.stderr.write("Usage: ./1-print_square.js <size>\n");
    process.stderr.write("Example: ./1-print_square.js 8\n");
    process.exit(1);
}

size = parseInt(process.argv[2], 10);

for (let i = 0; i < size; i++) {
    for (let j = 0; j < size; j++) {
        process.stdout.write("#");
    }
    process.stdout.write("\n");
}
```

## Conclusion

By changing the radix in the `parseInt` function, the square-printing JavaScript program now works as expected. Always remember to carefully consider the radix when using functions like `parseInt` that have it as an optional parameter.
