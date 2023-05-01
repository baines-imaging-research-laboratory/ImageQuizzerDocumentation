---
hide:
- toc
---
# Type

## Specs

| ||Details|
|---|---|---|
| **Name** | Type ||
| **Classification** | attribute ||
| **Parent** | <[Image](index.md)\> ||
| **Required** | yes ||
| **Syntax** | Type="*option*" |  |
| **Options** | Volume | load as scalar volume object |
|             | VolumeSequence | load 4D image as sequence volume object|
|             | LabelMap | load ROIs mask file on Label layer (for discrete values) |
|             | Segmentation | load ROIs as segmentation object |
|             | RTStruct | load DICOM ROIs as segmentation object |
| **Dependencies** | for 4D volumes | see VolumeSequence notes below |
|  | for Segmentation or RTStruct  | see Segmentation and RTStruct notes below |



## Description

The Type attribute for an Image element defines how to load the image or region of interest (ROI) into Slicer.

### Images volumes

2D or 3D images can be loaded as a scalar volume using Type="Volume".
4D images are loaded using Type="VolumeSequence". This will activate the sequence controls
to play the time series.

!!! Note "VolumeSequence"

    * When loading a 4D volume, 
	the preferred method of loading a multivolume must be set to *volumesequence* in order for the controls to be activated
	to play the series.
	This is described when installing 3D Slicer [Application settings](../../../getting_started/index.md#3d-slicer).
	
	* If the volume sequence being loaded is in DICOM format, the DICOM slices for all time points must be located
	in the same folder (no subfolders).

### Regions of interest (ROIs)

By using Type="LabelMap", Type="Segmentation" or Type="RTStruct" you have the flexibility of displaying these ROI image files
layered over the images that were loaded into the background and foreground. 

ROIs can be stored in a variety of formats. 
ROIs stored as discrete values (mask) are loaded as Type="LabelMap".
ROIs stored in segmentation or RTStruct files are loaded as Type="Segmentation" or Type="RTStruct" respectively.

!!! note "Segmentation and RTStruct"
	* Segmentation and RTStruct type images must have an [ROIs](rois/index.md) element defined.
	* ROIs stored in an RTStruct file must also have the DICOM="Y" attribute set in the Image element.



## Examples

### VolumeSequence

For an example of loading 4D images as Type="VolumeSequence" see the script example in [4D VolumeSequence](../../examples/example_volumesequence.md)

### Segmentation

For an example of loading images as Type="Segmentation" see the script example in [ROI Visibility](../../examples/example_roi_visibility.md#script-example)

### RTStruct

Example showing Volume and RTStruct types.
RTStruct file contains two ROIs. Only Tumor-contour is selected to be displayed.

(This script is based on a version of the TinyPatient dataset converted to DICOM format.)

```
<Session>
	<Page ID="TinyPatient" Descriptor="DicomSeries with RTStruct">
		<Image DicomRead="Y" Type="Volume" ID="CTSeries">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\TinyPatient\image0000.dcm</Path>
		</Image>
		<Image DicomRead="Y" Type="Volume" ID="CTSeries">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Sagittal</DefaultOrientation>
			<Path>ImageVolumes\TinyPatient\image0000.dcm</Path>
		</Image>
		<Image DicomRead="Y" Type="Volume" ID="CTSeries">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Coronal</DefaultOrientation>
			<Path>ImageVolumes\TinyPatient\image0000.dcm</Path>
		</Image>
		<Image DicomRead="Y" Type="RTStruct" ID="ROI">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Segmentation</Layer>
			<Path>ImageVolumes\TinyPatient\rtss.dcm</Path>
			<ROIs ROIVisibilityCode="Select">
			<ROI>Tumor_Contour</ROI>
			</ROIs>
		</Image>
		<Image DicomRead="Y" Type="RTStruct" ID="ROI">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Segmentation</Layer>
			<Path>ImageVolumes\TinyPatient\rtss.dcm</Path>
			<ROIs ROIVisibilityCode="Select">
				<ROI>Tumor_Contour</ROI>
			</ROIs>
		</Image>
		<Image DicomRead="Y" Type="RTStruct" ID="ROI">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Segmentation</Layer>
			<Path>ImageVolumes\TinyPatient\rtss.dcm</Path>
			<ROIs ROIVisibilityCode="Select">
				<ROI>Tumor_Contour</ROI>
			</ROIs>
		</Image>
	</Page>
</Session>
```


