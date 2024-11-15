---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->

#Release Notes
	Image Quizzer v3.4.0 - July 2024
				  v3.4.1 - July 2024
				  v3.4.2 - November 2024
	

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

	- v3.4.2
		- Disable floating segmentation toolset
			- User will no longer be able to undock the segmentation tool set which was previously enabled using space bar.

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
	- v3.4.2
		- ROIColorFile with indices not beginning with '1'
			If an ROI Color file is set up with the first index not equal to '1' the color spin box for segment editing
			will default to the	first label index number defined in the ROI Color table. If the user tries to 
			enter a label number into the spin box that is not defined in the ROI Color table, the system will
			automatically change the index to '0' (erase mode).
			
		- Viewing window not locked down in TwoOverTwo layout for the User Interaction lockdown feature
			On a Page with layout=TwoOverTwo and UserInteractionLog="Y", the top right (window 4) viewing window was not 
			locked for zoom and pan. (Red, Green and Yellow viewing windows were properly locked down). By adding an
			observer that captures when the layout changes, the app now locks down all 4 windows.
			
		- UserInteractionLog events not recorded
			The first Page that requested a user interaction log (UserInteractionLog="Y") was not being initialized 
			properly and therefore some initial events were not being recorded.
			
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
