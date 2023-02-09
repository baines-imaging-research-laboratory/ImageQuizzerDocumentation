# Build a quiz

The Image Quizzer is controlled by a script that is written using eXtensible Markup Language (XML) formatting. 
This script defines what images and questions are to be displayed and in what order. 
It can be created using a simple editor like Notepad.

!!! tip
    Notepad++ has a plugin for XML tools that can be downloaded to help check syntax as you build your quiz.
    This can be used in conjuction with the *ImageQuizzer.xsd* schema file found in the Resources\XML folder.
	
!!! Note
    When building your quiz, the administrator creates and makes changes to the original XML file.
    This is known throughout the documentation as the *master* quiz file.
    When the user starts a quiz session, a copy of this *master* quiz file, with the same name is placed in the User's folder
    ready to record the session responses. This is known throughout the documentation as the *Results* quiz file

## Simple quiz example

Here is a screenshot of a very simple quiz followed by the script that was used to create it.

![Simple Script Screenshot](assets/build/SimpleScript_Screenshot.png)


Script for the Simple Quiz example.

SimpleScript.xml
```
<Session>
	<Page ID="Patient 1">
		<Image ID="CT" Type="Volume">
				<DefaultDestination>Red</DefaultDestination>
				<Layer>Background</Layer>
				<DefaultOrientation>Axial</DefaultOrientation>
				<Path>ImageVolumes\CTChest\CTChest.nrrd</Path>
		</Image>
		<QuestionSet>
			<Question Type="CheckBox">
				<Option>Learning Tool</Option>
				<Option>Observer Study</Option>
			</Question>
		</QuestionSet>
	</Page>
</Session>
```

## Simple quiz elements and layout

Following describes the basic elements of the above script and the screen layout. 
See details for each element and their attributes in the [Elements and attributes](elements_attributes/index.md)
section of this documentation.

| Element | Description |
| ------- | ----------- |
| [Session](elements_attributes/session/index.md) | The root of the script containing all elements of the quiz. |
| [Page](elements_attributes/page/index.md)    | What appears in the 3D Slicer layout. This includes the images on the right side and the quiz on the left side. |
| Image | An element that defines specifics of the image to display
|QuestionSet | An element that contains a group of questions.|
| Question | An element that contains a group of options and specifics on how they are displayed. |
| Option     | An individual item that forms part of the question. |



![Simple Script Layout](assets/build/SimpleScript_Layout.png)


## Expanding your quiz

There are many XML elements and attributes available to customize your quiz.
Refer to the [Elements and attributes](elements_attributes/index.md) section for details.

!!! tip
    When working on quizzes that have a specific set of questions to be asked for numerous images,
	start the build process using the basic required elements for one Page. 
	Test this in Slicer to make sure it displays what you want.
	Then you can copy/paste the pages, update the Image Path element and the ID & Description attributes.


## Testing your quiz

When you are building your quiz, the general pattern is:

    - modify/create the XML quiz file (aka __master__ quiz)
    - run ImageQuizzer for modified quiz (Image Quizzer creates a copy of the master quiz in the user folder to capture responses.)
    - make additional modifications to master quiz
    - **remove quiz folder under the Users folder**
    - run ImageQuizzer again on modified master

!!! Note
	If you don't remove the results quiz folder under the User's folder, Image Quizzer will
	assume the user is resuming the quiz that was already started. It reads the copied
	quiz and your new modifications made to the master quiz will not be reflected.