---
hide:
- toc
---
# Option

## Specs

| |Value|Details|
|---|---|---|
| **Name** | Option |  |
| **Classification** | element ||
| **Parent** | <[Question](../index.md)\> ||
| **Required** | no ||
| **Syntax** | <Option\>string</Option\>| String holds text that is displayed for the question. |
|            |         | For Type='Button', the string is a relative path to an external script. |


## Description

An Option element is a child of a Question. It contains text that is to be displayed in the quiz questions.
(See note for question of type Button)
When observer presses the Next or Previous buttons, the Image Quizzer will capture the response for each Option element
which is recorded in the [results file](../../../results.md#response).

!!! Note "Button"
	For a Button type of question, the text in the Option element represents the relative path to an external script
	that will be run when the user presses the button. The path stored is relative to the directory of the Image Quizzer data
	that was selected by the user at [login time](../../../../user/user.md#login) .


## Example

See [Question Types](../../../examples/example_question_type.md) for examples.
