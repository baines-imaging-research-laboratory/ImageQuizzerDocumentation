---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# InitialSliceOffset

## Specs

| ||Details|
|---|---|---|
| **Name** | InitialSliceOffset ||
| **Classification** | attribute ||
| **Parent** | <[Image](index.md)\> ||
| **Required** | no ||
| **Syntax** | InitialSliceOffset="*decimal value*" | represents the slice in mm |
| **Dependencies**| [Layer](layer.md)  | must be "Background" |

## Description

When this attribute is assigned to an Image element, the module will display the image
when initially loaded at the slice position closest to the assigned value.

This can be used in conjunction with [ZoomFactor](zoom_factor.md) and [PanOrigin](pan_origin.md) attributes
to direct the user's attention to an area of interest on initial load.

## Example

See example script [Zoom Pan and Slice offset](../../examples/example_zoom_pan_sliceoffset.md)
