---
weight: 5
title: "screenCol(pixelX, x, cellLength)"
---

Returns the quadrille col to which the screen space `pixelX` coordinate belong.

{{< callout type="warning" >}}
1. `screenCol(pixelX, x, cellLength)` returns a value not constrain to lie in [0..[width]({{< ref "width" >}})].
2. If the quadrille is currently being drawn use the [mouseCol]({{< ref "mouse_col" >}}) property instead.
{{< /callout >}}

## Syntax

> `screenCol(pixelX, [x], [cellLength])`

## Parameters

| Param  | Description                                                                                              |
|------------|----------------------------------------------------------------------------------------------------------|
| `pixelX`     | Number: screen space x-coord                                                                             |
| `x`          | Number: quadrille upper left corner x-coord. If not provided it's value is inferred from `drawQuadrille` |
| `cellLength` | Number: cell length. If not provided it's value is inferred from `drawQuadrille`                         |