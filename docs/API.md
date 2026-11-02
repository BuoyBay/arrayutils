# ArrayUtils 0.1.0

Pure Buoy array range editing and numeric reductions inspired by [Joe Strout's
REALbasic ArrayUtils](https://strout.net/info/coding/rb/intro.html). Source and
sealed `.buipkg` consumers use `Import arrayutils`. No native dependencies.

## API and parity

| Original operation | Buoy equivalent |
| --- | --- |
| `Total`, `Average`, `Min`, `Max` | Package functions with Integer and Double array overloads |
| `Slice` | `Slice(items, first, finish)`, generic over element type |
| `RemoveSlice` | `RemoveSlice(items, first, finish)`, mutates in place |
| `Splice` | `Splice(items, first, finish, source, sourceFirst, sourceFinish)` |
| Array-valued `Append` | `AppendAll(items, source)`; avoids ambiguity with element append |
| `Reverse` | `Reverse(items)`, mutates in place |
| `Clone`, `Concat` | Existing `Array.Clone(items)`, `Array.Concat(left, right)` |

Functions are also extensions (`items.Total()`, `items.Slice(-2, 0)`). All range
arguments are explicit: the installed Buoy 0.72.0 compiler lost generic-extension
default arguments through sealed-package imports during development. The API
therefore does not depend on defaults surviving packaging.

Ranges follow the original **exclusive end index** convention, rather than
Buoy's built-in `Array.Slice` start/count convention. Negative indices count from
the end; `finish = 0` means the end. For `[1,2,3,4,5]`, `Slice(items,-2,0)` returns
`[4,5]`, and `Slice(items,0,-3)` returns `[1,2]`. To copy everything pass `0,0`.
An empty range in a nonempty array is `first = finish > 0`; zero cannot denote an
exclusive end at the beginning because it is the original end-of-array sentinel.

Ranges outside `0..Count`, or reversed ranges, throw `InvalidArgumentException`
before mutation. This is deliberately stricter than the original's inconsistent
invalid-range behavior. `Splice` validates both ranges before editing and takes
a snapshot of the source range, supporting overlapping self-splicing. `AppendAll`
also snapshots its source, so appending an array to itself is safe.

Structural edits require `Array.AsResizable(...)` or an initially empty resizable
array. `RemoveSlice` on an empty valid range is a no-op even for fixed arrays;
`Splice` and `AppendAll` require resizable arrays. `Reverse` accepts both modes.
`Slice` returns a fresh resizable array; copying class elements is shallow.
Edits preserve the array object so aliases observe the changes.

Numeric reductions return zero for empty arrays. `Average` accumulates in Double
and returns a fractional Double for Integer input. This avoids truncating integer
division and integer-sum overflow in the mean, but very large integers lose Double
precision. `Total(Integer)` retains Integer arithmetic; no arbitrary precision or
special handling of NaN/infinity is added. No native Array implementation or
compiler runtime was changed.

## Use with bpm

From a consumer project, use the source checkout as an explicit local dependency:

```sh
bpm add arrayutils --path /absolute/path/to/arrayutils
```

BPM resolves the package and installs the resulting archive in the consumer's
`packages/` directory. The source has no other package dependencies.

## Source and compatibility

The [provenance notes](../PROVENANCE.md) identify the original API inspiration
and the semantic differences of this independent implementation.
