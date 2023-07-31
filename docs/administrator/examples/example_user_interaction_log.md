---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# User Interaction Log

This example focusses on the
[UserInteractionLog](../elements_attributes/page/user_interaction_log.md) feature. This is an attribute
of the Page element. 

One application for this feature is to cross-reference the screen XY coordinates
captured using eye-tracking software. 

When you enable this feature, the application will:

- lock down all adjustable sizing aspects of the display
- generate a log file that captures the screen XY coordinates of the displayed viewing windows and the corresponding 
IJK coordinates of the image volume displayed
	
See [UserInteractionLog](../elements_attributes/page/user_interaction_log.md) for details.

 

## Prep

For the following example, we will use ChestCT and the PETCTFusion-Tutorial-Data 
dataset as described in the [sample data](sample_data.md#tutorial-data-links) section.	

Download and save the datasets in the subfolders under ImageVolumes folder as shown.

```
.
└─ ImageQuizzerData/
      └─ ImageVolumes/
          └─ CTChest/
                └─ CTChest.nrrd
          └─ PETCTFusion-Tutorial-Data/
                └─ PETCTFusion/
                      └─ CT1/
                         ├─ 26556672
                         ├─ 26556691
				         ├─ ...
                      └─ CT2/
                      └─ PET1/
                         ├─ 26558596
                         ├─ 26558607
				         ├─ ...
                     └─ PET2/
```



## Script example

This script example has UserInteractionLog="Y" attribute in the secnd Page element.

The first page loads one image volume in the background only while the
second page has both a foreground and background image volume loaded.

See details in [UserInteractionLog](../elements_attributes/page/user_interaction_log.md) 
for location and a description of the data captured in these log files.



```
<Session>
    <Page ID="Patient 1" Descriptor="CT" UserInteractionLog="Y">
        <Image ID="CT" Type="Volume"  ZoomFactor="1.2" PanOrigin="-92 27.5 -225.5" InitialSliceOffset="-245">
                <DefaultDestination>Red</DefaultDestination>
                <Layer>Background</Layer>
                <DefaultOrientation>Axial</DefaultOrientation>
                <Path>ImageVolumes\CTChest\CTChest.nrrd</Path>
        </Image>
        <Image ID="CT" Type="Volume" ZoomFactor="1.5" PanOrigin="-43.96383459076361 63.246218183203815 0.0" InitialSliceOffset="-112">
                <DefaultDestination>Green</DefaultDestination>
                <Layer>Background</Layer>
                <DefaultOrientation>Coronal</DefaultOrientation>
                <Path>ImageVolumes\CTChest\CTChest.nrrd</Path>
        </Image>
        <Image ID="CT" Type="Volume" ZoomFactor=".75" PanOrigin="118 39 0" InitialSliceOffset="91">
                <DefaultDestination>Yellow</DefaultDestination>
                <Layer>Background</Layer>
                <DefaultOrientation>Sagittal</DefaultOrientation>
                <Path>ImageVolumes\CTChest\CTChest.nrrd</Path>
        </Image>
        <QuestionSet ID="Steps" Descriptor="User interaction log feature">
            <Question Type="CheckBox" Descriptor="Testing user interaction log">
                <Option>Layout locked</Option>
				<Option>Log started</Option>
            </Question>
        </QuestionSet>
    </Page>
    <Page ID="Patient2" Descriptor="PET PSMA" Layout="TwoOverTwo" UserInteractionLog="Y">
        <Image DicomRead="Y" Type="Volume" ID="CT">
            <DefaultDestination>Red</DefaultDestination>
            <Layer>Background</Layer>
            <DefaultOrientation>Axial</DefaultOrientation>
            <Path>ImageVolumes\PETCTFusion-Tutorial-Data\PETCTFusion\CT1\26556672</Path>
        </Image>
        <Image DicomRead="Y" Type="Volume" ID="CT">
            <DefaultDestination>Green</DefaultDestination>
            <Layer>Background</Layer>
            <DefaultOrientation>Sagittal</DefaultOrientation>
            <Path>ImageVolumes\PETCTFusion-Tutorial-Data\PETCTFusion\CT1\26556672</Path>
        </Image>
        <Image DicomRead="Y" Type="Volume" ID="CT">
            <DefaultDestination>Yellow</DefaultDestination>
            <Layer>Background</Layer>
            <DefaultOrientation>Coronal</DefaultOrientation>
            <Path>ImageVolumes\PETCTFusion-Tutorial-Data\PETCTFusion\CT1\26556672</Path>
        </Image>
        <Image DicomRead="Y" Type="Volume" ID="PET" ColorTable='PET-Heat' >
            <DefaultDestination>Red</DefaultDestination>
            <Layer>Foreground</Layer>
            <DefaultOrientation>Axial</DefaultOrientation>
            <Path>ImageVolumes\PETCTFusion-Tutorial-Data\PETCTFusion\PET1\26558596</Path>
        </Image>
        <Image DicomRead="Y" Type="Volume" ID="PET" ColorTable='PET-Heat' >
            <DefaultDestination>Green</DefaultDestination>
            <Layer>Foreground</Layer>
            <DefaultOrientation>Sagittal</DefaultOrientation>
            <Path>ImageVolumes\PETCTFusion-Tutorial-Data\PETCTFusion\PET1\26558596</Path>
        </Image>
        <Image DicomRead="Y" Type="Volume" ID="PET" ColorTable='PET-Heat' >
            <DefaultDestination>Yellow</DefaultDestination>
            <Layer>Foreground</Layer>
            <DefaultOrientation>Coronal</DefaultOrientation>
            <Path>ImageVolumes\PETCTFusion-Tutorial-Data\PETCTFusion\PET1\26558596</Path>
        </Image>
        <Image Type="Volume" ID="PET" ColorTable='PET-Heat' >
            <DefaultDestination>Slice4</DefaultDestination>
            <Layer>Background</Layer>
            <DefaultOrientation>Coronal</DefaultOrientation>
            <Path>ImageVolumes\PETCTFusion-Tutorial-Data\PETCTFusion\PET1\26558596</Path>
        </Image>
        <QuestionSet ID="Steps" Descriptor="User interaction log feature">
            <Question Type="CheckBox" Descriptor="Testing user interaction log">
                <Option>Layout locked</Option>
				<Option>Log started</Option>
            </Question>
        </QuestionSet>
	</Page>
</Session>

```


