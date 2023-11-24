---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->

#Release Notes
	Image Quizzer v3.2.0
	November 10, 2023
	

##Requirements

	3D Slicer v4.11.20210226
	SlicerRT extension
	SlicerOpenCV extension
	
##New Features

	- Go To Bookmark
		- A new feature was added with two new Page attributes 'BookmarkID' and 'GoToBookmarkID'
		- This allows a user to return to a previously defined Page.
	- Markups Line measurement visibility
		- There is now a 'Show Length' checkbox in the Line Measurement group. 
		The user now has control whether the length of the lines added are visibile or not.
	- Setting the contour tool radius
		- A new Page attribute 'ContourToolRadius' was added to initialize the radius of the paint brush tool.
		This allows the user to begin contouring without having to adjust the radius slider for each newly
		displayed set of images. 
			
	
	
##Modifications

	- Segment Editor settings
		- When the user has selected a volume and drawing tool to start contouring a region of interest,
		these settings are maintained if the user moves to the Quiz or Extra Tools tabs and then returns
		to the Segment Editor tab to continue contouring.
	- Quiz validation
		- Attribute pairs 'BookmarkID' - 'GoToBookmarkID' and 'LabelMapID' - 'DisplayLabelMapID' 
		must be set with the same PageGroup numbers if the 'RandomizePageGroup' attibute is set to "Y"
	- Extra Tools Buttons
		- The Window/Level and Crosshairs buttons are now toggle type buttons
	- Question type: Button
		- The Button type of question has been modified to make it mandatory that 
		the button has been clicked
			
			
##Fixes

	- Question type: Button
		- The code has been modified to ensure proper execution of the external script 
		when running the application on different devices. 
		- All button-type questions are mandatory. Each button must be pressed.
	- User Interaction Log - coordinates capture
	    - Turning on and off of the logging feature to the capture of coordinates is now coordinated 
		properly when transitioning to different layouts using the Display Views tool on the Extra Tools tab.
	- Pop-up progress bar showing load of images through Image Quizzer was removed. This was causing Slicer to
	    randomly fail without error messages.
	- DisplayLabelMapID and LabelMapID
		- If RandomizePageGroups attribute for the Session is set to "Y", the pages that have 
		the image attributes LabelMapID and the corresponding DisplayLabelMapID defined must also have
		the	PageGroup attribute defined with the same number.
		
		  
<a href="https://bainesimaging.com" target="_blank">Baines Imaging Research Laboratories</a>, LRCP, London Health Sciences Centre, London, ON, Canada
