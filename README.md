# Crafting Interpreters — Chapters 4 and 5

This repository contains the complete Java code needed for Chapters 4 and 5,
including nested C-style block comments and the RPN printer challenge.

## Compile

From this folder, run:

```bash
javac com/craftinginterpreters/lox/*.java
```

## Test

```bash
java com.craftinginterpreters.lox.Lox examples/block_comments.lox
```

The scanner should produce tokens for the two `print` statements but no tokens
for the comments. The final `EOF` token should be reported on line 9.

Test the Chapter 5 RPN printer with:

```bash
java com.craftinginterpreters.lox.RpnPrinter
```

Expected output:

```text
1 2 + 4 3 - *
```

## Written response

Supporting nested comments requires the scanner to track how many comments are
open. Each `/*` increases the nesting level, while each `*/` decreases it. The
scanner must also count newlines inside comments to keep line numbers accurate.
