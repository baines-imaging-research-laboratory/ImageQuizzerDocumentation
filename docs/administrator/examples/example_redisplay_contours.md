---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# Redisplay contours

The Image Quizzer enables you to have the user create a contour for an image in one page and
have that contour redisplayed on the same image in a subsequent page.
This can be useful for comparing the user's contour with a gold standard.


## Prep

Download the RECIST-dataset as described in the [sample data](sample_data.md#tutorial-data-links) section.

Extract the RECIST-Tutorial-Data to a subfolder under ImageVolumes/ as shown.

```
.
└─ ImageQuizzerData/
      └─ ImageVolumes/
          └─ RECIST-Tutorial-Data/
              ├─ 2006-spgr.nrrd
              ├─ 2006-spgr-label.nrrd
              ├─ 2007-spgr.nrrd
              ├─ 2007-spgr.label.nrrd
			  └─ ...
```

## Script example

This example has the user create a contour for the tumor for two patients. 
Then the gold standard is displayed for the same two patients with the user's contour overlaid.

The same image is defined here in different orientations. 
The LabelMapID attribute needs to be set up on only one instance.
However, the DisplayLabelMapID attribute needs to be set up on each instance.

The gold standard label map is loaded onto the Segmentation layer.
This layer requires the element <ROIs/> element to be defined.
It has been set to display all stored contours.


```
<Session>
	<Page ID="Patient1" Descriptor="Create contours" EnableSegmentEditor="Y">
		<Image Type="Volume" ID="MR" RotateToAcquisition="Y" SegmentRequired="Y" LabelMapID="Patient1-contour">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\RECIST-Tutorial-Data\2006-spgr.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="MR" RotateToAcquisition="Y" SegmentRequired="Y">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Sagittal</DefaultOrientation>
			<Path>ImageVolumes\RECIST-Tutorial-Data\2006-spgr.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="MR" RotateToAcquisition="Y" SegmentRequired="Y">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Coronal</DefaultOrientation>
			<Path>ImageVolumes\RECIST-Tutorial-Data\2006-spgr.nrrd</Path>
		</Image>
		<QuestionSet ID="Create contours" Descriptor="">
			<Question Type="InfoBox" Descriptor="Contouring Instructions">
				<Option>In Segment Editor tab, select volume to create contours.</Option>
				<Option>   In Edit label map dropdown, use available tools to contour region of interest.</Option>
			</Question>
		</QuestionSet>
	</Page>
	<Page ID="Patient2" Descriptor="Create contours" EnableSegmentEditor="Y">
		<Image Type="Volume" ID="MR" RotateToAcquisition="Y" SegmentRequired="Y" LabelMapID="Patient2-contour">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\RECIST-Tutorial-Data\2007-spgr.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="MR" RotateToAcquisition="Y" SegmentRequired="Y">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Sagittal</DefaultOrientation>
			<Path>ImageVolumes\RECIST-Tutorial-Data\2007-spgr.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="MR" RotateToAcquisition="Y" SegmentRequired="Y">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Coronal</DefaultOrientation>
			<Path>ImageVolumes\RECIST-Tutorial-Data\2007-spgr.nrrd</Path>
		</Image>
		<QuestionSet ID="Create contours" Descriptor="">
			<Question Type="InfoBox" Descriptor="Contouring Instructions">
				<Option>In Segment Editor tab, select volume to create contours.</Option>
				<Option>   In Edit label map dropdown, use available tools to contour region of interest.</Option>
			</Question>
		</QuestionSet>
	</Page>
	<Page ID="Patient1" Descriptor="Compare to gold standard">
		<Image Type="Volume" ID="MR" RotateToAcquisition="Y" DisplayLabelMapID="Patient1-contour">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\RECIST-Tutorial-Data\2006-spgr.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="MR" RotateToAcquisition="Y" DisplayLabelMapID="Patient1-contour">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Sagittal</DefaultOrientation>
			<Path>ImageVolumes\RECIST-Tutorial-Data\2006-spgr.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="MR" RotateToAcquisition="Y" DisplayLabelMapID="Patient1-contour">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Coronal</DefaultOrientation>
			<Path>ImageVolumes\RECIST-Tutorial-Data\2006-spgr.nrrd</Path>
		</Image>
		<Image Type="Segmentation" ID="Gold standard">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Segmentation</Layer>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\RECIST-Tutorial-Data\2006-spgr-label.nrrd</Path>
			<ROIs ROIVisibilityCode='All'></ROIs>
		</Image>
		<Image Type="Segmentation" ID="Gold standard">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Segmentation</Layer>
			<DefaultOrientation>Sagittal</DefaultOrientation>
			<Path>ImageVolumes\RECIST-Tutorial-Data\2006-spgr-label.nrrd</Path>
			<ROIs ROIVisibilityCode='All'></ROIs>
		</Image>
		<Image Type="Segmentation" ID="Gold standard">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Segmentation</Layer>
			<DefaultOrientation>Coronal</DefaultOrientation>
			<Path>ImageVolumes\RECIST-Tutorial-Data\2006-spgr-label.nrrd</Path>
			<ROIs ROIVisibilityCode='All'></ROIs>
		</Image>
		<QuestionSet ID="Comparison" Descriptor="User with gold standard">
			<Question Type="InfoBox" Descriptor="Comparison">
				<Option>Gold standard contour is displayed with user's contour</Option>
			</Question>
		</QuestionSet>
	</Page>
	<Page ID="Patien2" Descriptor="Compare to gold standard">
		<Image Type="Volume" ID="MR" RotateToAcquisition="Y" DisplayLabelMapID="Patient2-contour">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\RECIST-Tutorial-Data\2007-spgr.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="MR" RotateToAcquisition="Y" DisplayLabelMapID="Patient2-contour">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Sagittal</DefaultOrientation>
			<Path>ImageVolumes\RECIST-Tutorial-Data\2007-spgr.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="MR" RotateToAcquisition="Y" DisplayLabelMapID="Patient2-contour">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Coronal</DefaultOrientation>
			<Path>ImageVolumes\RECIST-Tutorial-Data\2007-spgr.nrrd</Path>
		</Image>
		<Image Type="Segmentation" ID="Gold standard">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Segmentation</Layer>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\RECIST-Tutorial-Data\2007-spgr.label.nrrd</Path>
			<ROIs ROIVisibilityCode='All'></ROIs>
		</Image>
		<Image Type="Segmentation" ID="Gold standard">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Segmentation</Layer>
			<DefaultOrientation>Sagittal</DefaultOrientation>
			<Path>ImageVolumes\RECIST-Tutorial-Data\2007-spgr.label.nrrd</Path>
			<ROIs ROIVisibilityCode='All'></ROIs>
		</Image>
		<Image Type="Segmentation" ID="Gold standard">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Segmentation</Layer>
			<DefaultOrientation>Coronal</DefaultOrientation>
			<Path>ImageVolumes\RECIST-Tutorial-Data\2007-spgr.label.nrrd</Path>
			<ROIs ROIVisibilityCode='All'></ROIs>
		</Image>
		<QuestionSet ID="Comparison" Descriptor="User with gold standard">
			<Question Type="InfoBox" Descriptor="Comparison">
				<Option>Gold standard contour is displayed with user's contour</Option>
			</Question>
		</QuestionSet>
	</Page>
</Session>
```