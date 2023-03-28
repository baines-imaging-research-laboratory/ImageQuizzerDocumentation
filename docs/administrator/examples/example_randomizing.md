---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# Randomizing pages

Image Quizzer has the ability to automatically randomize the Pages that are presented to the observers.


To do this, two attributes are set up: 

1. [RandomizePageGroup](../elements_attributes/session/randomize_page_groups.md)
1. [PageGroup](../elements_attributes/page/pagegroup.md)

Any pages set up with PageGroup="0" will not be randomized and will always be the first pages to
be displayed in the quiz.

If the *RandomizePageGroup* attribute is set to "Y" but no *PageGroup* attributes are assigned,
the Image Quizzer will automatically add a *PageGroup* attribute to each Page and assign
numbers sequentially for the randomization.

The shuffled page group numbers are recorded in the observer's results file in the 
[RandomizedPageGroupIndices](../results.md#randomizedpagegroupindices) element.



## Prep

For the following example, we will be using a number of brain images that are available when you open Slicer.	

Download and save the following datasets as described in the [sample data](sample_data.md#slicer-sample-datasets) section.


- MRBrain Tumor1
- MRBrain Tumor2
- CT-MR Brain
- MRHead
 
Save each dataset to a subfolder under ImageVolumes/ as shown.

```
.
└─ ImageQuizzerData/
      └─ ImageVolumes/
          ├─ CT-MR Brain/
          ├─   ├─ CTBrain.nrrd
          ├─   ├─ MRBrainT1.nrrd
          ├─   └─ MRBrainT2.nrrd
          ├─ MRHead/
          ├─   └─ MRHead.nrrd
          ├─ MRBrainTumor1/
          ├─   ├─ MRBrainTumor1.nrrd
          ├─   └─ BaselineVolume.nrrd
          └─ MRBrainTumor2/
               └─ MRBrainTumor2.nrrd
```

## Script example

For this quiz example, we are setting up a quiz to look at brain images. It is important for this observer
study that each observer look at the images in a random order so that no information sharing occurs
between observers (i.e. no cheating!).

We have assigned the same PageGroup number to images that belong to the same patient. 
That way only the Pages that represent a different patient will be randomized.
This feature could be useful if doing a study that shows for example a pre-surgery and post-sugery
follow-up images that need to be displayed sequentially, but the patients themselves need to be shuffled.

We have also set up an introductory page with a PageGroup="0" assigned so that it will always
appear as the first Page displayed. This can be used to communicate general instructions for the
observer study that follows.

	

```
<Session RandomizePageGroups="Y">
	<Page ID="Intro" Descriptor="Brain image analysis" PageGroup="0">
		<QuestionSet ID="Instructions" Descriptor="First page">
			<Question Descriptor="User instructions:" Type="InfoBox">
				<Option>Pages with PageGroup="0" are not randomized.</Option>
				<Option>These always appear at the beginning of the quiz.</Option>
			</Question>
		</QuestionSet>
	</Page>
	<Page ID="PatientA" Descriptor="Grp1- Brain-Baseline"  Layout="OneUpRedSlice" PageGroup="1">
		<Image Type="Volume" ID="MR Baseline">
			<Layer>Background</Layer>
			<DefaultDestination>Red</DefaultDestination>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\MRBrainTumor1\MRBrainTumor1.nrrd</Path>
		</Image>
	</Page>
	<Page ID="PatientA" Descriptor="Grp1- Brain-MR" Layout="OneUpRedSlice" PageGroup="1">
		<Image Type="Volume" ID="MR Followup">
			<Layer>Background</Layer>
			<DefaultDestination>Red</DefaultDestination>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\MRBrainTumor1\MRBrainTumor1.nrrd</Path>
		</Image>
	</Page>
	<Page ID="PatientB" Descriptor="Grp2- Brain-MR" Layout="OneUpRedSlice" PageGroup="2">
		<Image Type="Volume" ID="MR">
			<Layer>Background</Layer>
			<DefaultDestination>Red</DefaultDestination>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\MRBrainTumor2\MRBrainTumor2.nrrd</Path>
		</Image>
	</Page>
	<Page ID="PatientC" Descriptor="Grp3- Brain-MR T1" Layout="OneUpRedSlice" PageGroup="3">
		<Image Type="Volume" ID="MR T1">
			<Layer>Background</Layer>
			<DefaultDestination>Red</DefaultDestination>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\CT-MR Brain\MRBrainT1.nrrd</Path>
		</Image>
	</Page>
	<Page ID="PatientC" Descriptor="Grp3- Brain-MR T2" Layout="OneUpRedSlice" PageGroup="3">
		<Image Type="Volume" ID="MR T2">
			<Layer>Background</Layer>
			<DefaultDestination>Red</DefaultDestination>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\CT-MR Brain\MRBrainT2.nrrd</Path>
		</Image>
	</Page>
	<Page ID="PatientC" Descriptor="Grp3- Brain-CT" Layout="OneUpRedSlice" PageGroup="3">
		<Image Type="Volume" ID="CT">
			<Layer>Background</Layer>
			<DefaultDestination>Red</DefaultDestination>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\CT-MR Brain\CTBrain.nrrd</Path>
		</Image>
	</Page>
	<Page ID="PatientD" Descriptor="Grp4- Brain-MR" Layout="OneUpRedSlice" PageGroup="4">
		<Image Type="Volume" ID="CT">
			<Layer>Background</Layer>
			<DefaultDestination>Red</DefaultDestination>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\MRHead\MRHead.nrrd</Path>
		</Image>
	</Page>
</Session>
```

After running this quiz, the element added into the [results quiz file](../results.md) may look like this:

```
		<RandomizedPageGroupIndices>0,4,2,3,1</RandomizedPageGroupIndices>
```

These indices define the order in which the Pages are displayed. They are set when
the user first logs in to the session. Each user will have a different set of indices.