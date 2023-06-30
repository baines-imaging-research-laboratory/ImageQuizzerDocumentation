---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->

#Release Notes
	Image Quizzer v2.3
	mmm dd, yyyy - not yet released
	

##Requirements

	3D Slicer v4.11.20210226
	SlicerRT extension
	
##New Features

	- (v2.3.0) Added attribute 'MergeLabelMaps' at the Image level
		- This attribute along with the 'DisplayLabelMapID' and the the Loop attribute on a previous page.
		- It will trigger the merge functionality which will first search previous pages for a matching LabelMapID
     	  and with that previous page attribute Loop="Y" .
		- Then it will collect all the pages associated with that loop, get the label maps that were stored
		  for images with a matching LabelMapID and combine them into one merged label map file.
		- The merged image will be displayed.
		- For details see [MergeLabelMaps](../administrator/elements_attributes/image/merge_labelmaps.md)
	- (v2.3.0) Added new Question Type : Button
		- The Button question will execute an external script.
		- The Option element for this type of question stores the relative path to the script.
		- The path is relative to the Image Quizzer data location defined by the user at login time.
	- (v2.3.0) Added new Image attributes ZoomFactor and PanOrigin
		- You can now default the image for the initial view to be zoomed in or out.
		- Using PanOrigin, you can move the image view to be centred at a different origin.
		- These attributes along with InitialSliceOffset can help to focus the view on a region of interest when the image is loaded.



##Modifications

	- (vx.y) Descriptor
		- details

##Fix

	- (vx.y) Descriptor
		- details
		  
[Baines Imaging Research Laboratories](https://bainesimaging.com), LRCP, London Health Sciences Centre, London, ON, Canada
