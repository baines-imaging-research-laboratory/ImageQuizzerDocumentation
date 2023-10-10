---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# Link views and multiple responses

For this example we will demonstrate Image Quizzer's ability to link the viewing windows so that images will scroll together.
Also, this example shows how different pages can be set up to allow the user to modify their response when using the Previous and Next buttons.


The two Page attributes being highlighted are: 

1. [LinkViews](../elements_attributes/page/link_views.md)
1. [AllowMultipleResponse](../elements_attributes/page/allow_multiple_response.md)



## Prep

Download and save the **CT-MR Brain** dataset as described in the [sample data](sample_data.md#slicer-sample-datasets) section.


Save the dataset to a subfolder under ImageVolumes/ as shown.

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

For this example, the first page is set up for linking views and also allows for multiple responses.
The second page has both of these attributes turned off.

```
<Session>
	<Page ID="Patient1" Descriptor="Brain-MR T1" LinkViews="Y"  AllowMultipleResponse="Y">
		<Image Type="Volume" ID="MR T1">
			<Layer>Background</Layer>
			<DefaultDestination>Red</DefaultDestination>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\CT-MR Brain\MRBrainT1.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="MR T2">
			<Layer>Background</Layer>
			<DefaultDestination>Green</DefaultDestination>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\CT-MR Brain\MRBrainT2.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="CT">
			<Layer>Background</Layer>
			<DefaultDestination>Yellow</DefaultDestination>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\CT-MR Brain\CTBrain.nrrd</Path>
		</Image>
		<QuestionSet ID="Linking Images">
			<Question  Type="CheckBox">
				<Option>Images are linked</Option>
				<Option>Images are not linked</Option>
				<Option>Multiple responses allowed</Option>
				<Option>Multiple responses not allowed</Option>
			</Question>
		</QuestionSet>
	</Page>
	<Page ID="Patient1" Descriptor="Brain-MR T1" LinkViews="N" AllowMultipleResponse="N">
		<Image Type="Volume" ID="MR T1">
			<Layer>Background</Layer>
			<DefaultDestination>Red</DefaultDestination>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\CT-MR Brain\MRBrainT1.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="MR T2">
			<Layer>Background</Layer>
			<DefaultDestination>Green</DefaultDestination>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\CT-MR Brain\MRBrainT2.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="CT">
			<Layer>Background</Layer>
			<DefaultDestination>Yellow</DefaultDestination>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\CT-MR Brain\CTBrain.nrrd</Path>
		</Image>
		<QuestionSet ID="Linking Images">
			<Question  Type="CheckBox">
				<Option>Images are linked</Option>
				<Option>Images are not linked</Option>
				<Option>Multiple responses allowed</Option>
				<Option>Multiple responses not allowed</Option>
			</Question>
		</QuestionSet>
	</Page>
</Session>
```

## Results file

The results file that follows shows that the user answered questions for both pages 1 and 2.
Then before pressing the **Finish** button, they pressed **Previous** and changed the checkbox selection.
This can be deduced by following the *ResponseTime* attribute in each *Response* element.

After changing the selection for page 1, the user advanced to page 2 using the **Next** button and found
that no modification to the original response was not allowed - the quiz question was greyed out.

Note the double **Response** elements for each **Option** in the first page where
the 3rd question was modified. 

```
<?xml version="1.0" encoding="utf-8"?>
	<Session UserName="Observer1">
		<Page AllowMultipleResponse="Y" Descriptor="Brain-MR T1" ID="Patient1" LinkViews="Y" PageComplete="Y" PageGroup="1">
			<Image ID="MR T1" Type="Volume">
				<Layer>Background</Layer>
				<DefaultDestination>Red</DefaultDestination>
				<DefaultOrientation>Axial</DefaultOrientation>
				<Path>ImageVolumes\CT-MR Brain\MRBrainT1.nrrd</Path>
				<State Destination="Red" Level="401.0" LoginTime="20230328_09:33:04.800754" Orientation="Axial" ResponseTime="20230328_09:33:45.533243" SliceOffset="-20.265101176531108" ViewingMode="Default" Window="802.0"/>
				<State Destination="Red" Level="401.0" LoginTime="20230328_09:33:04.800754" Orientation="Axial" ResponseTime="20230328_09:34:38.412159" SliceOffset="-32.116200220975195" ViewingMode="Default" Window="802.0"/>
			</Image>
			<Image ID="MR T2" Type="Volume">
				<Layer>Background</Layer>
				<DefaultDestination>Green</DefaultDestination>
				<DefaultOrientation>Axial</DefaultOrientation>
				<Path>ImageVolumes\CT-MR Brain\MRBrainT2.nrrd</Path>
				<State Destination="Green" Level="440.5" LoginTime="20230328_09:33:04.800754" Orientation="Axial" ResponseTime="20230328_09:33:45.533243" SliceOffset="-20.265101176531108" ViewingMode="Default" Window="881.0"/>
				<State Destination="Green" Level="440.5" LoginTime="20230328_09:33:04.800754" Orientation="Axial" ResponseTime="20230328_09:34:38.412159" SliceOffset="-32.116200220975195" ViewingMode="Default" Window="881.0"/>
			</Image>
			<Image ID="CT" Type="Volume">
				<Layer>Background</Layer>
				<DefaultDestination>Yellow</DefaultDestination>
				<DefaultOrientation>Axial</DefaultOrientation>
				<Path>ImageVolumes\CT-MR Brain\CTBrain.nrrd</Path>
				<State Destination="Yellow" Level="-679.0" LoginTime="20230328_09:33:04.800754" Orientation="Axial" ResponseTime="20230328_09:33:45.533243" SliceOffset="-20.265101176531108" ViewingMode="Default" Window="4690.0"/>
				<State Destination="Yellow" Level="-679.0" LoginTime="20230328_09:33:04.800754" Orientation="Axial" ResponseTime="20230328_09:34:38.412159" SliceOffset="-32.116200220975195" ViewingMode="Default" Window="4690.0"/>
			</Image>
			<QuestionSet ID="Linking Images">
				<Question Type="CheckBox">
					<Option>
						Images are linked
						<Response LoginTime="20230328_09:33:04.800754" ResponseTime="20230328_09:33:45.530255">Y</Response>
						<Response LoginTime="20230328_09:33:04.800754" ResponseTime="20230328_09:34:38.408172">Y</Response>
					</Option>
					<Option>
						Images are not linked
						<Response LoginTime="20230328_09:33:04.800754" ResponseTime="20230328_09:33:45.530255">N</Response>
						<Response LoginTime="20230328_09:33:04.800754" ResponseTime="20230328_09:34:38.408172">N</Response>
					</Option>
					<Option>
						Multiple responses allowed
						<Response LoginTime="20230328_09:33:04.800754" ResponseTime="20230328_09:33:45.530255">N</Response>
						<Response LoginTime="20230328_09:33:04.800754" ResponseTime="20230328_09:34:38.408172">Y</Response>
					</Option>
					<Option>
						Multiple responses not allowed
						<Response LoginTime="20230328_09:33:04.800754" ResponseTime="20230328_09:33:45.530255">N</Response>
						<Response LoginTime="20230328_09:33:04.800754" ResponseTime="20230328_09:34:38.408172">N</Response>
					</Option>
				</Question>
			</QuestionSet>
		</Page>
		<Page AllowMultipleResponse="N" Descriptor="Brain-MR T1" ID="Patient1" LinkViews="N" PageComplete="Y" PageGroup="2">
			<Image ID="MR T1" Type="Volume">
				<Layer>Background</Layer>
				<DefaultDestination>Red</DefaultDestination>
				<DefaultOrientation>Axial</DefaultOrientation>
				<Path>ImageVolumes\CT-MR Brain\MRBrainT1.nrrd</Path>
				<State Destination="Red" Level="401.0" LoginTime="20230328_09:33:04.800754" Orientation="Axial" ResponseTime="20230328_09:34:03.073548" SliceOffset="-21.20147133559338" ViewingMode="Default" Window="802.0"/>
				<State Destination="Red" Level="401.0" LoginTime="20230328_09:33:04.800754" Orientation="Axial" ResponseTime="20230328_09:34:52.624938" SliceOffset="-21.20147133559338" ViewingMode="Default" Window="802.0"/>
			</Image>
			<Image ID="MR T2" Type="Volume">
				<Layer>Background</Layer>
				<DefaultDestination>Green</DefaultDestination>
				<DefaultOrientation>Axial</DefaultOrientation>
				<Path>ImageVolumes\CT-MR Brain\MRBrainT2.nrrd</Path>
				<State Destination="Green" Level="440.5" LoginTime="20230328_09:33:04.800754" Orientation="Axial" ResponseTime="20230328_09:34:03.073548" SliceOffset="-20.265101176531108" ViewingMode="Default" Window="881.0"/>
				<State Destination="Green" Level="440.5" LoginTime="20230328_09:33:04.800754" Orientation="Axial" ResponseTime="20230328_09:34:52.624938" SliceOffset="-4.163952819596718" ViewingMode="Default" Window="881.0"/>
			</Image>
			<Image ID="CT" Type="Volume">
				<Layer>Background</Layer>
				<DefaultDestination>Yellow</DefaultDestination>
				<DefaultOrientation>Axial</DefaultOrientation>
				<Path>ImageVolumes\CT-MR Brain\CTBrain.nrrd</Path>
				<State Destination="Yellow" Level="-679.0" LoginTime="20230328_09:33:04.800754" Orientation="Axial" ResponseTime="20230328_09:34:03.073548" SliceOffset="-40.25366164063127" ViewingMode="Default" Window="4690.0"/>
				<State Destination="Yellow" Level="-679.0" LoginTime="20230328_09:33:04.800754" Orientation="Axial" ResponseTime="20230328_09:34:52.624938" SliceOffset="-2.7751107704434537" ViewingMode="Default" Window="4690.0"/>
			</Image>
			<QuestionSet ID="Linking Images">
				<Question Type="CheckBox">
					<Option>
						Images are linked
						<Response LoginTime="20230328_09:33:04.800754" ResponseTime="20230328_09:34:03.070559">N</Response>
					</Option>
					<Option>
						Images are not linked
						<Response LoginTime="20230328_09:33:04.800754" ResponseTime="20230328_09:34:03.070559">Y</Response>
					</Option>
					<Option>
						Multiple responses allowed
						<Response LoginTime="20230328_09:33:04.800754" ResponseTime="20230328_09:34:03.070559">N</Response>
					</Option>
					<Option>
						Multiple responses not allowed
						<Response LoginTime="20230328_09:33:04.800754" ResponseTime="20230328_09:34:03.070559">N</Response>
					</Option>
				</Question>
			</QuestionSet>
		</Page>
		<Login LoginTime="20230328_09:33:04.800754" LogoutTime="20230328_09:34:38.408172" QuizComplete="Y"/>
	</Session>

```