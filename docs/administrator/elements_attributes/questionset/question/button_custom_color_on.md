---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# ButtonCustomColorOn

## Specs

| ||Details|
|---|---|:---:|
| **Name** | ButtonCustomColorOn ||
| **Classification** | attribute ||
| **Parent** | <[Question](index.md)\> ||
| **Required** | no ||
| **Syntax** | ButtonCustomColorOn="*list of integer rbg values*" | 3 values separated by spaces |
| **Dependancy** | Question Type attribute | only applies to Type="Button"|

## Description

This attribute can be set on a **Button** type of question in order to customize the color of the button presented on the screen.

It accepts 3 integer values representing the RGB values of the color. If this attribute is missing, the default RGB color is used.
If there are multiple Option elements within this Question creating multiple buttons, this color is applied to all.


## Example

See [Button type](type.md#button)




See also [Question Types](../../../examples/example_question_type.md) for more examples.
