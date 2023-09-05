---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->

#Release Notes
	Image Quizzer v2.0.0
	October 18, 2022
	

##Requirements

	3D Slicer v4.11.20210226
	SlicerRT extension
	
##New Features

	- Added Extra Tools tab
		- Interactive Mode to adjust the Window/Level of the image
		- Crosshairs tools
			- when selected, the user must press the Shift key to activate the crosshairs
			- a toggle to turn on/off slice intersections 
		- Viewing Display Options
			- Allows the user to view a selected image in either:
				- 3 planes (displays Axial, Sagittal and Coronal)
				- 1 plane (displays specified orientation in one window)
			- Reset to default button will return to the originally defined setup from the quiz xml file
		- Line Measurement tools
			- a ruler tool to allow user to create measured line(s) (MarkupsLine)
			- measurements are captured in the user's quiz responses folder under the associated Page subfolder
				- filenames follow the format ImageID_Markupsline_n-bainesquizline.mrk.json files 
			- a delete tool to remove the last created point created
			- a button to clear all lines created on that Page
			- the 'Add new line' and 'Clear all' buttons are disabled when the Page is defined as complete and no multiple responses are allowed

	- Added Looping
		- new attribute for Page element Loop="Y"
		- when this Page is displayed, a Repeat button is accessible to the user
		- when pressed, the Images and Quiz questions for that Page will be duplicated in the xml file
		- this allows the user to create new quiz responses for the same set of images
		- use case example:
			- the user must segment all lesions one at a time, pressing Repeat to create a new segment
			- responses to quiz questions are specific for each contour
			
	- Added Page Randomizing
		- new attribute RandomizePageGroups added to Session element
		- new attribute PageGroup added to Page element
			- Page group numbers are required if randomizing is requested
			- if a PageGroup=0 is set, these Pages will remain at the beginning of the quiz;
				remaining pages are randomized
			- if there are pages with the same PageGroup number, they will be kept together during randomization;
				for exampleyou may want to keep all Pages holding images for a particular patient together (CT page, Follow-up1 page, Follow-up2 page etc.)
				
## Modifications

	- XML attribute changes (not backwards compatible with previous versions)
		- element tag Destination changed to DefaultDestination
		- element tag Orientation changed to DefaultOrientation
		- attribute EnableSegmentEditor moved from Image element to Page element
		- attribute SegmentRequired moved from QuestionSet element to Image element
		- new attribute SegmentRequiredOnAnyImage added to Page element
		- new attribute MinMarkupLinesRequiredOnAnyImage added to Page element
		- ROIs element now required on any element loaded as RTStruct or Segmentation;
			previously this was only required if the image element being loaded had attribute DicomRead="Y"

		
		  
<a href="https://bainesimaging.com" target="_blank">Baines Imaging Research Laboratories</a>, LRCP, London Health Sciences Centre, London, ON, Canada
