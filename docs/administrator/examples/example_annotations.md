---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# Annotations (contours and markup lines)

Through the scripting attributes, the administrator can define on which images the user
is required to create segmentations or markup lines.

A segmentation (also referred to as a contour) is created using the Segment Editor tab. The
resulting contours are stored as label maps in a file with a .nrrd extension.

Attributes associated with creating segmentations include:

| Element | Attribute |
|---------|-----------|
|Page | [EnableSegmentEditor](../elements_attributes/page/enable_segment_editor.md) |
| | [SegmentationRequiredOnAnyImage](../elements_attributes/page/segment_required_on_any_image.md) |
| Image | [SegmentRequired](../elements_attributes/image/segment_required.md) |

A markup line captures the length between two points selected by the user.
The lines can be added using the Line Measurement Ruler tool in the Extra Tools tab.
The results are stored in a file with the .mrk.json extension.

Attributes associated with creating markup lines include:

| Element | Attribute |
|---------|-----------|
|Page | [MinMarkupLinesRequiredOnAnyImage](../elements_attributes/page/min_markuplines_required_on_any_image.md) |
| Image | [MinMarkupLinesRequired](../elements_attributes/image/min_markuplines_required.md) |


User documentation on how to create these annotations can be found here:

- [How to contour](../../user/contouring.md)
- [Create line measuremets](../../user/extratools.md#line-measurement)





## Prep

For the following example, we will use the CT-MR Brain sample dataset that is available when you open Slicer.	

Download and save the dataset as described in the [sample data](sample_data.md#slicer-sample-datasets) section
to a subfolder under ImageVolumes folder as shown.

```
.
└─ ImageDatabase/
	└─ ImageVolumes/
		└─ CT-MR Brain/
			├─ CTBrain.nrrd
			├─ MRBrainT1.nrrd
			└─ MRBrainT2.nrrd
```

## Script example

For this quiz example, there are 3 pages set up. Each one has different annotation requirements.

In the first page (Patient1), the user would be allowed to contour on any of the images presented as well as to
create a markup measurement line on any image. They will not be allowed to proceed until there is at least
one markup line created and at least one labelmap that has a valid contour (cannot be empty - or all pixels equal to zero).

The second page (Patient2) has a layout defined as TwoOverTwo. The MR-T2 and CT images are displayed 
in Axial and Coronal views. The user is required to create a contour on the MR-T2 image and a markup line 
on the CT image. Because these images are each presented in more than one viewing window, the
attributes must be repeated for each window. The MR-T2 image also has the attribute "LabelMapID" set
so that the contour can be redisplayed on Page 3.

The third page (Patient3) shows all three images in the Axial view. The MR-T2 image is set to redisplay the
segmentation created on page 2 but also has the attribute SegmentationRequired="Y". This means that
the user must either create a new segmentation on the MR-T2 image, or modify the existing segmentation 
before being allowed to finish and exit the quiz. The user is also required to create 2 markup measurement lines on the MR-T1.




```
<Session>
	<Page Descriptor="Brain CT-MR" ID="Patient1" EnableSegmentEditor="Y" SegmentRequiredOnAnyImage="Y" MinMarkupLinesRequiredOnAnyImage="1">
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
			<Question Type="InfoBox" Descriptor="Contouring Instructions">
				<Option>In Segment Editor tab, select volume to create contours.</Option>
				<Option>   In Edit label map dropdown, use available tools to contour region of interest.</Option>
			</Question>
			<Question Type="InfoBox" Descriptor="Annotations Required">
				<Option>Segment on any image</Option>
				<Option>One markup line on any image</Option>
			</Question>
		</QuestionSet>
	</Page>
	<Page Descriptor="Brain CT-MR" ID="Patient2" EnableSegmentEditor="Y" Layout="TwoOverTwo">
		<Image ID="MR T2" Type="Volume" SegmentRequired="Y" LabelMapID="MR-T2 Contour">
			<Layer>Background</Layer>
			<DefaultDestination>Green</DefaultDestination>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\CT-MR Brain\MRBrainT2.nrrd</Path>
		</Image>
		<Image ID="MR T2" Type="Volume" SegmentRequired="Y">
			<Layer>Background</Layer>
			<DefaultDestination>Yellow</DefaultDestination>
			<DefaultOrientation>Coronal</DefaultOrientation>
			<Path>ImageVolumes\CT-MR Brain\MRBrainT2.nrrd</Path>
		</Image>
		<Image ID="CT" Type="Volume" MinMarkupLinesRequired="1">
			<Layer>Background</Layer>
			<DefaultDestination>Red</DefaultDestination>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\CT-MR Brain\CTBrain.nrrd</Path>
		</Image>
		<Image ID="CT" Type="Volume" MinMarkupLinesRequired="1">
			<Layer>Background</Layer>
			<DefaultDestination>Slice4</DefaultDestination>
			<DefaultOrientation>Coronal</DefaultOrientation>
			<Path>ImageVolumes\CT-MR Brain\CTBrain.nrrd</Path>
		</Image>
		<QuestionSet ID="Create contours" Descriptor="">
			<Question Type="InfoBox" Descriptor="Contouring Instructions">
				<Option>In Segment Editor tab, select volume to create contours.</Option>
				<Option>   In Edit label map dropdown, use available tools to contour region of interest.</Option>
			</Question>
			<Question Type="InfoBox" Descriptor="Annotations Required">
				<Option>Segment on MR-T2</Option>
				<Option>One markup line CT</Option>
			</Question>
		</QuestionSet>
	</Page>
	<Page Descriptor="Brain CT-MR" ID="Patient3" EnableSegmentEditor="Y">
		<Image ID="MR T1" Type="Volume" MinMarkupLinesRequired="2">
			<Layer>Background</Layer>
			<DefaultDestination>Yellow</DefaultDestination>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\CT-MR Brain\MRBrainT1.nrrd</Path>
		</Image>
		<Image ID="MR T2" Type="Volume" SegmentRequired="Y" DisplayLabelMapID="MR-T2 Contour">
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
			<Question Type="InfoBox" Descriptor="Contouring Instructions">
				<Option>In Segment Editor tab, select volume to create contours.</Option>
				<Option>   In Edit label map dropdown, use available tools to contour region of interest.</Option>
			</Question>
			<Question Type="InfoBox" Descriptor="Annotations Required">
				<Option>Segment on MR-T2</Option>
				<Option>Two markup lines on MR-T1</Option>
			</Question>
		</QuestionSet>
	</Page>
</Session>

```

### Results


Following is the what the results folders and results XML file may look like if you run the above example.
This would vary depending on where each user created the contours and markup lines.


```
Results tree structure

.
└─ ImageQuizzer/
    └─ Outputs/
      └─ UsersResults/
          └─ Observer1/
               ├─ PgGroup1_Patient1_Brain CT-MR/
			   │   ├─ Patient1_CT_MarkupsLine_quizline.mrk.json
			   │   └─ Patient1_MR T1-quizlabel.nrrd
               ├─ PgGroup2_Patient2_Brain CT-MR/
			   │   ├─ Patient2_CT_MarkupsLine_quizline.mrk.json
			   │   └─ Patient2_MR T2-quizlabel.nrrd
               ├─ PgGroup3_Patient3_Brain CT-MR/
			   │   ├─ Patient3_MR T1_MarkupsLine_1_quizline.mrk.json     (second measurement with '_1')
			   │   ├─ Patient3_MR T1_MarkupsLine_quizline.mrk.json       (first measurement)
			   │   └─ Patient3_MR T2-quizlabel.nrrd                      (contour label map)
			   └─ example_annotations.xml                                      (response results file)
```



```
Results file : example_annotations.xml

<?xml version="1.0" encoding="utf-8"?>
	<Session UserName="Observer1">
		<Page Descriptor="Brain CT-MR" EnableSegmentEditor="Y" ID="Patient1" MinMarkupLinesRequiredOnAnyImage="1" PageComplete="Y" PageGroup="1" SegmentRequiredOnAnyImage="Y">
			<Image ID="MR T1" Type="Volume">
				<Layer>Background</Layer>
				<DefaultDestination>Yellow</DefaultDestination>
				<DefaultOrientation>Axial</DefaultOrientation>
				<Path>ImageVolumes\CT-MR Brain\MRBrainT1.nrrd</Path>
				<LabelMapPath LoginTime="20230413_14:27:37.379856" ResponseTime="20230413_14:29:52.187094">example_annotations\PgGroup1_Patient1_Brain CT-MR\Patient1_MR T1-quizlabel.nrrd</LabelMapPath>
				<State Destination="Yellow" Level="182.72043010752674" LoginTime="20230413_14:27:37.379856" Orientation="Axial" ResponseTime="20230413_14:29:52.240166" SliceOffset="-12.60077090342297" ViewingMode="Default" Window="235.74193548387166"/>
			</Image>
			<Image ID="MR T2" Type="Volume">
				<Layer>Background</Layer>
				<DefaultDestination>Green</DefaultDestination>
				<DefaultOrientation>Axial</DefaultOrientation>
				<Path>ImageVolumes\CT-MR Brain\MRBrainT2.nrrd</Path>
				<State Destination="Green" Level="298.284946236559" LoginTime="20230413_14:27:37.379856" Orientation="Axial" ResponseTime="20230413_14:29:52.240166" SliceOffset="-19.93652601650279" ViewingMode="Default" Window="839.1720430107531"/>
			</Image>
			<Image ID="CT" Type="Volume">
				<Layer>Background</Layer>
				<DefaultDestination>Red</DefaultDestination>
				<DefaultOrientation>Axial</DefaultOrientation>
				<Path>ImageVolumes\CT-MR Brain\CTBrain.nrrd</Path>
				<MarkupLinePath LoginTime="20230413_14:27:37.379856" ResponseTime="20230413_14:29:52.197123">example_annotations\PgGroup1_Patient1_Brain CT-MR\Patient1_CT_MarkupsLine_quizline.mrk.json</MarkupLinePath>
				<State Destination="Red" Level="-732.8337801608598" LoginTime="20230413_14:27:37.379856" Orientation="Axial" ResponseTime="20230413_14:29:52.240166" SliceOffset="-33.95762238728382" ViewingMode="Default" Window="3128.820375335129"/>
			</Image>
			<QuestionSet Descriptor="" ID="Create contours">
				<Question Descriptor="Contouring Instructions" Type="InfoBox">
					<Option>
						In Segment Editor tab, select volume to create contours.
						<Response LoginTime="20230413_14:27:37.379856" ResponseTime="20230413_14:29:52.206092"/>
					</Option>
					<Option>
						   In Edit label map dropdown, use available tools to contour region of interest.
						<Response LoginTime="20230413_14:27:37.379856" ResponseTime="20230413_14:29:52.206092"/>
					</Option>
				</Question>
				<Question Descriptor="Annotations Required" Type="InfoBox">
					<Option>
						Segment on any image
						<Response LoginTime="20230413_14:27:37.379856" ResponseTime="20230413_14:29:52.206092"/>
					</Option>
					<Option>
						One markup line on any image
						<Response LoginTime="20230413_14:27:37.379856" ResponseTime="20230413_14:29:52.206092"/>
					</Option>
				</Question>
			</QuestionSet>
		</Page>
		<Page Descriptor="Brain CT-MR" EnableSegmentEditor="Y" ID="Patient2" Layout="TwoOverTwo" PageComplete="Y" PageGroup="2">
			<Image ID="MR T2" LabelMapID="MR-T2 Contour" SegmentRequired="Y" Type="Volume">
				<Layer>Background</Layer>
				<DefaultDestination>Green</DefaultDestination>
				<DefaultOrientation>Axial</DefaultOrientation>
				<Path>ImageVolumes\CT-MR Brain\MRBrainT2.nrrd</Path>
				<LabelMapPath LoginTime="20230413_14:27:37.379856" ResponseTime="20230413_14:30:42.947709">example_annotations\PgGroup2_Patient2_Brain CT-MR\Patient2_MR T2-quizlabel.nrrd</LabelMapPath>
				<State Destination="Green" Level="298.284946236559" LoginTime="20230413_14:27:37.379856" Orientation="Axial" ResponseTime="20230413_14:30:43.018773" SliceOffset="-19.93652601650279" ViewingMode="Default" Window="839.1720430107531"/>
			</Image>
			<Image ID="MR T2" SegmentRequired="Y" Type="Volume">
				<Layer>Background</Layer>
				<DefaultDestination>Yellow</DefaultDestination>
				<DefaultOrientation>Coronal</DefaultOrientation>
				<Path>ImageVolumes\CT-MR Brain\MRBrainT2.nrrd</Path>
				<LabelMapPath LoginTime="20230413_14:27:37.379856" ResponseTime="20230413_14:30:42.947709">example_annotations\PgGroup2_Patient2_Brain CT-MR\Patient2_MR T2-quizlabel.nrrd</LabelMapPath>
				<State Destination="Yellow" Level="298.284946236559" LoginTime="20230413_14:27:37.379856" Orientation="Coronal" ResponseTime="20230413_14:30:43.018773" SliceOffset="4.789432750086773" ViewingMode="Default" Window="839.1720430107531"/>
			</Image>
			<Image ID="CT" MinMarkupLinesRequired="1" Type="Volume">
				<Layer>Background</Layer>
				<DefaultDestination>Red</DefaultDestination>
				<DefaultOrientation>Axial</DefaultOrientation>
				<Path>ImageVolumes\CT-MR Brain\CTBrain.nrrd</Path>
				<MarkupLinePath LoginTime="20230413_14:27:37.379856" ResponseTime="20230413_14:30:42.960705">example_annotations\PgGroup2_Patient2_Brain CT-MR\Patient2_CT_MarkupsLine_quizline.mrk.json</MarkupLinePath>
				<State Destination="Red" Level="-732.8337801608598" LoginTime="20230413_14:27:37.379856" Orientation="Axial" ResponseTime="20230413_14:30:43.019776" SliceOffset="-36.48562226521351" ViewingMode="Default" Window="3128.820375335129"/>
			</Image>
			<Image ID="CT" MinMarkupLinesRequired="1" Type="Volume">
				<Layer>Background</Layer>
				<DefaultDestination>Slice4</DefaultDestination>
				<DefaultOrientation>Coronal</DefaultOrientation>
				<Path>ImageVolumes\CT-MR Brain\CTBrain.nrrd</Path>
				<MarkupLinePath LoginTime="20230413_14:27:37.379856" ResponseTime="20230413_14:30:42.960705">example_annotations\PgGroup2_Patient2_Brain CT-MR\Patient2_CT_MarkupsLine_quizline.mrk.json</MarkupLinePath>
				<State Destination="Slice4" Level="-732.8337801608598" LoginTime="20230413_14:27:37.379856" Orientation="Coronal" ResponseTime="20230413_14:30:43.019776" SliceOffset="19.175515083383083" ViewingMode="Default" Window="3128.820375335129"/>
			</Image>
			<QuestionSet Descriptor="" ID="Create contours">
				<Question Descriptor="Contouring Instructions" Type="InfoBox">
					<Option>
						In Segment Editor tab, select volume to create contours.
						<Response LoginTime="20230413_14:27:37.379856" ResponseTime="20230413_14:30:42.964705"/>
					</Option>
					<Option>
						   In Edit label map dropdown, use available tools to contour region of interest.
						<Response LoginTime="20230413_14:27:37.379856" ResponseTime="20230413_14:30:42.964705"/>
					</Option>
				</Question>
				<Question Descriptor="Annotations Required" Type="InfoBox">
					<Option>
						Segment on MR-T2
						<Response LoginTime="20230413_14:27:37.379856" ResponseTime="20230413_14:30:42.964705"/>
					</Option>
					<Option>
						One markup line CT
						<Response LoginTime="20230413_14:27:37.379856" ResponseTime="20230413_14:30:42.964705"/>
					</Option>
				</Question>
			</QuestionSet>
		</Page>
		<Page Descriptor="Brain CT-MR" EnableSegmentEditor="Y" ID="Patient3" PageComplete="Y" PageGroup="3">
			<Image ID="MR T1" MinMarkupLinesRequired="2" Type="Volume">
				<Layer>Background</Layer>
				<DefaultDestination>Yellow</DefaultDestination>
				<DefaultOrientation>Axial</DefaultOrientation>
				<Path>ImageVolumes\CT-MR Brain\MRBrainT1.nrrd</Path>
				<MarkupLinePath LoginTime="20230413_14:27:37.379856" ResponseTime="20230413_14:32:43.983178">example_annotations\PgGroup3_Patient3_Brain CT-MR\Patient3_MR T1_MarkupsLine_quizline.mrk.json</MarkupLinePath>
				<MarkupLinePath LoginTime="20230413_14:27:37.379856" ResponseTime="20230413_14:32:43.986178">example_annotations\PgGroup3_Patient3_Brain CT-MR\Patient3_MR T1_MarkupsLine_1_quizline.mrk.json</MarkupLinePath>
				<State Destination="Yellow" Level="182.72043010752674" LoginTime="20230413_14:27:37.379856" Orientation="Axial" ResponseTime="20230413_14:32:44.063097" SliceOffset="23.024229096577045" ViewingMode="Default" Window="235.74193548387166"/>
			</Image>
			<Image DisplayLabelMapID="MR-T2 Contour" ID="MR T2" SegmentRequired="Y" Type="Volume">
				<Layer>Background</Layer>
				<DefaultDestination>Green</DefaultDestination>
				<DefaultOrientation>Axial</DefaultOrientation>
				<Path>ImageVolumes\CT-MR Brain\MRBrainT2.nrrd</Path>
				<LabelMapPath LoginTime="20230413_14:27:37.379856" ResponseTime="20230413_14:30:43.870059">example_annotations\PgGroup3_Patient3_Brain CT-MR\Patient3_MR T2-quizlabel.nrrd</LabelMapPath>
				<State Destination="Green" Level="298.284946236559" LoginTime="20230413_14:27:37.379856" Orientation="Axial" ResponseTime="20230413_14:32:44.063097" SliceOffset="-3.976527885704449" ViewingMode="Default" Window="839.1720430107531"/>
			</Image>
			<Image ID="CT" Type="Volume">
				<Layer>Background</Layer>
				<DefaultDestination>Red</DefaultDestination>
				<DefaultOrientation>Axial</DefaultOrientation>
				<Path>ImageVolumes\CT-MR Brain\CTBrain.nrrd</Path>
				<State Destination="Red" Level="-732.8337801608598" LoginTime="20230413_14:27:37.379856" Orientation="Axial" ResponseTime="20230413_14:32:44.063097" SliceOffset="-39.01362214314319" ViewingMode="Default" Window="3128.820375335129"/>
			</Image>
			<QuestionSet Descriptor="" ID="Create contours">
				<Question Descriptor="Contouring Instructions" Type="InfoBox">
					<Option>
						In Segment Editor tab, select volume to create contours.
						<Response LoginTime="20230413_14:27:37.379856" ResponseTime="20230413_14:32:43.990178"/>
					</Option>
					<Option>
						   In Edit label map dropdown, use available tools to contour region of interest.
						<Response LoginTime="20230413_14:27:37.379856" ResponseTime="20230413_14:32:43.990178"/>
					</Option>
				</Question>
				<Question Descriptor="Annotations Required" Type="InfoBox">
					<Option>
						Segment on MR-T2
						<Response LoginTime="20230413_14:27:37.379856" ResponseTime="20230413_14:32:43.990178"/>
					</Option>
					<Option>
						Two markup lines on MR-T1
						<Response LoginTime="20230413_14:27:37.379856" ResponseTime="20230413_14:32:43.990178"/>
					</Option>
				</Question>
			</QuestionSet>
		</Page>
		<Login LoginTime="20230413_14:27:37.379856" LogoutTime="20230413_14:32:43.990178" QuizComplete="Y"/>
	</Session>



```
## See also

In the Quiz results section, see also

- [Annotations subfolders](../results.md#annotations_subfolders)
- [Contour capture](../results.md#contour-capture)
- [MarkupLine capture](../results.md#markupLine capture)
- [LabelMapPath](../results.md#labelmappath)
- [MarkupLinePath](../results.md#markuplinepath)



