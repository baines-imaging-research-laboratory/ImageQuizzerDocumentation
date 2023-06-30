---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# PanOrigin

## Specs

| ||Details|
|---|---|:---:|
| **Name** | PanOrigin ||
| **Classification** | attribute ||
| **Parent** | <[Image](index.md)\> ||
| **Required** | no ||
| **Syntax** | PanOrigin="*list of decimal values*" | values are separated by spaces |
|| | example: PanOrigin="10 20.5 3"|
| **Dependencies**| [Layer](layer.md) | must be "Background" |

## Description

The PanOrigin attribute will move the image to the specified position when loaded.

This attribute is only effective on a background layer.
If there is an image loaded into the foreground, the panning is automatically applied to it.

This can be used in conjunction with the ZoomFactor and InitialSliceOffset attributes to have the
initial view of the image focused on a specific region of interest.


## Example

See example script [Zoom Pan and Slice offset](../../examples/example_zoom_pan_sliceoffset.md)