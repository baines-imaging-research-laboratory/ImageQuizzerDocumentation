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

### Image Quizzer

The Image Quizzer project is currently available with special access permission through GitHub.
This will be made public in the near future (estimate 2nd quarter 2023).

Once downloaded, the following directory tree describes the basic files and folders 
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
	


### 3D Slicer

Download and install 3D Slicer version 4.11.20210226
    
	* https://download.slicer.org/download?os=win&date=2021-02-26
	
	or
	
	https://slicer-packages.kitware.com/#collection/5f4474d0e1d8c75dfc70547e/folder/5f4474d0e1d8c75dfc705482
	
	
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
          * This extension can be used as a preprocessor to convert dicom series slices to nrrd (or nifti) data volume to speed up loading of images when running the quiz

* Set Slicer application settings to be compatible with Image Quizzer
    * Open 3D Slicer
    * Select Edit>Application Settings
    * Select DICOM in the left-hand panel
    * Set Preferred multi-volume import format = volume sequence
    * Set Load referenced series = Always
    * Restart 3D Slicer if prompted

!!! Note
    We are using version 4.11.20210226; revision 29738
    
	Using any other version of Slicer may have unpredictable behavior for this application.



### Connecting Image Quizzer to 3D Slicer

To connect the Image Quizzer module

* Open 3D Slicer
* Select Edit > Application Settings
* Select Modules in the left-hand panel
* Click Add in the panel to the right of  “Additional module paths:” (you may have to click the ‘>>’ button)
* Browse for folder named **ImageQuizzereQuizzer** in the downloaded ImageQuizzerProject
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
	You must move the current user's results folder into a secure area before the next observer starts his/her quiz session.
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

## Sample datasets

You will find references in the [example scripts](../administrator/examples/index.md) section of this documentation
for datasets that are available in 3D Slicer.
If you wish to run the Image Quizzer example quizzes, you can download and save the image volumes
using the instructions below. Some of the sample datasets referenced to run the example scripts include:

* CTChest
* MRHead
* MRBrain Tumor1
* CT Cardio Volume Sequence
* TinyPatient (available when Developer's mode is enabled in Edit>Application Settings>Developer)

#### Download and save

Following is a brief set of commands to download and save any of the available image datasets.

* Open 3D Slicer. 
* In the Welcome to Slicer module, select **Download Sample Data**
* Select the image dataset to download.
* Select File>Save in Slicer's menu bar
* Unselect all check marks under File Name except for the image volume being saved.
* The default file format for saving data is *.nrrd which will match the script examples.
* Browse to the folder that you wish to save the sample data.
* Click on the Save button.

Refer to Slicer's documentation for [download and save](https://slicer.readthedocs.io/en/latest/user_guide/data_loading_and_saving.html) for more more details.

#### Suggested tree structure

This is the tree structure we use for testing and building the example scripts.
If you are using a tree structure with customized folder names,
you will have to modify the image **Path** element in the scripts to match your tree layout.

We recommend saving your data in a subfolder (e.g. ImageVolumes) since, in the parent database directory (ImageQuizzerData)
two other subfolders will be created:

1. The **Users** folder which will hold the observer response files.
1. The **SlicerDicomDatabase** folder that Slicer automatically creates to store pointers to the loaded DICOM files.

```
.
└─ ImageQuizzerData/
    │ └─ ImageVolumes/
    │     ├─ MRHead/
    │     │     └─ MRHead.nrrd
    │     ├─ MRBrain/
    │     │     └─ MRBrain.nrrd
    │     │
    │     ... etc.
	
	(automatically created)
    │	  
	├─ Users/
	└─ SlicerDicomDatabase/

```




