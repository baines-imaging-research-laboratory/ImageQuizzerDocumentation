---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->

#Release Notes
	Image Quizzer v3.3.0
	December 2023
	

##Requirements

	3D Slicer v4.11.20210226
	SlicerRT extension
	SlicerOpenCV extension
	
##New Features

	- Window Level
		- A WindowLevel attribute was added for the Image elements giving the user a starting point
			- especially useful if not loading the image as dicom
	- Auto update of Slicer's extensions modules list
		- When launching Slicer and the Image Quizzer from a USB, this script will automatically
			add the Image Quizzer module path to Slicer's extensions list enabling an automatic
			start of the Image Quizzer from a startup batch file. This cannot be preset since
			a USB can have different drive letters when plugging into different PC's or laptops.
	- Markups Line viewing windows display
		- Markup lines are linked to the image in the viewing window where the lines are generated.
			There is now a 'Display in all views' checkbox in the Line Measurement group giving the
			user control whether the lines created appear in all viewing windows (potentially displaying
			other associated images) or only in the windows displaying the originally linked image.
	- Preprocessing conversion utility - ConvertDicomToNiiVolume
		- A script to convert a dicom series into a NIfTI volume. This can be run for an individual
		series or can be run in batch mode.
	
	
##Modifications

	
			
			
##Fixes

	- Exit / Resume
		- When exiting from a quiz if the user had already reached the last page of the quiz and all requirements 
			were met, resuming the quiz was starting on the wrong page. The code has been modified
			to bring the user back to the last page when Exit was pressed in order to resume and press the Finish
			button to mark the Quiz as completed.
			
	- Page ID and Descriptor attributes
		- A validation is performed to make sure there are no special characters in these strings.
			These two attributes along with the PageGroup number are used to create the subfolders
			in the results folder and special characters are not allowed in the naming of folders.
			
	- Capture Image State
		- Image state is now properly captured on the last page of the quiz when user presses the 'Finish' button.
			
			
		  
<a href="https://bainesimaging.com" target="_blank">Baines Imaging Research Laboratories</a>, LRCP, London Health Sciences Centre, London, ON, Canada
