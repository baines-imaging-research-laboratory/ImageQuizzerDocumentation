---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# DisplayLabelMapID

## Specs

| ||Details|
|---|---|---|
| **Name** | DisplayLabelMapID ||
| **Classification** | attribute ||
| **Parent** | <[Image](index.md)\> ||
| **Required** | no ||
| **Syntax** | DisplayLabelMapID="*string*" | |
| **Associations** | |  |
|  | [Path](path.md)| path for image on this page must match image path on previous page |
|  | [LabelMapID](labelmap_id.md)| set on image of a previous page |
|  | [PageGroup](../page/pagegroup.md) | |
|  | [RandomizePageGroups](../session/randomize_page_groups.md) | |




## Description

This attribute (along with other associated attributes) provides a means to have the user's contour
from a specific image created from a previous page redisplayed on the same image on the current page. 
This can be useful for comparing the user's contour with a gold standard.

When an image has the DisplayLabelMapID set, the module will search the history of all previous pages
until it finds an image with the following two conditions:

- LabelMapID attribute on the image from the previous page matches the DisplayLabelMapID of the current image
- Path element for the image from the previous and current page match (i.e. the same image is being displayed)

If more than one image element is set up for this image path - differing orientations, 
this attribute needs to be set up on each instance.

If the pages of the study are to be randomized using the Session attribute *RandomizePageGroups* to "Y",
then the PageGroup attribute on the page for the images with *LabelMapID* and the *DisplayLabelMapID* page must be the same.


## Example

See [Redisplay contours](../../examples/example_redisplay_contours.md) example.

