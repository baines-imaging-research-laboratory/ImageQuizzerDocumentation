---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->

#Release Notes
	Image Quizzer v3.0.0
	September 29, 2023
	

##Requirements

	3D Slicer v4.11.20210226
	SlicerRT extension
	SlicerOpenCV extension
	
##New Features

	- (v3.0.0) 
		- Restructured the project directory tree
			- The restructuring of the project directory tree makes it easier for the administrator to navigate. 
			- There is now an Inputs subfolder to hold images, quiz, config files and scripts.
			- The Outputs subfolder stores the UsersResults.
			- For the user, the logging in process points to the default images and quiz directories.
		- New default locations:
			- Images:		 						.../ImageQuizzerProject/ImageQuizzer/Inputs/Images
			- Quiz file: 							.../ImageQuizzerProject/ImageQuizzer/Inputs/MasterQuiz
			- Scripts for 'Button' type questions:	.../ImageQuizzerProject/ImageQuizzer/Inputs/Scripts
			- Config file for emailing results:		.../ImageQuizzerProject/ImageQuizzer/Inputs/Config
			- Users results folders:				.../ImageQuizzerProject/ImageQuizzer/Outputs/UsersResults
			
	- (v3.0.0)
		- Users results folders
			- Results are no longer output to a subfolder under the image database parent directory.
			- This change was made in case there is no write access to where the images are stored.
			- The results can be found in the .../ImageQuizzerProject/ImageQuizzer/Outputs/UsersResults subfolder.
			
	
	
	
##Modifications

	- (v3.0.0)
		- Validation of ROIColorFile
			- Before launching a quiz, if an ROIColorFile is being used it is validated to ensure 
			a color has not been set up with the roi# = 0 . 
			(See documentation in Administrator guide> Scripting references > Session > ROIColorFile)
		- Validation of existence of image files 
			- If an image file is found to be missing from the image database folder selected 
			by the user during login, the user is prompted to change the location of the image
			database directory. The application does not error out any longer.

##Fix

	- (v3.0.0)
		- UserInteractionLog
			- Change was made to increase the viewing area 
				- height is no longer based on a ratio of the desktop pixel height but on a
				 calculation that takes into account the height of Slicer's menu and status bars.
		
		  
<a href="https://bainesimaging.com" target="_blank">Baines Imaging Research Laboratories</a>, LRCP, London Health Sciences Centre, London, ON, Canada
