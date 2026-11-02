---
title: "ArrayUtils API"
summary: "Generic half-open range operations and Integer or Double reduction overloads."
category: "Reference"
order: 20
keywords: ["Slice", "Splice", "RemoveSlice", "AppendAll", "Reverse", "Total", "Average", "Min", "Max"]
symbols: ["Slice", "RemoveSlice", "Splice", "AppendAll", "Reverse", "Total", "Average", "Min", "Max"]
related: ["index.md", "getting-started.md", "typed-api.md"]
---

# API reference

## Generic array operations

| Function or Sub | Behavior |
| --- | --- |
| `Slice(items, first, finish)` | Fresh resizable array containing the half-open signed range |
| `RemoveSlice(items, first, finish)` | Remove the range in place; empty valid ranges are no-ops even on fixed arrays |
| `Splice(items, first, finish, source, sourceFirst, sourceFinish)` | Replace destination range with a snapshot of the source range |
| `AppendAll(items, source)` | Append a source snapshot; self-append is supported |
| `Reverse(items)` | Reverse elements in place, including fixed arrays |

All generic operations support statically known element types. Ranges normalize negative indices relative to Count; finish zero means Count. Normalized first/finish must satisfy `0 <= first <= finish <= Count`, otherwise `InvalidArgumentException` is thrown before mutation.

Splice and AppendAll require a resizable destination even when the logical change might be empty. RemoveSlice requires resizing only for a nonempty range. Class elements retain normal reference identity; slicing is not a deep clone. Existing `Array.Clone` and `Array.Concat` cover cloning and concatenation, so the package does not add competing functions for them.

## Numeric reductions

| Function | Integer array result | Double array result |
| --- | --- | --- |
| `Total(items)` | Integer sum | Double sum |
| `Average(items)` | Fractional Double mean | Double mean |
| `Min(items)` | Integer minimum | Double minimum |
| `Max(items)` | Integer maximum | Double maximum |

All reductions return zero for empty input. Average accumulates in Double to avoid Integer division truncation and Integer-sum overflow in the mean. Very large Integer values can lose Double precision. Integer Total uses ordinary Integer arithmetic; there is no arbitrary precision or special NaN/infinity treatment.

All operations are also extensions on compatible arrays. The package neither changes Buoy's native array implementation nor synchronizes concurrent edits. Keep aliases and mutation ownership explicit.

See the [getting-started example](getting-started.md) and [overview](index.md).

[Full typed API: properties, parameters, defaults, and returns](typed-api.md)
