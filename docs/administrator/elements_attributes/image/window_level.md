---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# WindowLevel

## Specs

| ||Details|
|---|---|:---:|
| **Name** | WindowLevel ||
| **Classification** | attribute ||
| **Parent** | <[Image](index.md)\> ||
| **Required** | no ||
| **Syntax** | WindowLevel="*integer values*" | two values are separated by space |
|| | example: WindowLevel="400 50"|

## Description

The WindowLevel attribute will automatically adjust the window and level settings for the initial load of the image.
Any adjustments to the window/level settings by the user are stored in the ImageState element and are used going forward.

This is especially useful when loading images in a format other than DICOM.


## Example

See example script [Zoom Pan and Slice offset](../../examples/example_zoom_pan_sliceoffset.md)