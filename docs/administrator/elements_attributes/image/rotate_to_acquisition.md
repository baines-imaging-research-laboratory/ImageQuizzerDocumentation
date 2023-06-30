---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# RotateToAcquisition

## Specs

| ||Details|
|---|---|---|
| **Name** | RotateToAcquisition ||
| **Classification** | attribute ||
| **Parent** | <[Image](index.md)\> ||
| **Required** | no ||
| **Syntax** | RotateToAcquisition="*option*" |  |
| **Options** | Y | image is loaded in the acquisition frame of reference|
|             | N |(default) image is loaded in world coordinates frame of reference |


## Description

The RotateToAcquisition attribute, if set to yes, will automatically display the image 
in the frame of reference in which the volume was acquired in the scanner.
Otherwise, the image will be displayed according to the anatomical planes (Axial, Sagittal, Coronal).

## Example

See [example - rotate to acquisition](../../examples/example_rotating.md)