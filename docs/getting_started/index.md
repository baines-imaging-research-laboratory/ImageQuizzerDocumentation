# Getting started

<!--
* [System Requirements](system_requirements.md)

* [Installing](installation.md)

* [How to run](run.md)


-->
The Image Quizzer is a tool that was designed to run as a module on the [3D Slicer](https://slicer.org) platform.
Following you will find information to get the Image Quizzer installed and running on your computer.

## System Requirements

* Windows operating system (tested with Windows 7 and Windows 10)
* Notepad (or some editor)

* 3D Slicer v 4.11.20210226



!!! abstract "TODO"
    Currently, the Image Quizzer has been running on Windows operating systems (Windows 7 and 10). 
    With some adjustments to the installation notes, this may also run on a MAC system.

## Installation

### Image Quizzer

The Image Quizzer project is currently available with special access permission through GitHub.
This will be made public in the near future.

Once downloaded, the following directory tree describes the basic files and folders 
that may be relevant to the study coordinator when developing the script. 


```
.
└─ ImageQuizzerProject/
   ├─ Documentation/
   │     ├─ XML Elements and Attributes.xls (keywords to create the script)  
   │     └─ 3D Slicer – Keyboard Shortcuts.docx (popular shortcuts for user when in quiz)  
   ├─ ImageQuizzer
   │     └─ Resources/
   │           ├─ Config/
   │           │    └─ smtp_config_template.txt   (smtp config setup template for emailing results)
   │           └─ XML/
   │                ├─ Templates/
   │                │     └─ *.xml   (XML basics templates for script development)
   │                └─ *.xsd   (XML schema file for script development)
   ├─ImageQuizzerStartup.bat   (starts the Image Quizzer and does cleanup on close)
   └─ImageQuizzerShutdown.bat  (updated when running the quiz; may not exist on install)
```

!!! Note
    Other files/folders not shown in this tree may be:
	
    - required by the Image Quizzer module
    - relevant only to code developers
	- or under development


One option is to set up a USB with encrypted study data, the XML quiz file  along with 3D Slicer and the Image Quizzer module already installed and set up.
This USB can then be plugged into the observers laptop and the 
(VeraCrypt is an application that can be used to encrypt data and mount the encrypted volume onto your PC; admin rights are required.)



### 3D Slicer

Download and install 3D Slicer version 4.11.20210226
    
	* https://download.slicer.org/download?os=win&date=2021-02-26
	
!!! Note
    We are using version 4.11.20210226; revision 29738
    
	Using any other version of Slicer may have unpredictable behavior for this application

- Double click on the downloaded .exe file
- Accept installation defaults
- Install 3D Slicer extensions : SlicerRT, mpReview (optional)
      * Open 3D Slicer
      * Select View > Extension Manager
      * In the Search field (upper right-hand corner) input SlicerRT
      * Click Install
      * There will be a message to say the extension was installed
      * Click on Restart (bottom right-hand corner) and OK
      * Repeat for mpReview extension (optional)
          * Can be used as a preprocessor to convert dicom series to nrrd (or nifti) to speed up loading of images when running the quiz

* Set Slicer application settings to be compatible with Image Quizzer
    * Open 3D Slicer
    * Select Edit>Application Settings
    * Select DICOM in the left-hand panel
    * Set Preferred multi-volume import format = volume sequence
    * Set Load referenced series = Always
    * Restart 3D Slicer if prompted



## Connecting Image Quizzer to 3D Slicer

To connect the Image Quizzer module

* Open 3D Slicer
* Select Edit > Application Settings
* Select Modules in the left-hand panel
* Click Add in the panel to the right of  “Additional module paths:” (may have to click the ‘>>’ button)
* Search for folder named **ImageQuizzer** in the downloaded ImageQuizzerProject
    * eg. C:\Users\username\Documents\ImageQuizzerProject\ImageQuizzer
* Restart 3D Slicer if prompted

## How to start the Image Quizzer

There are two ways to run the Image Quizzer.

1. Using the Startup batch file

    It is recommended that you use the startup batch file, especially if you are loading DICOM images.
    The observer needs to navigate to the ImageQuizzerProject folder
	
    eg. C:\Users\username\Documents\ImageQuizzerProject
	
	and double click on the ImageQuizzerStartup.bat file.
    The startup batch file will start Slicer and immediately bring the user to the Image Quizzer login screen.

    When the user exits the quiz, the batch file will start a shutdown process that will cleanup
    the SlicerDicomDatabase folder that was created.
    This folder is created automatically whenever the Image Quizzer is started.
	Deleting this folder reduces the startup time when restarting the Image Quizzer.

    !!! Note
        Both the Startup and Shutdown batch files have commands specific to the Windows environment.
        If using a MAC, start the Image Quizzer directly in Slicer as described below.


1. Searching for the module in Slicer

    To start the module directly from Slicer, click in the Module box and look for
    Baines Custom Modules > Image Quizzer

    !!! Note
	    If starting the Image Quizzer without using the Startup batch file and
		you are loading DICOM image data, you can speed up the restart 
		by deleting the SlicerDicomDatabase folder between Image Quizzer startups.
		This folder is created automatically whenever the Image Quizzer is started.
		This folder can be found wherever you have defined your image data location.

        eg. If your image database is located here:
		
		    C:\Users\username\Documents\ImageDatabase
		
		you will find the SlicerDicomDatabase folder here:
		
		    C:\Users\username\Documents\ImageDatabase\SlicerDicomDatabase
	
 

## Setup for remote access

One option for running the Image Quizzer is to install the tool on a PC that observers
are able to log into remotely.
 
!!! Warning
    If you choose to have observers log into one PC, whether remotely or locally,
    it is recommended that each observer has their own login account. The login named
    associated with each observer is used to create the user's results folder.
    
	If you don't have unique accounts, you risk overwriting a previous user's results.
	You must move the current user's results folder into a secure area before the next observer starts the quiz.
    .
There may be issues if you are setting up the Image Quizzer so that the users can log in remotely. 
This is related to OpenGL which 3D Slicer uses for the graphical display.
Using the Image Quizzer through remote access may depend on the following:

* Video card driver
* Operating system edition and version
* Device management settings
* Remote desktop access software

We have had success using:

* Windows 10 Pro v 21H2
* NVIDIA Quadro 2000
* Windows Remote Desktop
* Other recommendations:
* Windows 10 must be used at both ends
* Google Remote Desktop, RealVNC, AnyDesk (free remote software options)

