---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# Max

## Specs

| ||Details|
|---|---|:---:|
| **Name** | Max ||
| **Classification** | attribute ||
| **Parent** | <[Question](index.md)\> ||
| **Required** | no ||
| **Syntax** | Max="*value*" | numeric input in quotes |
| **Dependencies** | Question Type attribute | must be set to "IntegerValue" or "FloatValue" |

## Description

The Max attribute for a Question is only valid when the Type attribute for the Question is an integer of float (decimal) value.
The Max attribute is not required. It also does not have to be paired with a Min attribute for this Question.
It will define the upper boundary allowed for the numeric input.

## Example

See [Question Types](../../../examples/example_question_type.md) for examples.