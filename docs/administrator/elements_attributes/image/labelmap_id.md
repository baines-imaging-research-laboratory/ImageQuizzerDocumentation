---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# LabelMapID

## Specs

| ||Details|
|---|---|---|
| **Name** | LabelMapID ||
| **Classification** | attribute ||
| **Parent** | <[Image](index.md)\> ||
| **Required** | no ||
| **Syntax** | LabelMapID="*string*" | |
| **Associations** | |  |
|  | [EnableSegmentEditor](../page/enable_segment_editor.md)| enable segmentation tab |
|  | [SegmentRequired](segment_required.md)| user must create a contour for this image |
|  | [Path](path.md)| path for image on this page must match image path on subsequent page |
|  | [DisplayLabelMapID](display_labelmap_id.md)| set on image of subsequent page |
|  | [PageGroup](../page/pagegroup.md) | |
|  | [RandomizePageGroups](../session/randomize_page_groups.md) | |




## Description

This attribute (along with other associated attributes) provides a means to have the user create a contour
on a specific image and have this contour redisplayed on the same image in a subsequent page.
This can be useful for comparing the user's contour with a gold standard.

If a subsequent page has an image element with the DisplayLabelMapID attribute set to match 
this LabelMapID, and the Path elements for both the current image and the subsequent image match, then the label map created
here will be redisplayed on the subsequent page.

If more than one image element is set up for this image path - differing orientations, 
this attribute only needs to be set up on one instance.

If the pages of the study are to be randomized using the Session attribute *RandomizePageGroups* to "Y",
then the PageGroup attribute on the page for the images with *LabelMapID* and the *DisplayLabelMapID* page must be the same.

## Example

See [Redisplay contours](../../examples/example_redisplay_contours.md) example.