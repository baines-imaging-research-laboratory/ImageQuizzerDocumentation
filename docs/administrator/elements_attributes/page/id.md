---
hide:
- toc
---
# ID

## Specs

| || Details |
|---|---|:---:|
| **Name** | ID ||
| **Classification** | attribute ||
| **Parent** | <[Page](index.md)\> ||
| **Required** | yes ||
| **Syntax** | ID="*string*" | character string |
| **Restrictions**  |  special characters not allowed | "'#&{}\\<>*?/$!:@+`~%^()+=,`|
| **Associations** | [Image ID](../image/id.md) | uniqueness validation |
||[Path](../image/path.md) | uniqueness validation |
|| [Descriptor](descriptor.md) | folder name |


## Description
ID is a required attribute for the Page element. It is used in combination with the Image ID attribute (also required)
to create a unique node name when loading the image into Slicer.

The PageID_Descriptor string combination appears in the quiz progress bar.
It is also used as part of the subfolder names (prefixed by the PageGroup number) 
 created in the User's results folder when capturing
contours and measurement lines that the user creates during the quiz.

!!!Warning "Uniqueness"

	The ID attribute for the Image is combined with the ID attribute
	of the Page to create a unique node name when loaded into Slicer. 
	There can be multiple Image elements within a Page with the same Path (e.g., one image
	loaded into different viewing windows). Each of these elements must
	have the same Image ID attribute. This is checked during quiz validation.
