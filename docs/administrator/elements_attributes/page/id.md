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


See also:  [Page](index.md), [Descriptor](descriptor.md)

## Description
ID is a required attribute for the Page element. It is used in combination with the Image ID attribute (required)
to create a unique node name when loading the image into Slicer.

The Page ID_Descriptor string combination appears as an identifier in the Slicer layout
when displaying the images. It is also used as part of the subfolder names (prefixed by the PageGroup number) 
 created in the User's results folder when capturing
contours and measurement lines that the user creates during the quiz. 
