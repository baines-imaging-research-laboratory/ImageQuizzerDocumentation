---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# DefaultDestination

## Specs

| ||Details|
|---|---|---|
| **Name** | DefaultDestination ||
| **Classification** | element ||
| **Parent** | <[Image](index.md)\> ||
| **Required** | no ||
| **Syntax** | DefaultDestination="*option*" | |
| **Options** | Red | (default)|
|             | Green | |
|             | Yellow | |
|             | Slice4 | |

## Description

This element defines in which viewing window to place the image.
The Red viewing window is the default window used if this element is missing.

The DefaultDestination element differs from the Destination attribute found in the State element.
DefaultDestination defines the original destination that the image is presented.
The State element attribute Destination captures the destination of the image at the time of response capture. 
This could differ from the original if the observer changed how to view the image (for example, using the 
[Extra Tools viewing display options](../../../user/extratools.md#viewing-display-options))


## Example

For examples on using the DefaultDestination element, see
[Layout Examples](../../examples/example_layouts.md#script-examples). 
