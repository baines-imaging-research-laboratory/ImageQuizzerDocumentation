---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# ROIs

## Specs

| ||Details|
|---|---|---|
| **Name** | ROIs ||
| **Classification** | element ||
| **Parent** | <[Image](index.md)\> ||
| **Required** | *y/n | *see Dependencies|
| **Syntax** | <ROIs\>...</ROIs\>| |
| **Dependencies** | <[Type](../type.md)\> | ROIs element is required when image Type is set as Segmentation or RTStruct |

## Description

The ROIs element is required if the image is defined as a Segmentation or RTStruct Type. 
Also required is its [ROIVisibilityCode](roi_visibility_code.md) attribute. This gives the administrator the flexibility
to define which regions of interest are to be displayed.


## Example

See [ROI visibility example](../../../examples/example_roi_visibility.md)