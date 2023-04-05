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
| **Dependencies**| [Layer](layer.md)  | must be "Background" or "Foreground" |

## Description

When this attribute is assigned to an Image element, the module will display the image
when initially loaded at the slice whose position is closest to the assigned value.

This is useful when you need to direct the user's attention to an area of interest on initial load.
