---
weight: 8
title: "isImage(row, col)"
---

Returns `true` if the cell at `(row, col)` contains a valid image-related type such as an [image](https://p5js.org/reference/#/p5.Image), [graphics](https://p5js.org/reference/#/p5.Graphics), or [framebuffer](https://p5js.org/reference/#/p5.Framebuffer), or if it is a [video](https://p5js.org/reference/#/p5.MediaElement) element, and `false` otherwise.

## Syntax

> `isImage(row, col)`

## Parameters

| Param | Description                                                                       |
|-------|-----------------------------------------------------------------------------------|
| `row` | Number: row index of the cell to be read `∈` [[0..height]]({{< ref "height" >}})  |
| `col` | Number: column index of the cell to be read `∈` [[0..width]]({{< ref "width" >}}) |

{{< callout type="info" >}}
Also available as the static method `Quadrille.isImage(value)`, which takes a `value` instead of a cell position.
{{< /callout >}}