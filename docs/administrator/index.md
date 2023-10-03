---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->

# Administrator guide

## Overview

The Image Quizzer is controlled by a script that is written using eXtensible Markup Language (XML) formatting. 
This script defines what images and questions are to be displayed and in what order. 
It can be created using a simple editor like Notepad.

Setting up the quiz XML is best done using a trial and error approach starting with the basic elements.
Once the basic building blocks are in place, you can customize the quiz adding in more features.

## Building and testing your script

See the documentation for [Quiz building basics](examples/build_basics.md) for details on the quiz setup.

!!! warning

    When building your quiz, the administrator creates and makes changes to the original XML file.
    This is known throughout the documentation as the **master** quiz file.
    When a quiz session is first started, a copy of this *master* quiz file, with the same name is placed in the user's results folder
    ready to record the session responses. This is known throughout the documentation as the **results** quiz file.

    After your initial test run of the quiz, if you edit the master quiz XML file,
	**you must delete the copy of the quiz in the user's results folder** before you run your next test.
	Otherwise, your changes will not be implemented.
	
	The process operates in such a way that when the Begin button is pressed to start a session, 
	the Image Quizzer examines the user's results folder to determine the presence of an existing results quiz.
	If one exists, the software assumes the user is going to resume the quiz and opens this pre-existing file
	which will not have your new modifications. If one does not exist, the updated master quiz is duplicated into the 
	user's results folder.
	
	
## Live run

When you have finished creating your script, ensure there are no pre-existing results quiz files
in the user's results folder. You want the user to start with an empty results folder.