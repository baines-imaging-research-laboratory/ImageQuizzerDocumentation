---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# ROI visibility

This example shows how to set up the ROI elements and attributes to display regions of interest
based on the code set in ROIVisibilityCode attribute.

The main elements and attributes of interest used for this example include:

- [ROIs](../elements_attributes/image/rois/index.md)
- [ROIVisibilityCode](../elements_attributes/image/rois/roi_visibility_code.md)
- [ROI](../elements_attributes/image/rois/roi.md)
- [Type](../elements_attributes/image/type.md)
- [Layer](../elements_attributes/image/layer.md)
- [ContourVisibility](../elements_attributes/session/contour_visibility.md)


## Prep

Download and save Slicer's TinyPatient [sample data](sample_data.md#slicer-sample-datasets).

!!! note
    In order to access this dataset, you have to turn on the developer mode.
	Edit>Application Settings>Developer>Enable developer mode


Suggested folder structure to match script:
```
.
└─ ImageDatabase/
      └─ ImageVolumes/
          └─ TinyPatient/
                ├─ TinyPatient_CT.nrrd
				└─ TinyPatient_Segments.seg.nrrd
```



## Script example

The TinyPatient dataset used in this example holds two segments named: Tumor_Contour and Body_Contour.
The script example repeats the presentation of the image and modifies the visibility code. 
The ContourVisibility attribute has been set to "Fill".

Only when the code is set to *Select* or *Fill* is the <ROI/> subelement required.



