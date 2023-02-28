---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# SegmentRequiredOnAnyImage

## Specs

| ||Details|
|---|---|:---:|
| **Name** | SegmentRequiredOnAnyImage ||
| **Classification** | attribute ||
| **Parent** | <[Page](index.md)\> ||
| **Required** | no ||
| **Syntax** | SegmentRequiredOnAnyImage="*option*" |  |
| **Options** | Y | user must create a contour on any loaded image|
|             | N |(default) no contour is required|
| **Dependencies**| [EnableSegmentEditor](enable_segment_editor.md) | must be set to "Y" |

## Description

If this attribute is set to "Y", the user must create a contour on any of the loaded images
using the segment editor. The attribute [EnableSegmentEditor](enable_segment_editor.md) must also be set to "Y".
The user will not be allowed to proceed to the next Page until a contour has been created.