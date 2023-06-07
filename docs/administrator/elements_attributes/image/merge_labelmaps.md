---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# MergeLabelMaps

## Specs

| ||Details|
|---|---|---|
| **Name** | MergeLabelMaps ||
| **Classification** | attribute ||
| **Parent** | <[Image](index.md)\> ||
| **Required** | no ||
| **Syntax** | MergeLabelMaps="*option*" |  |
| **Options** | Y | previous label maps are merged into one file and displayed|
|             | N |(default) no merged label maps are created|
| **Dependencies**| For current page/image elements |DisplayLabelMapID - exists|
|||SegmentEditor - off|
||| Path for image matches image on historical page |
|||PageGroup - number matches that of historical element|
|| For historical page/image elements| PageGroup number match to current page |
||| LabelMapID - matches DisplayLabelMapID |
||| Path for image matches image on current page |
|||Loop='Y'|
||| Page ID and Descriptor match for all repetitions (ignoring 'Rep##')


## Description

The MergeLabelMaps attribute works in association with the page Loop attribute. 
This is useful when you want the user to answer quiz questions for each ROI seen on an image
and then have all the ROI's for that image displayed on a subsequent page.

This is accomplished first of all with the [Loop](../page/loop.md) page attribute set to 'Y' and [LabelMapID](labelmap_id.md) defined for the image.
Then on a subsequent page for the same image, add the attributes [MergeLabelMaps](.) and [DisplayLabelMapID](display_labelmap_id.md).
The 'DisplayLabelMapID' on the current page must match the 'LabelMapID' on the historical page.
Also, the image paths for the current and historical elements must match.

The EnableSegmentEditor for the current page must be off.

## Example

See [example - rotate to acquisition](../../examples/example_rotating.md)