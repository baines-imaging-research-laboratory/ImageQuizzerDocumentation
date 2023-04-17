---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# ROI

## Specs

| ||Details|
|---|---|---|
| **Name** | ROI ||
| **Classification** | element ||
| **Parent** | <[ROIs](index.md)\> ||
| **Required** | *y/n | *see Dependencies|
| **Syntax** | <ROI\>string</ROI\>| name of ROI to display or ignore based on [ROIVisibilityCode](roi_visibility_code.md)|
| **Dependencies** | ROIVisibilityCode | an ROI name is required if the ROIVisibilityCode = 'Select' or 'Ignore' |
|  |  | this element is not required if the ROIVisibilityCode = 'All' or 'None' |

## Description

If the ROIVisibilityCode is set to Select or Ignore, there should be an ROI element for each region of interest
to display or ignore respectively. The string holds the name of the ROI which must match the name stored in 
the file exactly.

## Example

See [ROI visibility example](../../../examples/example_roi_visibility.md)