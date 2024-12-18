---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# ButtonToggleColorOff

## Specs

| ||Details|
|---|---|:---:|
| **Name** | ButtonToggleColorOff ||
| **Classification** | attribute ||
| **Parent** | <[Question](index.md)\> ||
| **Required** | no ||
| **Syntax** | ButtonToggleColorOff="*list of integer rbg values*" | 3 values separated by spaces |
| **Dependancy** | Question Type attribute | only applies to Type="Button"|

## Description

This attribute can be set on a **Button** type of question. If set, it puts the button into a **Toggle** mode 
and the RGB color defined is applied after clicking the button. It can be used in conjunction with the *ButtonCustomColorOn*
attribute to define an on/off color combination.

The functionality of a toggle button differs from that of a standard button in that it can be 
clicked multiple times or left unclicked entirely. Regardless of how many times the button is 
pressed—or if it is not pressed at all—it does not affect the user's ability to proceed to the next page.
For a standard button, the button must have been pressed at least once in order to proceed.


This attribute is defined with 3 integers representing the rgb values of the color. If this attribute is missing, the default rgb color is used when the button is clicked
and the button is treated as a standard type that requires the user to click it at least once before proceeding to the next page.
If there are multiple Option elements within this Question creating multiple buttons, this color is applied to all.


## Example

See [Button type](type.md#button)




See also [Question Types](../../../examples/example_question_type.md) for more examples.
