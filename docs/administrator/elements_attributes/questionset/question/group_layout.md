---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# GroupLayout

## Specs

| ||Details|
|---|---|:---:|
| **Name** | GroupLayout ||
| **Classification** | attribute ||
| **Parent** | <[Question](index.md)\> ||
| **Required** | no ||
| **Syntax** | GroupLayout="*string*" |  |
| **Options** | Vertical |(default) present options in a box vertically |
|             | Horizontal |present options in a box horizontally|
| **Restrictions** | | only for question types: Radio, CheckBox and Picture |

## Description

The GroupLayout attribute gives you the ability to line up your options in a question box either vertically or horizontally.
This attribute is only active for question types: Radio, CheckBox and Picture. If the attribute is missing,
the question defaults to a vertical layout.

## Example

See [Question Types](../../../examples/example_question_type.md) for examples.

See also [Type Options > RadioButton](type.md#radio)