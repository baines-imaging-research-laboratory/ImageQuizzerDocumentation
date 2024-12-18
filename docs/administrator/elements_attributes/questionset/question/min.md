---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# Min

## Specs

| ||Details|
|---|---|:---:|
| **Name** | Min ||
| **Classification** | attribute ||
| **Parent** | <[Question](index.md)\> ||
| **Required** | no ||
| **Syntax** | Min="*value*" | numeric input in quotes |
| **Dependancy** | Question Type attribute | must be set to "IntegerValue" or "FloatValue" |

## Description

The Min attribute for a Question is only valid when the Type attribute for the Question is an integer of float (decimal) value.
The Min attribute is not required. It also does not have to be paired with a Max attribute for this Question.
It will define the lower boundary allowed for the numeric input.

## Example

See [Question Types](../../../examples/example_question_type.md) for examples.
