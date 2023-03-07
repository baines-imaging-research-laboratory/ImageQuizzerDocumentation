---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# ID

## Specs

| ||Details|
|---|---|:---:|
| **Name** | ID ||
| **Classification** | attribute ||
| **Parent** | <[Image](index.md)\> ||
| **Required** | yes ||
| **Syntax** | ID="*string*" |  |

## Description

The ID attribute must be unique for each image in the Page.
This allows for the administrator to load images into the foreground and background
layers of one viewing window. 

Also, the ID attribute for the Image is combined with the ID attribute
of the Page to create a unique node name when loaded into Slicer.

!!! Warning
    If the same image is loaded into different viewing destinations, **they must have
    the same ID**. 


## Example
```
<Session>
	<Page ID="Patient1" Descriptor="PlanningCT" >
		<Image Type="Volume" ID="Fixed Volume" LabelMapID="Brain-fixed-contour">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\Brain\BrainCT_fixed.nrrd</Path>
		</Image>
		<Image ID="Unregistered" Type="Volume" Opacity="15">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Foreground</Layer>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\Brain\BrainCT_moving.nii</Path>
		</Image>
		<Image Type="Volume" ID="Fixed Volume">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Sagittal</DefaultOrientation>
			<Path>ImageVolumes\Brain\BrainCT_fixed.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="Fixed Volume">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Coronal</DefaultOrientation>
			<Path>ImageVolumes\Brain\BrainCT_fixed.nrrd</Path>
		</Image>
	</Page>
</Session>
```