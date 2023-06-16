---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# MergeLabelMaps

## Specs

| ||Details|
|---|---|---|
| **Name** | MergeLabelMaps ||
| **Classification** | attribute ||
| **Parent** | <[Image](index.md)\> ||
| **Required** | no ||
| **Syntax** | MergeLabelMaps="*option*" |  |
| **Options** | Y | previous label maps are merged into one file and displayed|
|             | N |(default) no merged label maps are created|
| **Dependencies**| For current page/image elements |DisplayLabelMapID - exists|
||| Path for image matches image on historical page |
|||PageGroup - number matches that of historical element|
|||SegmentEditor - off|
|||SegmentRequiredOnAnyImage - off|
||For historical page/image elements| LabelMapID - matches DisplayLabelMapID |
||| Path for image matches image on current page |
|||Loop='Y'|
||| Page ID and Descriptor match for all repetitions (ignoring 'Rep##')|
|| | PageGroup number match to current page |



## Description

The MergeLabelMaps attribute works in association with the page Loop attribute. 
This is useful when you want the user to answer quiz questions for each ROI seen on an image
and then have all the ROI's for that image displayed on a subsequent page.

This documentation refers to the 'Current' page (where MergeLabelMaps is defined on the image) and
a 'Historical' page that contains the paths to the label maps created using the 'Repeat' button.
The historical pages are found by matching the DisplayLabelMapID with a previous image holding the same LabelMapID.
The historical pages must meet a number of matching conditions:

- The [Loop](../page/loop.md) page attribute set to 'Y'. This allowed the user to use the 'Repeat' button
to create new pages. The 'ID' for each page was suffixed with the rep number '-Rep##'.
All historical pages from this loop (matching ID and Descriptor - without the -Rep## substring) will have the
label maps merged.
- The PageGroup numbers must match
- The image element 'Path' for the current and historical elements must match where 'LabelMapID' was set.

During quiz validation, all segmenting attributes are disallowed on the current page. This includes
the attributes 'EnableSegmentEditor', 'SegmentRequiredOnAnyImage' on the current page
and 'SegmentRequired' on any image of the current page must be set to 'N' or not existent.

During the merge, the function will collect all the labelmaps from the labelmap paths stored in the historical image,
combine them and then save them to a folder for the current page. The merged labelmap filename will have
the PageGroup#_PageID_LabelMapID-bainesquizlabel.nrrd.

If the user presses the Previous button to do some modifications and then Next to come back to the page with the MergeLabelMaps attribute,
the merge will happen again and the current merge file will be overwritten. This way the user 
can press previous to the looping page, change previously drawn contours (if AllowMultipleResponse="Y"), 
or press 'Repeat' to create a new page within that loop. 


