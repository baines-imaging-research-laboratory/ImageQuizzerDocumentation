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
|             | Vector | load single picture type of file |
|             | LabelMap | load ROIs mask file on Label layer (for discrete values) |
|             | Segmentation | load ROIs as segmentation object |
|             | RTStruct | load DICOM ROIs as segmentation object |
| **Dependencies** | for 4D volumes | see VolumeSequence notes below |
|  | for Segmentation or RTStruct  | see Segmentation and RTStruct notes below |
|  | <[Layer](layer.md)\>| restrictions for each Type option notes below|



## Description

The Type attribute for an Image element defines how to load the image or region of interest (ROI) into Slicer.

### Images volumes

2D or 3D images can be loaded as a scalar volume using Type="Volume".
4D images are loaded using Type="VolumeSequence". This will activate the sequence controls
to play the time series. These types can be assigned to the 'Foreground' or 'Background' Layer element.

!!! Note "VolumeSequence"

    * When loading a 4D volume, 
	the preferred method of loading a multivolume must be set to *volumesequence* in order for the controls to be activated
	to play the series.
	This is described when installing 3D Slicer [Application settings](../../../getting_started/index.md#3d-slicer).
	
	* If the volume sequence being loaded is in DICOM format, the DICOM slices for all time points must be located
	in the same folder (no subfolders).

### Vector

Single picture type images should be loaded as Type="Vector". These include images formatted as PNG, BMP, JPG, JPEG, and PDF.
Also accepted are single slice DCM images (eg. histology slice saved as a dicom image). This type can be assigned to the
 only to the 'Background' Layer element.
 
### LabelMap, Segmentation and RTStruct

By using Type="LabelMap", Type="Segmentation" or Type="RTStruct" you have the flexibility of displaying these ROI image files
layered over the images that were loaded into the background and foreground. 

#### Regions of interest (ROIs)

ROIs can be stored in a variety of image file formats. 

!!! note "LabelMap"
	* Image files have ROIs stored as discrete values (mask) are loaded as Type="LabelMap".
	* This type must be assigned to Layer="Label"

!!! note "Segmentation and RTStruct"
	* ROIs stored in segmentation or RTStruct files are loaded as Type="Segmentation" or Type="RTStruct" respectively. 
	* Segmentation and RTStruct type images must have an [ROIs](rois/index.md) element defined.
	* ROIs stored in an RTStruct file must also have the DICOM="Y" attribute set in the Image element.
	* These types must be assigned to the Layer="Segmentation".


## Examples

### VolumeSequence

For an example of loading 4D images as Type="VolumeSequence" see the script example in [4D VolumeSequence](../../examples/example_volumesequence.md)


### Segmentation

For an example of loading images as Type="Segmentation" see the script example in [ROI Visibility](../../examples/example_roi_visibility.md#script-example)

### RTStruct - dicom format

For an example showing Volume and RTStruct types of images see the script example in  [ROI - RTStruct](../../examples/example_rtstruct.md#script-example).
