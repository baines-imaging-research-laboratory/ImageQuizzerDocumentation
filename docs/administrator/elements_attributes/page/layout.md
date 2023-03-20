---
hide:
- toc
---
# Layout

## Specs

| |  | Details|
|---| ---|---|
| **Name** | Layout ||
| **Classification** | attribute ||
| **Parent** | <[Page](index.md)\> ||
| **Required** | no ||
| **Syntax** | Layout="*option*" ||
| **Options** | FourUp |(default) Red Green Yellow windows with 3D window in upper right|
|             | TwoOverTwo | Red Green Yellow and Slice4 windows|
|             | OneUpRedSlice | Red window only|
|             | SideBySideRedYellow | Red Yellow windows (matches Slicer's SideBySide configuration)|


## Description
The Layout attribute defines the layout configuration to use for image display. These follow the standard layouts
provided by Slicer.

Depending on the layout chosen, set the [DefaultDestination](../image/default_destination.md) element to
one of the associated viewing window names as described above in Options.



## Examples

See [Layout Examples](../../examples/example_layouts.md#script-examples)