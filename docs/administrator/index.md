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

## Building your script

!!! warning

    When building your quiz, the administrator creates and makes changes to the original XML file.
    This is known throughout the documentation as the *master* quiz file.
    When the user starts a quiz session, a copy of this *master* quiz file, with the same name is placed in the user's results folder
    ready to record the session responses. This is known throughout the documentation as the *results* quiz file.

    After your initial run of the quiz, if you edit the master quiz XML file,
	**you must delete the copy of the quiz in the user's results folder** before your next run.
	Otherwise, your changes will not be recognized on the next run.


!!! tip
    Notepad++ has a plugin for XML tools that can be downloaded to help check syntax as you build your quiz.
    This can be used in conjuction with the *ImageQuizzer.xsd* schema file found in the Resources\XML folder.
    The schema file is set up to do some immediate validation as you build your script.
	
