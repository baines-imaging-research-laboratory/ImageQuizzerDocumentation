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




## Description

This attribute (along with other associated attributes) provides a means to have the user create a contour
on a specific image and have this contour redisplayed on the same image in a subsequent page.
This can be useful for comparing the user's contour with a gold standard.


