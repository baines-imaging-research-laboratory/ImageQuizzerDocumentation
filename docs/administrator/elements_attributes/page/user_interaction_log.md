---
hide:
- toc
---
# UserInteractionLog

## Specs

| |||
|---|---||
| **Name** | UserInteractionLog ||
| **Classification** | attribute ||
| **Parent** | <[Page](index.md)\> |
| **Required** | no ||
| **Syntax** | UserInteractionLog="*option*" |||
| **Options** | N | (default) interaction logs are not created |
|             | Y | interaction logs are created for each page |

## Description

The main function of the User Interaction Log feature is to capture the XY screen coordinates
 of the four corners of every viewing window,
along with the IJK values corresponding to the loaded image volumes displayed within those windows.
As the user interacts with the images by scrolling through them, this coordinate information
is continuously recaptured and added to the log file. 

A user interaction log may be used in conjuction with eye tracking software
which records XY screen coordinates of eye movements over time.
By cross-referencing the XY screen coordinates recorded by the eye tracking system
with the corresponding IJK values of the loaded image volume, it is possible
to determine the specific area of the image that the user was focusing on at a given time point.

Due to its close association with eye tracking, enabling this feature
results in a fixed viewing environment, which, in turn, restricts all movable
aspects of the application. This includes actions such as minimizing or resizing the
application and adjusting the size of the viewing windows. This lockdown happens on the first 
encounter of a Page with the attribute *UserInteractionLog="Y"* and will remain in effect for the remainder of the Session.

When you enable the UserInteractionLog feature for a Page element, the Image Quizzer will:

- lock down all adjustable sizing aspects of the display (at first encounter and effective for the remainder of the Session)
- generate a log file that records the viewing window XY screen coordinates
and the IJK values of the loaded image volumes displayed within those windows.

## Log details

Following is a list of the information captured in each log file:

	- CPU Uptime, Time,
	- Viewing window layout (TwoOverTwo, OneUpRedSlice, FourUp, SideBySideRedYellow),
	- Viewing window name (Red, Green, Yellow, Slice4),
	- Corner location (Top Left, Top Right, Bottom Left, Bottom Right),
    - Screen coordinates X,Y for corner location
	- Viewing window height, width (pixels),
	- Background image name I,J,K,
	- Foreground image name I,J,K,
	- Background transformation 4x4 matrix (XY to IJK),
	- Foreground transformation 4x4 matrix (XY to IJK)



## Example


See the [user interaction log example](../../examples/example_user_interaction_log.md)
for a script that uses this feature.

## Results

User interaction logs are unique to each XML Page that has
the UserInteractionLog attribute set to "Y" and are consequently
stored in the user's results folder within their respective Page subfolders.
When the user clicks the Next button to load a new Page of images, a new log
is generated to capture the interactions specific to that Page. Conversely, 
if the user presses the Previous button, the captured information is added 
to the existing log created for the previous Page.


The following tree structure represents the output for the script provided
in the example referenced above.

The log files are located in a subfolder created for each Page of the quiz XML file.


```
.
└─ImageDatabase/
   └─Users/
     └─Observer1/
       └─Test_UserInteraction.xml
	     ├─PgGroup1_Patient 1_CT/
         │ └─UserInteractionLog.csv
	     ├─PgGroup2_Patient2_PET PSMA/
         │ └─UserInteractionLog.csv
	     │...
```


