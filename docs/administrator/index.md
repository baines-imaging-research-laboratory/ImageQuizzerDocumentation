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
	
	What happens is that when the Begin button is clicked to start a session,
	the Image Quizzer checks the user's results folder to see if there is an existing results quiz.
	If there is, it assumes the user is going to resume the quiz and it opens this pre-existing file.
	
	
## Live run

When you have finished creating your script, ensure there are no pre-existing results quiz files
in the user's results folder. You want the user to start with an empty results folder.