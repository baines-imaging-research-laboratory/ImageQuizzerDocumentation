---
hide:
- toc
---
# Type

## Specs

| ||Details|
|---|---|---|
| **Name** | Type ||
| **Classification** | attribute ||
| **Parent** | <[Question](index.md)\> ||
| **Required** | yes ||
| **Syntax** | Type="*option*" |  |
| **Options** | Radio |one radio button for each Option element|
|             | CheckBox |one checkbox for each Option element|
|             | Text |text box displayed for character intput |
|             | InfoBox |text defined in Option element displayed in one line |
|             | IntegerValue |box that accepts an integer value |
|             | FloatValue |box that accepts an decimal value |
|             | Button | button that will run external script defined in the Option element|

## Description

The Type attribute for a Question element defines how the quiz display will present each Option element defined in the Question.
It is a required attribute.

!!! Note "Button"
    The Button type of question will execute an external script. The location of the script is defined 
	in the Option element of the question as a path relative to the
	directory that holds the data for the Image Quizzer defined at login time.
	This script can access elements of the Slicer application by importing the 'slicer' class.
	
	If the script fails, the button will turn a light red color and a warning message appears 
	for the user to contact the administrator.
	


## Example

See [Question type](../../../examples/example_question_type.md) examples.
