---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# Building basics

The **master** quiz XML file can be created using a simple editor such as Notepad.
This is where you enter XML elements and attributes that will define how the quiz
images and associated questions are displayed.

This section presents a simple script example with a desciption of the resulting layout.
It also provides tips on the development process for building and testing your script. 

Specifics for each element and attribute can be found in the 
[Scripting references](../elements_attributes/index.md) section.



!!! tip
    Notepad++ has a plugin for XML tools that can be downloaded to help check syntax as you build your quiz.
    This can be used in conjuction with the *ImageQuizzer.xsd* schema file found in the ImageQuizzer/Inputs/MasterQuiz folder.
    The schema file is set up to do some immediate validation as you build your script.

!!! warning
    Note the [Warning](../index.md) for building and testing your script.
    (It could save you time and headaches.)


## Prep

Download and save Slicer's CTChest dataset as described in the [sample data suggested tree structure](sample_data.md#suggested-tree-structure) section.

```
.
└─ ImageDatabase/
    └─ ImageVolumes/
        └─ CTChest/
            └─ CTChest.nrrd
			   
```

## Simple quiz example

Here is a screenshot of a very simple quiz followed by the script that was used to create it.

![Simple Script Screenshot](../assets/build/SimpleScript_Screenshot.png)


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


## Script elements layout


![Simple Script Layout](../assets/build/SimpleScript_Layout.png)



## Expanding your quiz

There are many XML elements and attributes available to customize your quiz.
Some of these are shown in the Quiz examples section. You can also
refer to the [Scripting references](../elements_attributes/index.md) section for a complete list of features.

!!! tip
    When working on quizzes that have a specific set of questions to be asked for numerous sets of images,
	start the build process using the basic required elements for one page. 
	Test this in Slicer to make sure it displays what you want.
	Then you can copy/paste the pages, update the image Path element and the ID & 
	Description attributes to make each page unique.

## Testing your quiz

When you are building your quiz, the general editing pattern is:

1. create the XML master quiz file
1. run ImageQuizzer to test your script
1. make additional modifications to master quiz
1. **remove quiz folder under the Users folder** (see tree structure below for location)
1. rerun ImageQuizzer on modified master

```
User's folder found here:
.
└─ ImageQuizzer/
	  └─ Outputs/
	      └─ UsersResults
              └─ username
                  └─ copy_of_master_quiz_for_responses.xml
	
```

!!! Note
    During your test, when the Begin button is pressed, the Image Quizzer creates a copy
	of the master quiz in the user folder (the results quiz) to capture responses.
	If you make changes but don't remove this results quiz folder between tests, Image Quizzer will
	assume the user is resuming the quiz that was already started. It reads the existing results
	quiz file and the new modifications made to the master quiz will not be reflected.
	
	See also [Building your script \> Warning](../index.md#bulding-and-testing-your-script)

## Quiz Validation

As you build your quiz, it is advisable to do a trial run. Start the quiz by selecting **Begin**
within the Login window. The quiz undergoes validation based on various criteria.
If any criteria are unmet, the validator will present
a message box with the issues that were encountered. Once the issues are resolved, the quiz will 
begin. This was set up to prevent errors during live sessions for the user.

