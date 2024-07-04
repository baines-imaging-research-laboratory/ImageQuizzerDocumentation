---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->

# Getting started

The Image Quizzer is a tool that was designed to run as a module on the 3D Slicer platform.
Following you will find information to get the Image Quizzer installed and running on your computer.
See also [Quick links](../about/quicklinks.md) for overview and url links.

## System Requirements

* Windows operating system 
    - (tested with Windows 7, 10 and 11; not compatible on MAC OS at this time)
* Notepad (or some editor)

* 3D Slicer v 4.11.20210226


## Installation


### 3D Slicer

Download and install  <a href="https://slicer-packages.kitware.com/#collection/5f4474d0e1d8c75dfc70547e/folder/5f4474d0e1d8c75dfc705482" target="_blank">3D Slicer</a>
	 version 4.11.20210226
	
	
- Double click on the downloaded .exe file
- Accept installation defaults

!!! Warning
    We are using version 4.11.20210226; revision 29738
    
	Using any other version of Slicer may have unpredictable behaviour for this application.



##### Extensions

- Install 3D Slicer extensions : SlicerRT, SlicerOpenCV, mpReview (optional)
      * Open 3D Slicer
		* .\Slicer 4.11.20210226\Slicer.exe
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
		* .\Slicer 4.11.20210226\Slicer.exe
    * Select Edit>Application Settings
    * Select DICOM in the left-hand panel
    * Set Preferred multi-volume import format = volume sequence
    * Set Load referenced series = Always
    * Restart 3D Slicer if prompted



### Image Quizzer

##### Download

Latest release  <a href="https://github.com/baines-imaging-research-laboratory/BainesImageQuizzer/releases" target="_blank">here</a> labeled Image Quizzer v #.#.#

Pre-release versions <a href="https://github.com/baines-imaging-research-laboratory/BainesImageQuizzer/tags" target="_blank">here</a> labeled dev_v#.#.#

##### Extract

Once downloaded, extract all files from the BainesImageQuizzer-QuizApp_v#.#.#.zip file into the (recommended) folder named **BainesImageQuizzer**.

!!! Warning 
	BACKUP Inputs and Outputs folders !!!
	
    If overwriting an existing copy of the Image Quizzer, be sure to back up any results, images and setup files
	currently stored in the Inputs and Outputs folder. 

##### Components

The following directory tree describes the basic files and folders 
that may be relevant to the study administrator when developing the script. 


```
.
└─ BainesImageQuizzer/
   ├─ Documentation/
   │     └─ ReadMe.txt                              (contains links to on-line documentation)  
   ├─ ImageQuizzer
   │     ├─ Code/                                   (contains code to run the Image Quizzer application)
   │     ├─ Inputs/
   │     │   ├─ Config/
   │     │   │    └─ smtp_config_template.txt       (smtp config setup template for emailing results)
   │     │   ├─ Images/                             (parent directory for default image database)
   │     │   │   └─ ImageDatabase         			
   │     │   ├─ MasterQuiz/                         (default location for XML master quiz file)
   │     │   │   └─ *.xsd                           (XML schema file for script development)
   │     │   └─ Scripts/                            (default location for scripting files for 'Button' type questions)
   │     └─ Outputs/
   │         └─ UserResults                         (parent directory for users quiz results)
   ├─ USB-Support/
   │     ├─ README - Startup.txt
   │     ├─ Start Image Quizzer.bat
   │     ├─ USB01-RunScriptShell.py
   │     └─ USB02-UpdateSlicerExtensionList.py
   │
   ├─ImageQuizzerStartup.bat         (starts the Image Quizzer and does cleanup on close)
   ├─ImageQuizzerStartup-USB.bat     (starts the Image Quizzer installed on USB and does cleanup on close)
   └─ImageQuizzerShutdown.bat        (updated when running the quiz; may not exist on install)
   
```

!!! Note
    There are other files/folders not shown in this tree. They are not necessary for script development.
    but required for execution of the Image Quizzer module.	
	

### Connecting Image Quizzer to 3D Slicer

#### PC based (fixed device) install

To connect the Image Quizzer module

