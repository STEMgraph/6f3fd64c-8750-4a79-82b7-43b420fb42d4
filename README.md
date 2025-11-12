<!---
{
  "id": "6f3fd64c-8750-4a79-82b7-43b420fb42d4",
  "teaches": "Using Foreground and Background Colors in the Linux Terminal",
  "author": "Stephan Bökelmann",
  "depends_on": ["cdd3d87d-0e87-4a00-a676-83ca9f245bd7"],
  "first_used": "2025-03-20",
  "keywords": ["learning", "exercises", "education", "practice", "ANSI escape codes", "terminal colors"]
}
--->

# Using Foreground and Background Colors in the Linux Terminal

## 1) Introduction

Modern terminal emulations support **ANSI escape codes**, which allow users to modify text appearance, including **color**, **boldness**, and **cursor positioning**. This feature has been widely used in **system logs**, **command-line utilities**, and even **text-based user interfaces**.

The **ANSI escape sequences** were first introduced with the **DEC VT100** terminal in the 1970s. These sequences, prefixed by the **ESC** (escape) character, are still widely supported in modern terminal emulators.

Understanding how to use these escape codes will enable you to create **visually structured terminal outputs**, improving clarity and readability.

## 1.1) Basic Color Control

Text color in the terminal is controlled using the following format:

```
\033[<STYLE>;<FOREGROUND>;<BACKGROUND>m
```

Where:
- `\033[` is the escape character (`ESC` in ASCII)
- `<STYLE>` defines the **text style** (e.g., bold, underlined)
- `<FOREGROUND>` specifies the **text color**
- `<BACKGROUND>` sets the **background color**
- `m` terminates the sequence

To reset color back to default, use:
```
\033[0m
```

## 1.2) Color Codes

### 1.2.1) Text Style Codes
| Code | Style        |
|------|-------------|
| 0    | Reset       |
| 1    | Bold        |
| 4    | Underlined  |
| 7    | Inverted    |

### 1.2.2) Foreground Color Codes
| Code | Color     |
|------|-----------|
| 30   | Black     |
| 31   | Red       |
| 32   | Green     |
| 33   | Yellow    |
| 34   | Blue      |
| 35   | Magenta   |
| 36   | Cyan      |
| 37   | White     |

### 1.2.3) Background Color Codes
| Code | Color     |
|------|-----------|
| 40   | Black     |
| 41   | Red       |
| 42   | Green     |
| 43   | Yellow    |
| 44   | Blue      |
| 45   | Magenta   |
| 46   | Cyan      |
| 47   | White     |

## 1.3) Further Readings and Other Sources
- [ANSI Escape Codes on Wikipedia](https://en.wikipedia.org/wiki/ANSI_escape_code)
- [Bash Prompt Escape Sequences](https://tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html)

## 3) Tasks

1. Print Colored Text
Write a C program that prints "Hello, World!" in red using ANSI escape codes.

```c
#include <stdio.h>

int main() {
    printf("\033[31mHello, World!\033[0m\n");
    return 0;
}
```

2. Combine Foreground and Background Colors
Modify the program to print "Colorful Text!" in yellow with a blue background.

```c
#include <stdio.h>

int main() {
    printf("\033[33;44mColorful Text!\033[0m\n");
    return 0;
}
```

3. Create a Rainbow Effect
Write a program that prints a rainbow of colors.

```c
#include <stdio.h>

int main() {
    for (int i = 30; i <= 37; i++) {
        printf("\033[%dmColor %d\033[0m\n", i, i);
    }
    return 0;
}
```

4. Experiment with Text Styles
Try different text styles like **bold**, **underlined**, and **inverted**.

```c
#include <stdio.h>

int main() {
    printf("\033[1mBold Text\033[0m\n");
    printf("\033[4mUnderlined Text\033[0m\n");
    printf("\033[7mInverted Text\033[0m\n");
    return 0;
}
```

## 4) Questions

1. What happens if you omit `\033[0m` at the end of a print statement?
2. Can you find a way to use RGB colors in the terminal instead of the 8 basic ones?
3. How does your terminal handle escape codes? Do some codes work differently in different terminal emulators?

## 5) Advice

Mastering ANSI escape codes can significantly enhance command-line applications, making logs more readable and CLI tools more interactive. Try integrating these techniques into your scripts, command-line utilities, and even progress indicators!

For advanced users, **TrueColor (24-bit color)** support allows for finer control over color output. Research `\033[38;2;<R>;<G>;<B>m` for foreground colors and `\033[48;2;<R>;<G>;<B>m` for background colors!
