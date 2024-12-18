---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->

#Release Notes
	Image Quizzer v3.4.0 - July 2024
				  v3.4.1 - July 2024
				  v3.4.2 - November 2024
				  v3.4.3 - 
	

##Requirements

	3D Slicer v4.11.20210226
	SlicerRT extension
	SlicerOpenCV extension
	
##New Features

	- v3.4.3
		- Button color
			- The administrator has the ability to customize the color of a 'Button' type of 
			question using the new 'ButtonColorOn' attribute assigning the desired RGB values.
			
		- Toggle button 
			- The administrator can change the functionality of a button to *Toggle* mode
			by setting the 'ButtonToggleColorOff' attribute for a 'Button' type of question.
			
			Without 'ButtonToggleColorOff' attribute set, a button will run the underlying
			script and the suffix '-Done' is added to the text on the button. The quiz will not move
			on to the next page until the button has been pressed running the underlying script.
			
			By setting the 'ButtonToggleColorOff' attribute with customized RGB values, the
			button goes into a toggle mode. The button can be pushed as many times as the user
			wants to run the underlying script or not pushed at all. The color of the button
			will oscillate between the color assigned with the 'ButtonColorOn' attribute
			or the default color if unassigned) and the assigned 'ButtonToggleColorOff' RGB
			values. The quiz will proceed to the next page regardless of whether this button 
			is pressed or not.
		
	- v3.4.1
		- UML diagram
			- added to folder .../ImageQuizzerProject/Documentation

		- Quiz validation
			- quiz is now validated against the xml schema stored in  
				.../ImageQuizzer/Inputs/MasterQuiz/ImageQuizzer.xsd
		
	- v3.4.0
		- Response element events
			- An attribute has been added to the response element describing the event that led to the
			addition of this element. This helps the administrator with the analysis of the results quiz.
			
	
##Modifications

	- v3.4.3
		- Quiz validation 
			- restrictions lifted for matching segmentation type elements (labelmaps, segmentation files,
			RTStruct files) to image volume elements. Previously, one image volume could only be
			associated with one segmentation type of file. Now, the administrator has more flexibility
			to load different segmentation files for the same image that is being displayed in different
			viewing windows.

	- v3.4.2
		- Disable floating segmentation toolset
			- User will no longer be able to undock the segmentation tool set which was previously 
			enabled using space bar.

	- v3.4.1
		- QuestionSet elements
			- As a result of the addition of the XMLSchema validation, each Page on the Quiz must have 
			a QuestionSet element. There can be multiple QuestionSets and they can be empty 
			(no Question elements). If there are Image elements on the Page, the QuestionSet 
			element must follow the Image elements.
			
	- v3.4.0
		- File naming convention
			- Changed suffix for label map and markup line file names from -bainesquizxxx to -quizxxx 
			to allow for more room when estimating the length of the saved files during quiz validation
			to stay under the Windows limit of 256 characters.
			
			
##Fixes

	- v3.4.3
		- UserInteractionLog bug
			- There was a bug when closing the UserInteractionLog on the last page. It would crash and the last
			set of coordinates would not be saved in the log as well as the last set of contours if there was
			any segment editing done. This was resolved with proper file handling at the close of the quiz.
			
	- v3.4.2
		- ROIColorFile with indices not beginning with '1'
			If an ROI Color file is set up with the first index not equal to '1' the color spin box for 
			segment editing will default to the	first label index number defined in the ROI Color table.
			If the user tries to enter a label number into the spin box that is not defined in the 
			ROI Color table, the system will automatically change the index to '0' (erase mode).
			
		- Viewing window not locked down in TwoOverTwo layout for the User Interaction lockdown feature
			On a Page with layout=TwoOverTwo and UserInteractionLog="Y", the top right (window 4) viewing 
			window was not locked for zoom and pan. (Red, Green and Yellow viewing windows were properly
			locked down). By adding an observer that captures when the layout changes, the app now 
			locks down all 4 windows.
			
		- UserInteractionLog events not recorded
			The first Page that requested a user interaction log (UserInteractionLog="Y") was not being 
			initialized properly and therefore some initial events were not being recorded.
			
	- v3.4.1
		- fix XMLSchema which wasn't validating the quiz during quiz launch the same way that Notepad++ 
			would validate it. Notepad++ would allow for a Page with only Image elements and no QuestionSet 
			elements. Validation through the code during quiz launch would not allow this. 
			This fix provides consistency between both validators. Now,	the administrator must always have
			one or more QuestionSet elements on a Page and it must follow the Image elements if there are any.
			The QuestionSet element can be empty.

	- v3.4.0
		- Workflow fixes
			- code refactored addressing general fixes as user moves between pages especially for Previous,
			GoToBookmark and Repeat buttons.
			
		- Markup Lines
			- When a markup line was added through the Extra Tools panel, the option to display the line in all 
			views was not working properly. Also, it was not correctly linked to image when using the Extra Tools
			panel feature to display the image in various viewing modes.
			
		  
<a href="https://bainesimaging.com" target="_blank">Baines Imaging Research Laboratories</a>, Verspeeten Family Cancer Centre, London Health Sciences Centre, London, ON, Canada
