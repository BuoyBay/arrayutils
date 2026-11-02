---
title: "arrayutils typed API"
summary: "Source-derived public signatures, properties, parameters, defaults, and return values."
category: "Reference"
order: 21
types: []
dependencies: []
symbols: ["AppendAll", "Average", "Max", "Min", "RemoveSlice", "Reverse", "Slice", "Splice", "Total"]
related: ["api.md", "getting-started.md", "index.md"]
---

# arrayutils typed API

Generated from the package source declarations. Platform guards are shown where present; inherited members are documented on the base type. See the [API contracts](api.md) for behavior and limitations.

### Slice

`Public Extension Function Slice Of T(items As Array Of T, first As Integer, finish As Integer) As Array Of T`

Copy a half-open range; negative indices count back from the end, finish=0 means end.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `items` | `Array Of T` | `ByVal` | Required |
| `first` | `Integer` | `ByVal` | Required |
| `finish` | `Integer` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Array Of T` |

### RemoveSlice

`Public Extension Sub RemoveSlice Of T(items As Array Of T, first As Integer, finish As Integer)`

Remove a half-open range. Structural mutation requires a resizable array.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `items` | `Array Of T` | `ByVal` | Required |
| `first` | `Integer` | `ByVal` | Required |
| `finish` | `Integer` | `ByVal` | Required |

Returns: no value.

### Splice

`Public Extension Sub Splice Of T(items As Array Of T, first As Integer, finish As Integer, source As Array Of T, sourceFirst As Integer, sourceFinish As Integer)`

Replace a range with a snapshot of the source range; self-splicing is supported.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `items` | `Array Of T` | `ByVal` | Required |
| `first` | `Integer` | `ByVal` | Required |
| `finish` | `Integer` | `ByVal` | Required |
| `source` | `Array Of T` | `ByVal` | Required |
| `sourceFirst` | `Integer` | `ByVal` | Required |
| `sourceFinish` | `Integer` | `ByVal` | Required |

Returns: no value.

### AppendAll

`Public Extension Sub AppendAll Of T(items As Array Of T, source As Array Of T)`

Append every source element, using a snapshot so self-append terminates.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `items` | `Array Of T` | `ByVal` | Required |
| `source` | `Array Of T` | `ByVal` | Required |

Returns: no value.

### Reverse

`Public Extension Sub Reverse Of T(items As Array Of T)`

Reverse in place, including fixed arrays.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `items` | `Array Of T` | `ByVal` | Required |

Returns: no value.

### Total

`Public Extension Function Total(items As Array Of Integer) As Integer`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `items` | `Array Of Integer` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Integer` |

### Average

`Public Extension Function Average(items As Array Of Integer) As Double`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `items` | `Array Of Integer` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Double` |

### Min

`Public Extension Function Min(items As Array Of Integer) As Integer`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `items` | `Array Of Integer` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Integer` |

### Max

`Public Extension Function Max(items As Array Of Integer) As Integer`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `items` | `Array Of Integer` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Integer` |

### Total (overload 2)

`Public Extension Function Total(items As Array Of Double) As Double`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `items` | `Array Of Double` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Double` |

### Average (overload 2)

`Public Extension Function Average(items As Array Of Double) As Double`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `items` | `Array Of Double` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Double` |

### Min (overload 2)

`Public Extension Function Min(items As Array Of Double) As Double`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `items` | `Array Of Double` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Double` |

### Max (overload 2)

`Public Extension Function Max(items As Array Of Double) As Double`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `items` | `Array Of Double` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Double` |
