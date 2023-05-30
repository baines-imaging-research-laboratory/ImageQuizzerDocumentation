---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->

#Release Notes
	Image Quizzer v2.2.1
	May 30, 2023
	

##Requirements

	3D Slicer v4.11.20210226
	SlicerRT extension
	
##New Features

	- (v2.1) Added attribute 'InitialSliceOffset' at the Image level
		- when image is initially loaded, it will be displayed at the offset (in mm) set in the quiz xml file
		- example:
			<Image Type="Volume" ID="MR" RotateToAcquisition="Y" InitialSliceOffset="35.15">
				<DefaultDestination>Yellow</DefaultDestination>
				<Layer>Background</Layer>
				<DefaultOrientation>Coronal</DefaultOrientation>
				<Path>ImageVolumes\BrainTumor1\MRBrainTumor1.nrrd</Path>
			</Image>

	- (v2.1) Added attribute 'ContourVisibility' at the Session level
		- Options: 'Fill' (solid display) or 'Outline' (default)
		- This setting applies to images loaded as a label map as well as a segmentation.

	- (v2.2) Added ContourVisibility controls to Extra Tools tab
		- User can toggle whether contours appear as outlines or filled.
		- User can also change the opacity of the contours.

	- (v2.2) Added Email Results feature
		- Study coordinator can add 'EmailResultsTo="email@address.com"' attribute to the Session element
		- When user has completed the quiz, the results folder will be zipped and emailed to the address given
		- Configuration for smtp host server must be defined (See documentation)


##Modifications

	- (v2.1) XML attribute changes (not backwards compatible with previous versions)
		- new attribute 'InitialSliceOffset' added to Image element
		- new attribute 'EmailResultsTo' added to Session element
		- new attribute 'ContourVisibility' added to Session element


##Fix

	- (v2.2.1) Reading DICOM images sometimes would load a volume multiple times.
		- Image Quizzer code was modified to load DICOM images using the SOPInstanceUID function.
		  This function takes into account the confidence associated with each Slicer plugin that
		  is available for loading the image and chooses the one with the highest confidence.

	- Fix display using Viewing Display options in Extra Tools tab for time series image volumes.
		  Sometimes, the image would not be displayed at all, or when being the "Reset to default"
		  button is pressed, the state of the image (slice number being observed) would not be retained. 
		  
[Baines Imaging Research Laboratories](https://bainesimaging.com), LRCP, London Health Sciences Centre, London, ON, Canada
