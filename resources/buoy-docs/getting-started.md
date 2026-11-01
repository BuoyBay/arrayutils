---
title: "ArrayUtils getting started"
summary: "Use numeric reductions, signed slices, and resizable range edits in a complete program."
category: "Guides"
order: 10
keywords: ["resizable", "copy", "reverse", "integer", "double"]
related: ["index.md", "api.md", "typed-api.md"]
---

# Getting started

Install `arrayutils` through BPM or copy `arrayutils-0.1.0.buipkg` into the consumer's `packages/`. Use `Import arrayutils`; no native library is needed.

## Slice and edit

This complete console program calculates an average, copies the final two scores, replaces a String range, and reverses the edited array.

```buoy
Import arrayutils

Sub Main()
    Dim scores As Array Of Integer = [10, 20, 30, 40, 50]
    Print Average(scores)
    Dim tail As Array Of Integer = Slice(scores, -2, 0)
    Print Total(tail)
    Dim editable As Array Of String = Array.AsResizable(["one", "two", "three"])
    Splice(editable, 1, 2, ["second", "inserted"], 0, 0)
    Reverse(editable)
    For Each word As String In editable
        Print word
    Next
End Sub
```

The replacement call removes indices 1 through 1 because finish 2 is exclusive. Its source range `0, 0` means the entire replacement array. Constructing `editable` with `Array.AsResizable` permits structural changes.

## Use functions or extensions

Operations can be called as package functions or extensions, such as `items.Total()` and `items.Slice(-2, 0)`. All range arguments are explicit. This avoids depending on generic-extension default arguments surviving older sealed-package imports.

Validate application ranges before calling, or catch `InvalidArgumentException`. Splice validates both destination and source before editing; a bad source range does not partially remove destination data. Reverse needs no resizing and accepts fixed arrays.

These algorithms are platform-independent source code. Repository verification records runtime execution on Linux x86_64 and compiler checks on all six desktop targets; compiler checks alone do not establish runtime execution on the other systems.

Continue with [API reference](api.md), or return to [ArrayUtils](index.md).
