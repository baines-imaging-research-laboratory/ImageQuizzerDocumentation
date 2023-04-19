---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# Rotate to acquisition

This example focuses on [RotateToAcquisition](../elements_attributes/image/rotate_to_acquisition.md) (an attribute for the Image element).
Also included is the [LinkViews](../elements_attributes/page/link_views.md) (an attribute for the Page element)
attribute to demonstrate their basic functionality and how they may conflict with each other.

Using the RotateToAcquisition attribute on an Image element, you can have an image
displayed immediately in the frame of reference that the volume was acquired. The default
is to display the image according to the anatomical coordinate system (Axial, Sagittal and Coronal).

The LinkViews attribute allows the user to scroll through the slices on one image view and 
have the other views scroll as well.

## Prep

For the following example, we will use the CT-MR Brain sample dataset that is available when you open Slicer.	

Download and save the dataset as described in the [sample data](sample_data.md#slicer-sample-datasets) section
to a subfolder under ImageVolumes folder as shown.

```
.
└─ ImageQuizzerData/
      └─ ImageVolumes/
          └─ CT-MR Brain/
               ├─ CTBrain.nrrd
               ├─ MRBrainT1.nrrd
               └─ MRBrainT2.nrrd
```

## Script example

This script has three pages each with the EnableSegmentEditor attribute set to "Y".

The first page uses the LinkViews attribute and the images do not
use the RotateToAcquisition attribute. You should be able to scroll through the slices on one view and
have the other views also scroll as well. If you go to the Segment Editor tab and set the Master Volume 
to any of the loaded images, you should see the image 'snap' to the acquisition orientation.

The second page does not use the LinkViews attribute, but the images are set with the RotateToAcquisition attribute set to "Y".
Now if you go to the Segment Editor tab and assign one of the loaded images to the Master Volume, there will
be no 'snap' rotation as the image is already in the acquired orientation.

The third page uses both the LinkViews and RotateToAcquisition attributes. If you try to scroll
through any of the images, the others do not scroll as well since they were each acquired at a slightly 
different angle.





```
<Session>
	<Page Descriptor="Brain CT-MR" ID="Patient1" EnableSegmentEditor="Y" LinkViews="Y">
		<Image ID="MR T1" Type="Volume">
			<Layer>Background</Layer>
			<DefaultDestination>Yellow</DefaultDestination>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\CT-MR Brain\MRBrainT1.nrrd</Path>
		</Image>
		<Image ID="MR T2" Type="Volume">
			<Layer>Background</Layer>
			<DefaultDestination>Green</DefaultDestination>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\CT-MR Brain\MRBrainT2.nrrd</Path>
		</Image>
		<Image ID="CT" Type="Volume">
			<Layer>Background</Layer>
			<DefaultDestination>Red</DefaultDestination>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\CT-MR Brain\CTBrain.nrrd</Path>
		</Image>
		<QuestionSet ID="Create contours" Descriptor="">
			<Question Type="InfoBox" Descriptor="Attributes">
				<Option>LinkViews="Y"</Option>
				<Option>RotateToAcquisition="N" (attribute is absent)</Option>
			</Question>
			<Question Type="InfoBox" Descriptor="Contouring Instructions">
				<Option>In Segment Editor tab, select volume to create contours.</Option>
				<Option>   In Edit label map dropdown, use available tools to contour region of interest.</Option>
			</Question>
			<Question Type="CheckBox" Descriptor="Functionality">
				<Option>Images should scroll together</Option>
				<Option>Images should 'snap' to acquired axis for segmenting</Option>
			</Question>
		</QuestionSet>
	</Page>
	<Page Descriptor="Brain CT-MR" ID="Patient2" EnableSegmentEditor="Y">
		<Image ID="MR T2" Type="Volume" RotateToAcquisition="Y">
			<Layer>Background</Layer>
			<DefaultDestination>Green</DefaultDestination>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\CT-MR Brain\MRBrainT2.nrrd</Path>
		</Image>
		<Image ID="MR T1" Type="Volume" RotateToAcquisition="Y">
			<Layer>Background</Layer>
			<DefaultDestination>Yellow</DefaultDestination>
			<DefaultOrientation>Coronal</DefaultOrientation>
			<Path>ImageVolumes\CT-MR Brain\MRBrainT1.nrrd</Path>
		</Image>
		<Image ID="CT" Type="Volume" RotateToAcquisition="Y">
			<Layer>Background</Layer>
			<DefaultDestination>Red</DefaultDestination>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\CT-MR Brain\CTBrain.nrrd</Path>
		</Image>
		<QuestionSet ID="Create contours" Descriptor="">
			<Question Type="InfoBox" Descriptor="Attributes">
				<Option>LinkViews="N" (attribute is absent)</Option>
				<Option>RotateToAcquisition="Y"</Option>
			</Question>
			<Question Type="InfoBox" Descriptor="Contouring Instructions">
				<Option>In Segment Editor tab, select volume to create contours.</Option>
				<Option>   In Edit label map dropdown, use available tools to contour region of interest.</Option>
			</Question>
			<Question Type="CheckBox" Descriptor="Functionality">
				<Option>Images don't scroll together</Option>
				<Option>Images do not rotate when segmenting - already in acquisition orientation</Option>
			</Question>
		</QuestionSet>
	</Page>
	<Page Descriptor="Brain CT-MR" ID="Patient3" EnableSegmentEditor="Y" LinkViews="Y">
		<Image ID="MR T1" Type="Volume" RotateToAcquisition="Y">
			<Layer>Background</Layer>
			<DefaultDestination>Yellow</DefaultDestination>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\CT-MR Brain\MRBrainT1.nrrd</Path>
		</Image>
		<Image ID="MR T2" Type="Volume" RotateToAcquisition="Y">
			<Layer>Background</Layer>
			<DefaultDestination>Green</DefaultDestination>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\CT-MR Brain\MRBrainT2.nrrd</Path>
		</Image>
		<Image ID="CT" Type="Volume" RotateToAcquisition="Y">
			<Layer>Background</Layer>
			<DefaultDestination>Red</DefaultDestination>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\CT-MR Brain\CTBrain.nrrd</Path>
		</Image>
		<QuestionSet ID="Create contours" Descriptor="">
			<Question Type="InfoBox" Descriptor="Attributes">
				<Option>LinkViews="Y"</Option>
				<Option>RotateToAcquisition="Y"</Option>
			</Question>
			<Question Type="InfoBox" Descriptor="Contouring Instructions">
				<Option>In Segment Editor tab, select volume to create contours.</Option>
				<Option>   In Edit label map dropdown, use available tools to contour region of interest.</Option>
			</Question>
			<Question Type="CheckBox" Descriptor="Functionality">
				<Option>Images don't scroll together even with LinkViews set to "Y"</Option>
				<Option>Images do not rotate when segmenting - already in acquisition orientation</Option>
			</Question>
		</QuestionSet>
	</Page>
</Session>


```
## See also



