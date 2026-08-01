---
weight: 3
title: "isEmpty(row, col)"
---

Returns `true` if the cell found at `(row, col)` is empty and `false` otherwise. Empty means `== null` — which catches both `null` (the empty-cell value) **and** `undefined`. Since an out-of-bounds [read]({{< ref "read" >}}) returns `undefined`, **out-of-bounds positions count as empty too**.

{{< callout type="warning" >}}
**Guard order matters in traversals.** Because out-of-bounds counts as empty, a BFS/DFS neighbor test of `isEmpty(r, c)` alone happily walks off the board. Lead with [isValid]({{< ref "is_valid" >}}): `isValid(r, c) && isEmpty(r, c)` — the pattern the built-in [reach]({{< ref "reach" >}}) and [path]({{< ref "path" >}}) queries follow.
{{< /callout >}}

## Syntax

> `isEmpty(row, col)`

## Parameters

| Param | Description                                                                       |
|-------|-----------------------------------------------------------------------------------|
| `row` | Number: row index of the cell to be read `∈` [[0..height]]({{< ref "height" >}})  |
| `col` | Number: column index of the cell to be read `∈` [[0..width]]({{< ref "width" >}}) |

{{< callout type="info" >}}
Also available as the static method `Quadrille.isEmpty(value)`, which takes a `value` instead of a cell position.
{{< /callout >}}