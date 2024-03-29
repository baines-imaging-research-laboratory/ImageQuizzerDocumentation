---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->

#Release Notes
	Image Quizzer v2.3
	August 30, 2023
	

##Requirements

	3D Slicer v4.11.20210226
	SlicerRT extension
	SlicerOpenCV extension
	
##New Features

	- (v2.3.0) 
		- Added attribute 'MergeLabelMaps' at the Image level
			- This attribute along with the 'DisplayLabelMapID' and the the Loop attribute on a previous page.
			- It will trigger the merge functionality which will first search previous pages for a matching LabelMapID
			  and with that previous page attribute Loop="Y" .
			- Then it will collect all the pages associated with that loop, get the label maps that were stored
			  for images with a matching LabelMapID and combine them into one merged label map file.
			- The merged image will be displayed.
		- Added new Question Type : Button
			- The Button question will execute an external script.
			- The Option element for this type of question stores the relative path to the script.
			- The path is relative to the Image Quizzer data location defined by the user at login time.
		- Added new Image attributes 'ZoomFactor' and 'PanOrigin'
			- You can now default the image for the initial view to be zoomed in or out.
			- Using PanOrigin, you can move the image view to be centred at a different origin.
			- These attributes along with InitialSliceOffset can help to focus the view on a region of interest when the image is loaded.
		- Added new Page attribute 'UserInteractionLog' to capture screen X,Y coordinates and I,J,K values of loaded images.



##Modifications

	- (v2.3.0)
		- SlicerOpenCV extension
			- This extension is now a requirement. It is used for capturing the CPU uptime which is recorded in the logs
			created with the UserInteractionLog feature.
		- Segment Editor tab
			- Only the segmenting tools that are activated for the Image Quizzer are visible. This includes draw, paint, erase and 
			change label tools.
		- User Login name
			- User now has the option to change the login name from the Windows login default.  This is useful if the Image Quizzer application,
			data and quiz files are stored on a USB stick, allowing the user to work on the same quiz on different PC's.
		- Default location for image database
			- The default location for the quiz images is now .../ImageQuizzerProject/ImageQuizzer/Resources/ImageQuizzerData.
			The directory selector for the image database points here during the user login.
			Using this location to store the quiz images is not mandatory but may make it easier for users when logging in.

##Fix

	- (v2.3.0)
		- Extra Tools : Viewing Display Options
			- When 'Reset to default' button is pressed, the current state of the quiz questions is redisplayed instead of what has been stored in the XML results file.
		- Extra Tools : Viewing Display Options
			- Slice offsets and window/level values are maintained when moving between different viewing modes (3 Planes or 1 Plane) and the default setting.
		- Segment Editor : Sphere and Smudge tools
			- The sphere and smudge tools will now work when creating contours on a sagittal or coronal orientation - as well as the axial.
		
		  
<a href="https://bainesimaging.com" target="_blank">Baines Imaging Research Laboratories</a>, LRCP, London Health Sciences Centre, London, ON, Canada
