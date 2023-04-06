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
|  | [EnableSegmentEditor](../page/enable_segment_editor.md)| enable segmentation tab |
|  | [SegmentRequired](segment_required.md)| user must create a contour for this image |
|  | [Path](path.md)| path for image on this page must match image path on subsequent page |
|  | [LabelMapID](labelmap_id.md)| set on image of a previous page |




## Description

This attribute (along with other associated attributes) provides a means to have the user's contour
from a specific image on a previous page redisplayed on the image in this page. The LabelMapID from a 
previous page must match the DisplayLabelMapID string and the Path element for the image on this page and
the Path for the image on the previous page must match.

This can be useful for comparing the user's contour with a gold standard.


