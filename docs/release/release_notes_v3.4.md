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

	- v3.4.0 
		- ButtonScriptRerunRequired 
			- New attribute for a button type question forcing user's to rerun the associated script if revisit a page with this type of button.
			
		- UML diagram
			- added to folder .../ImageQuizzerProject/Documentation
		
	
##Modifications

	- v3.3
		- Response elements
			- If a user exits but has not answered all quiz questions, an empty response element 
			is now added to the results file.
			- An attribute has been added to the response element describing the event that led to the
			addition of the element.
			
		- Quiz validation
			- quiz is now validated against the xml schema stored in the .../ImageQuizzer/Inputs/MasterQuiz folder
			
		- File naming convention
			- Changed suffix for label map and markup line file names from -bainesquizxxx to -quizxxx to allow
			for more room when estimating the length of the saved files during quiz validation to stay under the Windows
			limit of 256 characters.
			
			
##Fixes

	- v3.3
			
		- Workflow fixes
			- code refactored addressing general fixes as user moves between pages especially for Previous,
			GoToBookmark and Repeat buttons.
			
		- Markup Lines
			- When a markup line was added through the Extra Tools panel, the option to display the line in all views was not
			working properly. Also, it was not correctly linked to image when using the Extra Tools panel feature to display
			the image in various viewing modes.
			
		  
<a href="https://bainesimaging.com" target="_blank">Baines Imaging Research Laboratories</a>, Verspeeten Family Cancer Centre, London Health Sciences Centre, London, ON, Canada
