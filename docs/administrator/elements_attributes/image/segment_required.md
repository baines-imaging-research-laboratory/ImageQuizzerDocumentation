---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# SegmentRequired

## Specs

| ||Details|
|---|---|---|
| **Name** | SegmentRequired ||
| **Classification** | attribute ||
| **Parent** | <[Image](index.md)\> ||
| **Required** | no ||
| **Syntax** | SegmentRequired="*option*" |  |
| **Options** | Y | user must create a segmentation for this image|
|             | N |(default) no segmentation needs to be created for this image |
| **Dependencies** | [Layer](layer.md) | Not valid on Image elements with Layer="Segmentation" or Layer="Label" |
||[EnableSegmentEditor](../page/enable_segment_editor.md)||

## Description


!!! note
	If you need the user to create a segmentation on the same image presented in multiple viewing windows
	you must include the attribute in each of the duplicated XML image elements. The user only has to 
	create the segmentation on one of these viewing windows.
	
	This attribute is not applicable for images with the xml *Layer* element assigned to "Segmentation" or "Label". 

	See example below.


## Creating segmentations

To create a segmentation, the user needs to first select the Segment Editor tab and then
use the drop down box to select the image that the contour is to be associated with.
Once the master volume is selected, a few things happen:

- a labelmap file is created in the user's results folder.
    - This is located in a subfolder named with PgGroup#_PgID_PgDescriptor.
	- File name is constructed using ImageID_ImageDescriptor-quizlabel.nrrd

- a LabelMapPath xml element is added as a child to the Image element in the user's results xml file
so that the administrator has a reference to the stored labelmap file.

The contouring tools are located in the *Edit Selected Label Map* drop down section.
A restricted number of tools are available (paint, draw, erase, undo, redo, and change label number/color).

When the SegmentRequired attribute is assigned to an Image element,
the following rules must be true in order for the requirement to be fulfilled.

- If no labelmap previously existed for this image, one must be created.
    - An empty label map is not accepted.
- If a labelmap already existed (eg. redisplayed from a previous page using DisplayLabelMapID), modification of the label map is required.
    - The user must change the displayed labelmap using the Segment Editor tools.

See also the [how to contour](../../../user/contouring.md) link for more user specific instructions.

## Example

This example shows the MR T1 repeated in the Red and Yellow viewing windows and a segmentation
 is required on the T1 image but no segmentation is required on the T2 image. The  *SegmentRequired*
attribute is repeated for each viewing window.

```
<Session>
	<Page Descriptor="Brain-MR" ID="Patient1" EnableSegmentEditor="Y">
		<Image ID="MR T1" Type="Volume" SegmentRequired="Y">
			<Layer>Background</Layer>
			<DefaultDestination>Red</DefaultDestination>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\CT-MR Brain\MRBrainT1.nrrd</Path>
		</Image>
		<Image ID="MR T1" Type="Volume" SegmentRequired="Y">
			<Layer>Background</Layer>
			<DefaultDestination>Yellow</DefaultDestination>
			<DefaultOrientation>Coronal</DefaultOrientation>
			<Path>ImageVolumes\CT-MR Brain\MRBrainT1.nrrd</Path>
		</Image>
		<Image ID="MR T2" Type="Volume">
			<Layer>Background</Layer>
			<DefaultDestination>Green</DefaultDestination>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\CT-MR Brain\MRBrainT2.nrrd</Path>
		</Image>
	</Page>
</Session>
```