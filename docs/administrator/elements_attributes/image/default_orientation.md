---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# DefaultOrientation

## Specs

| ||Details|
|---|---|---|
| **Name** | DefaultOrientation ||
| **Classification** | element ||
| **Parent** | <[Image](index.md)\> ||
| **Required** | no ||
| **Syntax** | <DefaultOrientation\>*option*</DefaultOrientation\> | |
| **Options** | Axial | (default)|
|             | Sagittal | |
|             | Coronal | |

## Description

This element defines in which orientation to display the image.
The Axial is the default orientation used if this element is missing.

The DefaultOrientation element differs from the Orientation attribute found in the State element.
DefaultOrientation defines the original orientation that the image is presented.
The State element attribute Orientation captures the orientation of the image at the time of response capture. 
This could differ from the original if the observer changed how to view the image (for example, using the 
[Extra Tools viewing display options](../../../user/extratools.md#viewing-display-options))


## Example

For examples on using the DefaultDestination element, see
[Layout Examples](../../examples/example_layouts.md#script-examples). 
