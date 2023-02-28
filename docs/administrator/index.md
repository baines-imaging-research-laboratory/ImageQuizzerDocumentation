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

!!! tip
    Notepad++ has a plugin for XML tools that can be downloaded to help check syntax as you build your quiz.
    This can be used in conjuction with the *ImageQuizzer.xsd* schema file found in the Resources\XML folder.
	

Setting up the quiz XML is best done using a trial and error approach starting with the basic elements.
Once the basic building blocks are in place, add in more features.

It is recommended to only set up one full page to start. See how it looks and behaves
when the Image Quizzer module is active.
Then copy/paste the Page with ID, descriptor, image path adjustments to make the pages unique.



!!! Note
    When building your quiz, the administrator creates and makes changes to the original XML file.
    This is known throughout the documentation as the *master* quiz file.
    When the user starts a quiz session, a copy of this *master* quiz file, with the same name is placed in the User's folder
    ready to record the session responses. This is known throughout the documentation as the *results* quiz file


