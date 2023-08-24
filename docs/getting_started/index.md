---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->

# Getting started

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


### 3D Slicer

Download and install [3D Slicer](   
	https://slicer-packages.kitware.com/#collection/5f4474d0e1d8c75dfc70547e/folder/5f4474d0e1d8c75dfc705482)
	 version 4.11.20210226
	
	
- Double click on the downloaded .exe file
- Accept installation defaults

!!! Warning
    We are using version 4.11.20210226; revision 29738
    
	Using any other version of Slicer may have unpredictable behavior for this application.



##### Extensions

- Install 3D Slicer extensions : SlicerRT, SlicerOpenCV, mpReview (optional)
      * Open 3D Slicer
      * Select View > Extension Manager
		  * In the Search field (upper right-hand corner) input SlicerRT
		  * Click Install
		  * There will be a message to say the extension was installed
		  * Click on Restart (bottom right-hand corner) and OK
      * Repeat for SlicerOpenCV
      * Repeat for mpReview extension (optional)
          * This extension can be used as a preprocessor to convert dicom series slices to nrrd (or nifti) data volume to speed up loading of images when running the quiz

##### Settings

* Set Slicer application settings to be compatible with Image Quizzer
    * Open 3D Slicer
    * Select Edit>Application Settings
    * Select DICOM in the left-hand panel
    * Set Preferred multi-volume import format = volume sequence
    * Set Load referenced series = Always
    * Restart 3D Slicer if prompted



### Image Quizzer

##### Download

Download the Image Quizzer [here](
https://github.com/baines-imaging-research-laboratory/BainesImageQuizzer/tags)

- The release versions are labeled QuizApp_v#.#.#
- The pre-release, with the latest features are labeled dev_v#.#.#

##### Extract

Once downloaded, extract all files from the BainesImageQuizzer-QuizApp_v#.#.# file.

##### Components

The following directory tree describes the basic files and folders 
that may be relevant to the study administrator when developing the script. 


```
.
└─ ImageQuizzerProject/
   ├─ Documentation/
   │     ├─ XML Elements and Attributes.xls (keywords to create the script)  
   │     └─ 3D Slicer – Keyboard Shortcuts.docx (popular shortcuts for the user when in quiz)  
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
    There are other files/folders not shown in this tree. They are not necessary for script development.
    They may be either under development or required for execution of the Image Quizzer module.	
	


### Connecting Image Quizzer to 3D Slicer

To connect the Image Quizzer module

* Open 3D Slicer
* Select Edit > Application Settings
* Select Modules in the left-hand panel
* Click Add in the panel to the right of  “Additional module paths:” (you may have to click the ‘>>’ button)
* Browse for folder named **ImageQuizzer** in the downloaded ImageQuizzerProject
    * eg. C:\Users\username\Documents\ImageQuizzerProject\ImageQuizzer
* Restart 3D Slicer if prompted

## How to start the Image Quizzer

There are two ways to run the Image Quizzer.

1. Using the Startup batch file (recommended)

    It is recommended that you use the startup batch file, especially if you are loading DICOM images.
    The observer needs to navigate to the ImageQuizzerProject folder
	
    eg. C:\Users\username\Documents\ImageQuizzerProject
	
	and double click on the ImageQuizzerStartup.bat file.
    The startup batch file will start Slicer and immediately bring the user to the Image Quizzer login screen.

    When the user exits the quiz, the batch file will start a shutdown process that will cleanup
    the SlicerDicomDatabase folder that was created.
    (This folder is created automatically by Slicer whenever the Image Quizzer is started.
	Deleting this folder reduces the startup time when restarting the Image Quizzer.)

    !!! Note
        Both the Startup and Shutdown batch files have commands specific to the Windows environment.
        If using a MAC, start the Image Quizzer directly in Slicer as described below.


1. Selecting the Image Quizzer module in Slicer

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
	

## Test your installation

You can test your installation by following the instructions for [building a simple script](../administrator/examples/build_basics.md).


See [Quiz Examples](../administrator/examples/index.md) section in the Administrator's guide
for examples showing how to build your script and activate various features available in the Image Quizzer.



## Distribution to observers

Following are some options on how to get this tool to your observers/students:

* [install and setup](#installation) on individual's laptop/PC as described above.
* set up for [remote access](#setup-for-remote-access).
* or [distribute on a USB](#distribute-via-usb)

### Setup for remote access

One option for running the Image Quizzer is to install the tool on a PC that observers
are able to log into remotely.
 
!!! Warning
    If you choose to have observers log into one PC, whether remotely or locally,
    it is recommended that each observer has their own login account. The login named
    associated with each observer is used to create the user's results folder, keeping 
	responses for each observer separate.
    
	If you don't have unique accounts, you risk overwriting a previous user's results.
	You must move the current user's results folder into a secure area before the next observer starts their quiz session.
    .
There may be display issues if you are setting up the Image Quizzer so that the users can log in remotely. 
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

### Distribute via USB

Distribution to observers can be done by setting up a USB with 3D Slicer and the Image Quizzer module already installed, along with encrypted study data and the XML quiz file.
This USB can then be plugged into the observers laptop or PC and the quiz is ready-to-go.

!!! tip
    VeraCrypt is an application that can be used to encrypt data and mount the encrypted volume onto your PC; (admin rights are required).


