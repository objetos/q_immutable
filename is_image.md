---
weight: 12
title: "isImage(row, col)"
---

Returns `true` if the cell at `(row, col)` contains a valid image-related type such as an [image](https://p5js.org/reference/#/p5.Image), [graphics](https://p5js.org/reference/#/p5.Graphics), or [framebuffer](https://p5js.org/reference/#/p5.Framebuffer), or if it is a [video](https://p5js.org/reference/#/p5.MediaElement) element, and `false` otherwise.

## Example

The `isImage()` method is exemplified in [read(row, col)]({{< ref "read#example" >}}).

## Syntax

> `isImage(row, col)`

## Parameters

| param    | description                                                                     |
|----------|---------------------------------------------------------------------------------|
| row      | Number: col number of the cell to be read [\[0..height\]]({{< ref "height" >}}) |
| col      | Number: row number of the cell to be read [\[0..width\]]({{< ref "width" >}})   |