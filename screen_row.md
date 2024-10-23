---
weight: 15
draft: false
title: "screenRow(pixelY, y, cellLength)"
---

Returns the quadrille row to which the screen space `pixelY` coordinate belong.

{{< callout type="warning" >}}
**Observations**  
1. `screenRow(pixelY, y, cellLength)` returns a value not constrain to lie in [0..[height]({{< ref "height" >}})].
2. If the quadrille is currently being drawn use the [mouseRow]({{< ref "mouse_row" >}}) property instead.
{{< /callout >}}

# Syntax

> `screenRow(pixelY, [y], [cellLength])`

# Parameters

| parameter  | description                                                                                              |
|------------|----------------------------------------------------------------------------------------------------------|
| pixelY     | Number: screen space y-coord                                                                             |
| y          | Number: quadrille upper left corner y-coord. If not provided it's value is inferred from `drawQuadrille` |
| cellLength | Number: cell length. If not provided it's value is inferred from `drawQuadrille`                         |