---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# ROIs from RTStruct dicom

This example shows Volume and RTStruct types of images loaded from dicom files.
The RTStruct containes two ROIs. Only the "Tumor" contour is selected to be displayed.

The main elements and attributes of interest used for this example include:

- [ROIs](../elements_attributes/image/rois/index.md)
- [ROIVisibilityCode](../elements_attributes/image/rois/roi_visibility_code.md)
- [ROI](../elements_attributes/image/rois/roi.md)
- [Type](../elements_attributes/image/type.md)
- [Layer](../elements_attributes/image/layer.md)


## Prep
The example script is based on a version of the TinyPatient dataset converted to DICOM format.


Download and save Slicer's TinyPatient [sample data](sample_data.md#slicer-sample-datasets).
Slicer can be used to load these images and then saved in dicom format using the **Create a DICOM Series** module.

!!! note
    In order to access this dataset, you have to turn on the developer mode.
	Edit>Application Settings>Developer>Enable developer mode
	
	


Suggested folder structure to match script:
```
.
└─ ImageDatabase/
      └─ ImageVolumes/
          └─ TinyPatient/
                ├─ image0000.dcm
                ├─ image0001.dcm
                ├─ image0002.dcm
                ├─ ...
                ├─ 
				└─ rtss.dcm
```






## Script example

The RTStruct file contains two ROIs. Only Tumor_Contour is selected to be displayed.
See [ROI Visibility](./example_roi_visibility.md#script-example) for more ROI selection options.


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
		<QuestionSet></QuestionSet>
	</Page>
</Session>
```

