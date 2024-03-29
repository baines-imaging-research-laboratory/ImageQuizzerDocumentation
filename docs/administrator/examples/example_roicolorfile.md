---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# ROI Color File

This example shows the setup of a lung study where the user must segment two regions of interest.
When in the Segment Editor tab, only 2 colors options are presented to the user.

The main attributes of interest used for this example include:

- ROIColorFile="Lung_SABR_Study_colors"
    - an attribute in the Session root element
	- name of the file holding color rgba definition
	- there is no .txt extension in this attribute
- EnableSegmentEditor="Y"
    - an attribute of the Page element
    - to open the Segment Editor tab in the Image Quizzer
- SegmentRequiredOnAnyImage="Y"
    - an attribute of the Page element
    - the user cannot advance to the next Page of images and questions until
	a contour has been created on any of the images displayed
	


## Prep

Download and save Slicer's CTChest [sample data](sample_data.md#slicer-sample-datasets).


Suggested folder structure to match script:
```
.
└─ ImageDatabase/
      └─ ImageVolumes/
          └─ CTChest/
                └─ CTChest.nrrd
```


## Create color file

Create the color text file.
Format: roi# roiName red green blue alpha

Place this file in the same directory where the master quiz file is located.

```
Lung_SABR_Study_colors.txt

1 Ground_glass_opacity_(GGO) 241 214 145 255
2 Consolidative_region 191 2 34 255

```

## Script example

```
Lung_SABR.xml

<Session ROIColorFile="Lung_SABR_Study_colors"
	<Page ID="Patient 1" Descriptor="Lung SABR Study" EnableSegmentEditor="Y" SegmentRequiredOnAnyImage="Y">
		<Image ID="CT" Type="Volume">
				<DefaultDestination>Red</DefaultDestination>
				<Layer>Background</Layer>
				<DefaultOrientation>Axial</DefaultOrientation>
				<Path>ImageVolumes\CTChest\CTChest.nrrd</Path>
		</Image>
		<Image ID="CT" Type="Volume">
				<DefaultDestination>Green</DefaultDestination>
				<Layer>Background</Layer>
				<DefaultOrientation>Sagittal</DefaultOrientation>
				<Path>ImageVolumes\CTChest\CTChest.nrrd</Path>
		</Image>
		<Image ID="CT" Type="Volume">
				<DefaultDestination>Yellow</DefaultDestination>
				<Layer>Background</Layer>
				<DefaultOrientation>Coronal</DefaultOrientation>
				<Path>ImageVolumes\CTChest\CTChest.nrrd</Path>
		</Image>
		<QuestionSet Descriptor="Lung SABR Study">
			<Question Descriptor="Assessment" Type="Radio">
				<Option>Injury</Option>
				<Option>Local recurrence</Option>
			</Question>
		</QuestionSet>
	</Page>
</Session>
```

## Display results

```
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
```
Screenshot of quiz options:

![Quiz radio button options](assets/Example_ROIColorFile_Quiz.png)

```
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
```

Screenshot of ROI color options

Popup window shows available colors. Access by clicking on the color bar.

![Segment color options](assets/Example_ROIColorFile_SegmentColors.png)



## See also

Scripting references section:

- [ROIColorFile](../elements_attributes/session/roi_colorfile.md)
- [EnableSegmentEditor](../elements_attributes/page/enable_segment_editor.md)
- [SegmentRequiredOnAnyImage](../elements_attributes/page/segment_required_on_any_image.md)


## References:

Parts of this example are based on a previous observer study carried out in our lab.

<div class="csl-entry">Mattonen, S. A., Palma, D. A., Johnson, C., Louie, A. v, Landis, M., Rodrigues, G., Chan, I., Etemad-rezai, R., Yeung, T. P. C., Senan, S., &#38; Ward, A. D. (2015). Detection of Local Cancer Recurrence After Stereotactic Ablative Radiation Therapy for Lung Cancer : Physician Performance Versus Radiomic Assessment. <i>Radiation Oncology Biology</i>. https://doi.org/10.1016/j.ijrobp.2015.12.369</div>