* Open 3D Slicer
* Select Edit > Application Settings
* Select Modules in the left-hand panel
* Click Add in the panel to the right of  “Additional module paths:” (you may have to click the ‘>>’ button)
* Browse for folder named **ImageQuizzer\Code** in the downloaded BainesImageQuizzer
    * eg. C:\Users\username\Documents\BainesImageQuizzer\ImageQuizzer\Code
* Restart 3D Slicer if prompted

#### USB based (portable device) install

Since a USB when mounted on various PC's or laptops can have differing drive letters, this
connection is done automatically when you use the ImageQuizzerStartup-USB.bat batch file.


## How to start the Image Quizzer

There are two ways to run the Image Quizzer.

1. Using the Startup batch file (recommended)

    It is recommended that you use the startup batch file, especially if you are loading DICOM images.
    The observer needs to navigate to the BainesImageQuizzer folder
	
    eg. C:\Users\username\Documents\BainesImageQuizzer
	
	Double-click on one of the two startup batch files:
	
		-ImageQuizzerStartup.bat
		-ImageQuizzerStartup-USB.bat  (use only if installs of the Image Quizzer and Slicer were consolidated on a USB stick.)
		
    The startup batch file will start Slicer and immediately bring the user to the Image Quizzer login screen.

    When the user exits the quiz, the batch file will start a shutdown process that will clear
    the SlicerDicomDatabase folder that was created in the ImageQuizzer\Outputs folder.
    (This folder is created automatically by Slicer whenever the Image Quizzer is started.
	Deleting this folder reduces the startup time when restarting the Image Quizzer.)


1. Selecting the Image Quizzer module in Slicer

    To start the module directly from Slicer, click in the Module box and look for
    Baines Custom Modules > Image Quizzer

    !!! Note
	    If starting the Image Quizzer without using the Startup batch file and
		you are loading DICOM image data, you can speed up the restart 
		by deleting the SlicerDicomDatabase folder between Image Quizzer startups.
		This folder is created automatically whenever the Image Quizzer is started 
		in the Outputs folder.
		
		    ...\BainesImageQuizzer\ImageQuizzer\Outputs\SlicerDicomDatabase
		

## Test your installation

You can test your installation by following the instructions for [building a simple script](../administrator/examples/build_basics.md).


See [Quiz Examples](../administrator/examples/index.md) section in the Administrator's guide
for examples showing how to build your script and activate various features available in the Image Quizzer.

## Quiz Results

Quiz results can be found in the folder:

...\BainesImageQuizzer\ImageQuizzer\Outputs\UserResults\\*username*\\*quizname*

See [Quiz Results - Response Capture](../administrator/results.md) section for more details.



## Distribution to observers

Following are some options on how to get this tool to your observers/students:

* [install and setup](#installation) on individual's laptop/PC as described above.
* set up for [remote access](#setup-for-remote-access).
* or [distribute on a USB](#distribute-via-usb)

## Logging in

!!! Warning
    If you choose to have observers log into one PC, whether remotely or locally,
    it is recommended that each observer log in with a unique name. The default
    name displayed in the login window matches the Windows user name. This can be 
	overriden. The login name associated with each observer is used to create the 
	user's results folder, keeping responses for each observer separate.
	
	If the user exits the quiz prior to completion, the quiz can be resumed from that
	spot IF the user logs in again using the same name as the original login.
    
	Capturing the quiz results folder for a user and moving it to a secure location reduces the 
	risk of a user logging in under the wrong user name - accidentally overwriting
	results from another user.

### Setup for remote access

One option for running the Image Quizzer is to install the tool on a PC that observers
are able to log into remotely.
 
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

Distribution to observers can be done by setting up a USB with 3D Slicer and the Image Quizzer module already installed, along with study data (encrypted) and the XML quiz file.
This USB can then be plugged into the observers laptop or PC and the quiz is ready-to-go. 
Use ImageQuizzerStartup-USB.bat to start the Image Quizzer as described above in [How to start the ImageQuizzer](#how-to-start-the-image-quizzer)

In the USB-Support folder, the following two files can be moved to the USB root directory for the user's convenience:

- Start Image Quizzer.bat
- README - Startup.txt

The startup batch file assumes the following layout on the USB:
```
/
├─ BainesImageQuizzer
├─Slicer 4.11.20210226
├─Start Image Quizzer.bat      - for autostart of Image Quizzer
└─README - Startup.txt         - for general instructions on auto and manual start (optional)

```
