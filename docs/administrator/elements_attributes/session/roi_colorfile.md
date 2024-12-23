---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# ROIColorFile

## Specs

| ||Details|
|---|---|:---:|
| **Name** | ROIColorFile ||
| **Classification** | attribute ||
| **Parent** | <[Session](index.md)\> ||
| **Required** | no ||
| **Syntax** | ROIColorFile="*colorfilename*" | filename without .txt extension |

## Description

The ROIColorFile attribute gives the administrator the ability to assign specific ROI names and colors that will appear as options
when the user is contouring in the segment editor. This can be useful when you want to restrict the user to
a specific set of ROI's and have each ROI categorized by color.

!!! Note
	The ROI color file settings are applicable solely to label maps, which when creating contours with the segment editor these
	color options are displayed, or when a label map is imported as an XML image element in the Master Quiz file with Type="LabelMap." 
	These settings do not apply to Segmentation or RTStruct types of image elements.

## Setup

To activate this feature, the administrator must create a .txt file in an editor using the syntax shown below.
This file must be saved in the same folder as the study xml file.


## Syntax

Syntax for each line in the text file. **NB. The roi# cannot be 0** :

```
roi# roi_name red green blue alpha
```


Typically, the table is arranged with roi index numbers beginning at 1, with each subsequent entry having consecutive indices.
While it's possible to start with a different index number, if a user manually inputs a number into the spin box that isn't present in the color file, 
the system will automatically change the number to '0' (erase mode). Additionally, if the numbers aren't consecutive, the spin box for
selecting the contour label index may freeze on label '0', requiring the user to press the color bar to establish a valid index entry.

Empty lines are not acceptable. A line beginning with '#' can be used as a comment line.


## Example

### Setup

A color file is assigned to a study for PI-Rads segmentation.
The administrator creates a text file (PiRadsStudy_colors.txt) and places it in
the same directory as the XML for this quiz (PIRADS_SegmentationStudy.xml).

!!! tip
    In this example, these files are being placed in the default directory used by 
    Image Quizzer for the master quiz. Having the quiz and color file in the MasterQuiz
	directory saves the user from having to navigate through file explorer to locate the quiz.

```
.

└─ImageQuizzer/
  └─Inputs/
    └─MasterQuiz/
      ├─PIRADS_SegmentationStudy.xml
      └─PiRadsStudy_colors.txt
		
```

Add the attribute to the <Session\> element.	
```
<Session ROIColorFile="PiRadsStudy_colors">
	<Page>
		...
	</Page>
</Session>
```

Create the color text file.
```
PiRadsStudy_colors.txt

1 PI-RADS_very_low 128 174 128 255
2 PI-RADS_low 241 214 145 255
3 PI-RADS_intermediate 177 122 101 255
4 PI-RADS_high 111 184 210 255
5 PI-RADS_very_high 191 2 34 255

```


##Usage

To activate the color file popup in the Segment Editor, the user must press on the label's color bar.

![ROIColorFileScreenshot](assets/ROIColorFileScreenshot.png)