```
<Session ContourVisibility="Fill">
	<Page ID="TinyPatient" Descriptor="ROI Visibility All">
		<Image Type="Volume" ID="CTSeries">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\TinyPatient\TinyPatient_CT.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="CTSeries">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Sagittal</DefaultOrientation>
			<Path>ImageVolumes\TinyPatient\TinyPatient_CT.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="CTSeries">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Coronal</DefaultOrientation>
			<Path>ImageVolumes\TinyPatient\TinyPatient_CT.nrrd</Path>
		</Image>
		<Image Type="Segmentation" ID="Segmentation">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Segmentation</Layer>
			<Path>ImageVolumes\TinyPatient\TinyPatient_Segments.seg.nrrd</Path>
			<ROIs ROIVisibilityCode="All"></ROIs>
		</Image>
		<Image Type="Segmentation" ID="Segmentation">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Segmentation</Layer>
			<Path>ImageVolumes\TinyPatient\TinyPatient_Segments.seg.nrrd</Path>
			<ROIs ROIVisibilityCode="All"></ROIs>
		</Image>
		<Image Type="Segmentation" ID="Segmentation">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Segmentation</Layer>
			<Path>ImageVolumes\TinyPatient\TinyPatient_Segments.seg.nrrd</Path>
			<ROIs ROIVisibilityCode="All"></ROIs>
		</Image>
		<QuestionSet ID="QS-Checkup" Descriptor="ROI Display">
			<Question Type="CheckBox" Descriptor="Code: All">
				<Option>Display all rois</Option>
			</Question>
		</QuestionSet>
	</Page>
	<Page ID="TinyPatient" Descriptor="ROI Visibility None">
		<Image Type="Volume" ID="CTSeries">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\TinyPatient\TinyPatient_CT.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="CTSeries">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Sagittal</DefaultOrientation>
			<Path>ImageVolumes\TinyPatient\TinyPatient_CT.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="CTSeries">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Coronal</DefaultOrientation>
			<Path>ImageVolumes\TinyPatient\TinyPatient_CT.nrrd</Path>
		</Image>
		<Image Type="Segmentation" ID="Segmentation">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Segmentation</Layer>
			<Path>ImageVolumes\TinyPatient\TinyPatient_Segments.seg.nrrd</Path>
			<ROIs ROIVisibilityCode="None"></ROIs>
		</Image>
		<Image Type="Segmentation" ID="Segmentation">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Segmentation</Layer>
			<Path>ImageVolumes\TinyPatient\TinyPatient_Segments.seg.nrrd</Path>
			<ROIs ROIVisibilityCode="None"></ROIs>
		</Image>
		<Image Type="Segmentation" ID="Segmentation">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Segmentation</Layer>
			<Path>ImageVolumes\TinyPatient\TinyPatient_Segments.seg.nrrd</Path>
			<ROIs ROIVisibilityCode="None"></ROIs>
		</Image>
		<QuestionSet ID="QS-Checkup" Descriptor="ROI Display">
			<Question Type="CheckBox" Descriptor="Code: None">
				<Option>Display no rois</Option>
			</Question>
		</QuestionSet>
	</Page>
	<Page ID="TinyPatient" Descriptor="ROI Visibility Select One ROI">
		<Image Type="Volume" ID="CTSeries">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\TinyPatient\TinyPatient_CT.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="CTSeries">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Sagittal</DefaultOrientation>
			<Path>ImageVolumes\TinyPatient\TinyPatient_CT.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="CTSeries">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Coronal</DefaultOrientation>
			<Path>ImageVolumes\TinyPatient\TinyPatient_CT.nrrd</Path>
		</Image>
		<Image Type="Segmentation" ID="Segmentation">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Segmentation</Layer>
			<Path>ImageVolumes\TinyPatient\TinyPatient_Segments.seg.nrrd</Path>
			<ROIs ROIVisibilityCode="Select">
				<ROI>Tumor_Contour</ROI>
			</ROIs>
		</Image>
		<Image Type="Segmentation" ID="Segmentation">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Segmentation</Layer>
			<Path>ImageVolumes\TinyPatient\TinyPatient_Segments.seg.nrrd</Path>
			<ROIs ROIVisibilityCode="Select">
				<ROI>Tumor_Contour</ROI>
			</ROIs>
		</Image>
		<Image Type="Segmentation" ID="Segmentation">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Segmentation</Layer>
			<Path>ImageVolumes\TinyPatient\TinyPatient_Segments.seg.nrrd</Path>
			<ROIs ROIVisibilityCode="Select">
				<ROI>Tumor_Contour</ROI>
			</ROIs>
		</Image>
		<QuestionSet ID="QS-Checkup" Descriptor="ROI Display">
			<Question Type="CheckBox" Descriptor="Code: Select">
				<Option>Display tumor contour</Option>
			</Question>
		</QuestionSet>
	</Page>
	<Page ID="TinyPatient" Descriptor="ROI Visibility Select Multiple ROIs">
		<Image Type="Volume" ID="CTSeries">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\TinyPatient\TinyPatient_CT.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="CTSeries">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Sagittal</DefaultOrientation>
			<Path>ImageVolumes\TinyPatient\TinyPatient_CT.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="CTSeries">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Coronal</DefaultOrientation>
			<Path>ImageVolumes\TinyPatient\TinyPatient_CT.nrrd</Path>
		</Image>
		<Image Type="Segmentation" ID="Segmentation">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Segmentation</Layer>
			<Path>ImageVolumes\TinyPatient\TinyPatient_Segments.seg.nrrd</Path>
			<ROIs ROIVisibilityCode="Select">
				<ROI>Body_Contour</ROI>
				<ROI>Tumor_Contour</ROI>
			</ROIs>
		</Image>
		<Image Type="Segmentation" ID="Segmentation">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Segmentation</Layer>
			<Path>ImageVolumes\TinyPatient\TinyPatient_Segments.seg.nrrd</Path>
			<ROIs ROIVisibilityCode="Select">
				<ROI>Body_Contour</ROI>
				<ROI>Tumor_Contour</ROI>
			</ROIs>
		</Image>
		<Image Type="Segmentation" ID="Segmentation">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Segmentation</Layer>
			<Path>ImageVolumes\TinyPatient\TinyPatient_Segments.seg.nrrd</Path>
			<ROIs ROIVisibilityCode="Select">
				<ROI>Body_Contour</ROI>
				<ROI>Tumor_Contour</ROI>
			</ROIs>
		</Image>
		<QuestionSet ID="QS-Checkup" Descriptor="ROI Display">
			<Question Type="CheckBox" Descriptor="Code: Select">
				<Option>Display tumor contour</Option>
				<Option>Display body contour </Option>
			</Question>
		</QuestionSet>
	</Page>
	<Page ID="TinyPatient" Descriptor="ROI Visibility Ignore">
		<Image Type="Volume" ID="CTSeries">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\TinyPatient\TinyPatient_CT.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="CTSeries">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Sagittal</DefaultOrientation>
			<Path>ImageVolumes\TinyPatient\TinyPatient_CT.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="CTSeries">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Coronal</DefaultOrientation>
			<Path>ImageVolumes\TinyPatient\TinyPatient_CT.nrrd</Path>
		</Image>
		<Image Type="Segmentation" ID="Segmentation">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Segmentation</Layer>
			<Path>ImageVolumes\TinyPatient\TinyPatient_Segments.seg.nrrd</Path>
			<ROIs ROIVisibilityCode="Ignore">
				<ROI>Body_Contour</ROI>
			</ROIs>
		</Image>
		<Image Type="Segmentation" ID="Segmentation">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Segmentation</Layer>
			<Path>ImageVolumes\TinyPatient\TinyPatient_Segments.seg.nrrd</Path>
			<ROIs ROIVisibilityCode="Ignore">
				<ROI>Body_Contour</ROI>
			</ROIs>
		</Image>
		<Image Type="Segmentation" ID="Segmentation">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Segmentation</Layer>
			<Path>ImageVolumes\TinyPatient\TinyPatient_Segments.seg.nrrd</Path>
			<ROIs ROIVisibilityCode="Ignore">
				<ROI>Body_Contour</ROI>
			</ROIs>
		</Image>
		<QuestionSet ID="QS-Checkup" Descriptor="ROI Display">
			<Question Type="CheckBox" Descriptor="Code: Ignore">
				<Option>Display tumor only - ignore body contour</Option>
			</Question>
		</QuestionSet>
	</Page>
</Session>

```

