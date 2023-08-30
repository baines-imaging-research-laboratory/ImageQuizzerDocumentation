---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->

# Gold standard - Learning tool

An application for the Image Quizzer is to use it as a educational tool. You can have a user contour
a lesion on one page and on the following page, display the user's contour along with a pre-defined gold
standard.


## Prep

A sample dataset is not currently available on Slicer that has a predefined tumor
segmentation so creating a gold standard has to be done manually in order for the 
example script to work.

Download and save Slicer's MRBrainTumor1 dataset as described in the [sample data](sample_data.md#slicer-sample-datasets) section.

Suggested folder structure to match script:


```

.
└─ ImageQuizzerData/
      └─ ImageVolumes/
          └─ MRBrainTumor1/
		       ├─ MRBrainTumor1.nrrd
               └─ MRBrainTumor1-GoldStandard.seg.nrrd   (created manually - not in download)

```

A pseudo gold standard file can be captured by running the following script in the Image Quizzer
up to the first page. Create a contour and then use Slicer's functionality in File>Save to 
capture the contour as a segmentation file (.seg.nrrd format), rename it and store it in the folder
as described above.



## Script example


```
<Session>
	<Page ID="Patient 1" Descriptor="Contouring Challenge" EnableSegmentEditor="Y" SegmentRequiredOnAnyImage="Y">
		<Image Type="Volume" ID="MR" RotateToAcquisition="Y" LabelMapID="MR_Contour" InitialSliceOffset="25">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\MRBrainTumor1\MRBrainTumor1.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="MR" RotateToAcquisition="Y" InitialSliceOffset="0.468">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Sagittal</DefaultOrientation>
			<Path>ImageVolumes\MRBrainTumor1\MRBrainTumor1.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="MR" RotateToAcquisition="Y" InitialSliceOffset="35.15">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Coronal</DefaultOrientation>
			<Path>ImageVolumes\MRBrainTumor1\MRBrainTumor1.nrrd</Path>
		</Image>
		<QuestionSet ID="Contouring Challenge" Descriptor="">
			<Question Type="InfoBox" Descriptor="Segmentation Instructions">
				<Option>Contour the tumor using the segment editor.</Option>
			</Question>
		</QuestionSet>
	</Page>
	<Page ID="Patient 1" Descriptor="Contouring Challenge"  EnableSegmentEditor="Y" SegmentRequiredOnAnyImage="Y">
		<Image Type="Volume" ID="MR" RotateToAcquisition="Y" DisplayLabelMapID="MR_Contour">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\MRBrainTumor1\MRBrainTumor1.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="MR" RotateToAcquisition="Y" DisplayLabelMapID="MR_Contour">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Sagittal</DefaultOrientation>
			<Path>ImageVolumes\MRBrainTumor1\MRBrainTumor1.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="MR" RotateToAcquisition="Y" DisplayLabelMapID="MR_Contour">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Coronal</DefaultOrientation>
			<Path>ImageVolumes\MRBrainTumor1\MRBrainTumor1.nrrd</Path>
		</Image>
		<Image Type="Segmentation" ID="Gold" RotateToAcquisition="Y">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Segmentation</Layer>
			<Path>ImageVolumes\MRBrainTumor1\MRBrainTumor1-GoldStandard.seg.nrrd</Path>
			<ROIs ROIVisibilityCode='All'></ROIs>
		</Image>
		<Image Type="Segmentation" ID="Gold" RotateToAcquisition="Y">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Segmentation</Layer>
			<Path>ImageVolumes\MRBrainTumor1\MRBrainTumor1-GoldStandard.seg.nrrd</Path>
			<ROIs ROIVisibilityCode='All'></ROIs>
		</Image>
		<Image Type="Segmentation" ID="Gold" RotateToAcquisition="Y">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Segmentation</Layer>
			<Path>ImageVolumes\MRBrainTumor1\MRBrainTumor1-GoldStandard.seg.nrrd</Path>
			<ROIs ROIVisibilityCode='All'></ROIs>
		</Image>
		<QuestionSet ID="Gold Standard Display" Descriptor="">
			<Question Type="InfoBox" Descriptor="Compare to gold standard">
				<Option>The gold standard is presented over the user's contour.</Option>
			</Question>
		</QuestionSet>
	</Page>
</Session>
```

