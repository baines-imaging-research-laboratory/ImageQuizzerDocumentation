---
hide:
- toc
---
# Descriptor

## Specs

| || Details |
|---|---|:---:|
| **Name** | Descriptor ||
| **Classification** | attribute ||
| **Parent** | <[Page](index.md)\> ||
| **Required** | no ||
| **Syntax** | Descriptor="*string*" | character string |
| **Restrictions**  |  special characters not allowed | "'#&{}\\<>*?/$!:@+`~%^()+=,`|
| **Associations** | [ID](id.md) | folder name |


## Description
Descriptor is not a required attribute for the Page element. It is used in combination with the ID attribute (required)
to identify the Page element.

The ID_Descriptor string combination appears in the quiz progress bar.
It is also used as part of the subfolder names (prefixed by the PageGroup number) 
 created in the User's results folder when capturing
contours and measurement lines that the user creates during the quiz.