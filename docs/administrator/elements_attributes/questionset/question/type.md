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
|             | Picture | to display a picture type file (eg. .png or .jpg)|

## Description

The Type attribute for a Question element defines how the quiz display will present each Option element defined in the Question.
It is a required attribute.

!!! Note "Button"
    The Button type of question will execute an external script. The Option element holds the filename
	of the script located in the .../ImageQuizzer/Inputs/Scripts directory.
	If the script fails, the button will turn a light red color and a warning message appears 
	for the user to contact the administrator.
	
	This script can access elements of the Slicer application by importing the 'slicer' class.
	
	
!!! Note "Picture"
	The Picture question type enables the display of an image file (such as .png or .jpg) in the quiz.
	The Option element holds the filename for the picture file located in the .../ImageQuizzer/Inputs/MasterQuiz directory
	along with the XML master quiz file.

## Example

See [Question type](../../../examples/example_question_type.md) examples.
