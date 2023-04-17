---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# Layer

## Specs

| ||Details|
|---|---|:---:|
| **Name** | Layer ||
| **Classification** | element ||
| **Parent** | <[Image](index.md)\> ||
| **Required** | no ||
| **Syntax** | <Layer\>*option*</Layer\> |  |
| **Options** | Background | (default) load image on background layer|
|             | Foreground |load image on foreground layer |
|             | Label |load label map mask on label layer |
|             | Segmentation |load segmentation images on segmentation layer |

## Description

This element defines where to place the image being loaded.
Background is the default layer. If you want to load two images in one viewing window,
create 2 image elements, one for each image and assign the layer for one as "Background" and the other as "Foreground".
See [layering](../../examples/example_layering.md) example.

The Label layer is best assigned to images that contain a mask representing a region of interest (ROI).
The Segmentation layer can be used to load images that contain multiple segments for the same ROI.
For the Label and Segmentation layers, you have the ability to identify which ROIs to display or ignore.

See also:

- [ROIs](rois/index.md) element description.
- [ROIVisibiltyCode](rois/roi_visibility_code.md) attribute description.
- [ROI](rois/roi.md) element description.
