---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# ROIVisibilityCode

## Specs

| ||Details|
|---|---|---|
| **Name** | ROIVisibiltyCode ||
| **Classification** | attribute ||
| **Parent** | <[ROIs](index.md)\> ||
| **Required** | y | when the ROIs element is defined|
| **Syntax** |ROIVisibiltyCode="*option*" | |
| **Options** | All | display all ROIs stored in the file |
| | None | do not display any of the stored ROIs |
| | Select | display only the ROIs that have a name matching the string stored in the [ROI](roi.md) subelements |
| | Ignore | display all ROIs stored in the file except for the ones that have a name matching the string stored in the [ROI](roi.md) subelements |

## Description

The setting of the ROIVisibilityCode determines how to display the ROIs stored in the RTStruct or Segmentation volume.
If this attribute is set to All, then all ROIs stored in the file are displayed. Similarly, if set to None, there won't be any displayed.

If this attribte is set to Select, then [ROI](roi.md) subelements must be defined holding the names of the ROIs to be displayed.
If set to Ignore, then [ROI](roi.md) subelements must be defined holding the names of the ROIs **NOT** to be displayed.
The Select and Ignore codes can be useful if there are a large number of ROIs stored in the file.


## Example

See [ROI visibility example](../../../examples/example_roi_visibility.md)