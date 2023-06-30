---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# ZoomFactor

## Specs

| ||Details|
|---|---|:---:|
| **Name** | ZoomFactor ||
| **Classification** | attribute ||
| **Parent** | <[Image](index.md)\> ||
| **Required** | no ||
| **Syntax** | ZoomFactor="*value*" | decimal value for zoom percentage  |
| | | default value is 1 |
| **Dependencies**| [Layer](layer.md) | must be "Background"|

## Description

The ZoomFactor adjusts the displayed image's field of view, representing a percentage relative to the original image view upon loading. 
A value less than one will zoom out (e.g. a value of 0.5 decreases the image field of view by 50%) 
and greater than one the display will zoom in (e.g. a value of 1.5 will increase the image field of view by 50%). The default value is 1 (no zoom).

This attribute is only effective on a background layer.
If there is an image loaded into the foreground, the zoom factor is automatically applied to it.

This can be used in conjunction with the PanOrigin and InitialSliceOffset attributes to have the
initial view of the image focused on a specific region of interest.


## Example

See example script [Zoom Pan and Slice offset](../../examples/example_zoom_pan_sliceoffset.md)