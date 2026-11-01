---
title: "ArrayUtils"
summary: "Edit signed array ranges and calculate numeric reductions in pure Buoy."
category: "Overview"
order: 0
keywords: ["array", "range", "slice", "splice", "average"]
related: ["getting-started.md", "api.md", "typed-api.md"]
---

# ArrayUtils

ArrayUtils adds generic signed-range array editing and Integer/Double reductions. It is pure Buoy with no native dependencies. Use it for half-open slices, in-place range replacement, safe self-append, and small numeric aggregations.

## Range model

Ranges use a zero-based first index and an exclusive finish index. Negative indices count back from the end. A finish of zero means the end of the array, so `Slice(items, 0, 0)` copies everything and `Slice(items, -2, 0)` copies the final two elements.

This differs from the built-in `Array.Slice` start/count convention. In a nonempty array, use equal positive first/finish values for an empty range. Zero cannot denote an exclusive end at the beginning because it is the end-of-array sentinel.

## Mutation and ownership

`RemoveSlice`, `Splice`, `AppendAll`, and `Reverse` modify the existing array object, so aliases observe edits. Structural changes require a resizable array. Slice results are fresh resizable arrays; class elements are copied shallowly. Splice and append snapshot the source, making overlapping self-edits well-defined.

The numeric functions return zero for empty arrays. Integer averages accumulate and divide as Double, preserving fractional results while accepting Double precision loss for very large integers. Integer totals keep Integer arithmetic.

The API is independently implemented from the original ArrayUtils idea, with stricter range validation. No compiler runtime or native array implementation is changed.

Read [Getting started](getting-started.md) and the [API reference](api.md).
