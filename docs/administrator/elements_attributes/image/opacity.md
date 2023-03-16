---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# Opacity

## Specs

| ||Details|
|---|---|:---:|
| **Name** | Opacity ||
| **Classification** | attribute ||
| **Parent** | <[Image](index.md)\> ||
| **Required** | no ||
| **Syntax** | Opacity="*value*" | value is a decimal between 0 and 1  |
| **Dependencies**| Layer="Foreground" | |

## Description

The opacity attribute is effective on an Image element that has been assigned to a Foreground layer.
This adjusts the visibility balance between the foreground and background images.
If no Opacity attribute is set for an image loaded into the foreground layer, the default is set to .5 .


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
		<Image ID="Unregistered" Type="Volume" Opacity=".3">
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