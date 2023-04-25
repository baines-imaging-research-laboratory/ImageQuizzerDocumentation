---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# Building basics

This section presents a simple script with a desciption of the resulting layout.
It also provides tips on the development process for building and testing your script. 

!!! tip
    Notepad++ has a plugin for XML tools that can be downloaded to help check syntax as you build your quiz.
    This can be used in conjuction with the *ImageQuizzer.xsd* schema file found in the Resources/XML folder.
    The schema file is set up to do some immediate validation as you build your script.


## Prep

Download and save Slicer's CTChest dataset as described in the [sample data](sample_data.md#slicer-sample-datasets) section.

Suggested folder structure to match script:
```
.
└─ ImageQuizzerData/
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
refer to the [Scripting references](../elements_attributes/index.md) section for more details.

!!! tip
    When working on quizzes that have a specific set of questions to be asked for numerous sets of images,
	start the build process using the basic required elements for one page. 
	Test this in Slicer to make sure it displays what you want.
	Then you can copy/paste the pages, update the image Path element and the ID & 
	Description attributes to make each page unique.

## Testing your quiz

When you are building your quiz, the general pattern is:

1. create the XML quiz file (aka __master__ quiz)
1. run ImageQuizzer to test your script
1. make additional modifications to master quiz
1. **remove quiz folder under the Users folder** (see tree structure below for location)
1. rerun ImageQuizzer on modified master

```
User's folder found here:
.
└─ ImageQuizzerData/
    │ └─ ImageVolumes/
    │     ├─ CTChest/
    │     │     └─ CTChest.nrrd
    │     ... etc.
    └─ Users/
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
