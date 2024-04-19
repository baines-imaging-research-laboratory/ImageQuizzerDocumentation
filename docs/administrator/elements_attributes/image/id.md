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
| **Associations** | [Page ID](../page/id.md) | uniqueness validation |
||[Path](path.md) | uniqueness validation |

## Description

The ID attribute must be unique for each image in the Page.
This allows for the administrator to load images into the foreground and background
layers of one viewing window. 

#### Uniqueness
The ID attribute for the Image is combined with the ID attribute
of the Page to create a unique node name when loaded into Slicer. 
There can be multiple Image elements within a Page with the same Path (e.g., one image
loaded into different viewing windows). Each of these elements must
have the same Image ID attribute. This is checked during quiz validation.




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