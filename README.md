# Crafting Interpreters — Chapters 4–6

This repository contains the Java code for Chapters 4–6, including nested
C-style block comments, the RPN printer, and all three Chapter 6 parsing
challenges.

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

## Chapter 6 tests

Start the prompt:

```bash
java com.craftinginterpreters.lox.Lox
```

Comma expressions are left-associative and have the lowest precedence:

```text
> 1 + 2, 3 * 4
(, (+ 1.0 2.0) (* 3.0 4.0))
> 1, 2, 3
(, (, 1.0 2.0) 3.0)
```

The conditional operator is right-associative:

```text
> true ? 1 : false ? 2 : 3
(?: true 1.0 (?: false 2.0 3.0))
```

A binary operator without a left operand reports a targeted error:

```text
> + 1 * 2
[line 1] Error at '+': Missing left-hand operand.
```