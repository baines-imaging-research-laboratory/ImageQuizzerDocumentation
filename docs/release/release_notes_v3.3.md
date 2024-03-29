---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->

#Release Notes
	Image Quizzer v3.3.0 - December 2023
				  v3.3.2 - January 2024
				  v3.3.4 - February 2024
	

##Requirements

	3D Slicer v4.11.20210226
	SlicerRT extension
	SlicerOpenCV extension
	
##New Features

	- v3.3.0 
		- Window Level
			- A WindowLevel attribute was added for the Image elements giving the user a starting point
				- especially useful if not loading the image as dicom
			
		- Markups Line viewing windows display
			- Markup lines are linked to the image in the viewing window where the lines are generated.
				There is now a 'Display in all views' checkbox in the Line Measurement group giving the
				user control whether the lines created appear in all viewing windows (potentially displaying
				other associated images) or only in the windows displaying the originally linked image.
			
	- v3.3.1
		- Auto update of Slicer's extensions modules list
			- When launching Slicer and the Image Quizzer from a USB, this script will automatically
				add the Image Quizzer module path to Slicer's extensions list enabling an automatic
				start of the Image Quizzer from a startup batch file. This cannot be preset since
				a USB can have different drive letters when plugging into different PC's or laptops.
			
	- v3.3.0
		- Preprocessing conversion utility - ConvertDicomToNiiVolume
			- A script to convert a dicom series into a NIfTI volume. This can be run for an individual
			series or can be run in batch mode.

	- v3.3.4
		- Picture type question
			- This question type enables an image to be displayed in the quiz.
	
		- USB-Support
			- Connecting the Image Quizzer module to Slicer when using a USB is complicated by the fact that the 
			drive letter assigned to the USB is not consistent when plugged into different PCs or laptops.
			There are 2 python scripts in this folder that will update Slicer's extensions ini file automatically. 
			
			
	
##Modifications

	- v3.3.2
		- Markup Lines 
			- Option to display markup lines in all views is now set to False. 
			
			
##Fixes

	- v3.3.0
		- Exit / Resume
			- When exiting from a quiz if the user had already reached the last page of the quiz and  
			  all requirements were met, resuming the quiz was starting on the wrong page. 
			  The code has been modified to bring the user back to the last page when Exit was 
			  pressed in order to resume and press the Finish	button to mark the Quiz as completed.
				
		- Page ID and Descriptor attributes
			- A validation is performed to make sure there are no special characters in these strings.
			  These two attributes along with the PageGroup number are used to create the subfolders
			  in the results folder and special characters are not allowed in the naming of folders.
				
		- Capture Image State
			- Image state is now properly captured on the last page of the quiz when user 
			  presses the 'Finish' button.
		
	- v3.3.1
		- USB Startup batch scripts
			- Scripting adjusted to update the Slicer extensions list to automatically recognize 
			  the Image Quizzer.
			- These scripts use Python that is embedded in Slicer so that the users don't need to
			  download and install Python software.
			  
	- v3.3.2
		- Markup Lines 
			- The 'Display in all views' setting is now recognized immediately when first displaying 
			  the images (you no longer need to toggle this option to get it in sync).
			  
			- The 'Clear all lines' option now checks for existence of the file in the results folder
			  before calling on the operating system to delete it. (Previously, if an image was 
			  displayed in two views with different orientations, there may have been some undeleted
			  markup line files and the xml results file was not updated properly.)
			  
	- v3.3.3
		- UserInteractionLog
			- If you have a quiz that uses the UserInteractionLog attribute intermittently between Pages,
			  the zoom, pan and window resizing capabilities were not being enabled when the 
			  UserInteractionLog was set to 'N'.
		
	- v3.3.4
		- Question type "Button" messaging
			- Fix the validation error message when the script linked to the Button-type question
			  is not found.
		
		- Import of OpenCV library (cv2)- for UserInteractionLog="Y"
			- Error handling added for the import of the SlicerOpenCV extension. If the extension 
			  is missing (either not added or it is not available) the user interaction logs 
			  will have a 0 recorded in the logs for the CPU Uptime column.
			  
		- Validation added for the quiz to make sure all Page elements that have at least one Image  
			sub-element have at least one Image assigned to the Red viewing window.
			This ensures the availability of Slicer's segmentation functionality.
		  
<a href="https://bainesimaging.com" target="_blank">Baines Imaging Research Laboratories</a>, LRCP, London Health Sciences Centre, London, ON, Canada
