---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->

#Release Notes
	Image Quizzer v3.4.0 - July 2024
	

##Requirements

	3D Slicer v4.11.20210226
	SlicerRT extension
	SlicerOpenCV extension
	
##New Features

		- UML diagram
			- added to folder .../ImageQuizzerProject/Documentation

		- Response elements
			- An attribute has been added to the response element describing the event that led to the
			addition of the element.
			
		- Quiz validation
			- quiz is now validated against the xml schema stored in  .../ImageQuizzer/Inputs/MasterQuiz/ImageQuizzer.xsd
		
	
##Modifications

	- v3.4.1
		- QuestionSet elements
			- As a result of the fix to the XMLSchema validation, each Page on the Quiz must have a QuestionSet element.
			There can be multiple QuestionSets and they can be empty (no Question elements). If there are Image elements on the
			Page, the QuestionSet element must follow the Image elements.
			
	- v3.4.0
		- File naming convention
			- Changed suffix for label map and markup line file names from -bainesquizxxx to -quizxxx to allow
			for more room when estimating the length of the saved files during quiz validation to stay under the Windows
			limit of 256 characters.
			
			
##Fixes
	- v3.4.1
		- fix XMLSchema which wasn't validating the quiz during quiz launch the same way that Notepad++ would validate it.
			Notepad++ would allow for a Page with only Image elements and no QuestionSet elements. Validation through the
			code during quiz launch would not allow this. This fix provides consistency between both validators. Now,
			the administrator must always have one or more QuestionSet elements on a Page and it must follow the
			Image elements if there are any. The QuestionSet element can be empty.

	- v3.4.0
		- Workflow fixes
			- code refactored addressing general fixes as user moves between pages especially for Previous,
			GoToBookmark and Repeat buttons.
			
		- Markup Lines
			- When a markup line was added through the Extra Tools panel, the option to display the line in all views was not
			working properly. Also, it was not correctly linked to image when using the Extra Tools panel feature to display
			the image in various viewing modes.
			
		  
<a href="https://bainesimaging.com" target="_blank">Baines Imaging Research Laboratories</a>, Verspeeten Family Cancer Centre, London Health Sciences Centre, London, ON, Canada
