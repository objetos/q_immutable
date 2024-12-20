---
weight: 4
title: "isEmpty(row, col)"
---

Returns `true` if the cell found at `(row, col)` is empty and `false` otherwise. Only cells defined as `null` are considered empty.

## Example

The `isEmpty()` method is exemplified in [visitQuadrille(quadrille, fx, cells)]({{< ref "visit_quadrille#visitquadrillequadrille-fx-cells" >}}).

## Syntax

> `isEmpty(row, col)`

## Parameters

| param    | description                                                                     |
|----------|---------------------------------------------------------------------------------|
| row      | Number: row number of the cell to be read [\[0..height\]]({{< ref "height" >}}) |
| col      | Number: col number of the cell to be read [\[0..width\]]({{< ref "width" >}})   |
