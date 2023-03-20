---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# Layouts

The Image Quizzer enables you to define the configuration of viewing windows to be
displayed. The different layouts available are shown in the examples below.

Following are the window assignments available for each of the layouts. These window names
are used in the [DefaultDestination](../elements_attributes/image/default_destination.md) element.

| | Name | Details| Notes |
|---| ---|---|---|
| **Options** | FourUp |(default) Red, Green, and Yellow| default 3 windows |
|             | TwoOverTwo | Red, Green, Yellow, and Slice4 | Helpful when you need 4 windows |
|             | OneUpRedSlice | Red window only| Good for close ups |
|             | SideBySideRedYellow | Red and Yellow windows | Good for comparisons |



The main attributes of interest used for this example include:

- [DicomRead](../elements_attributes/image/dicom_read.md)
- [Layout](../elements_attributes/page/layout.md)
- [DefaultDestination](../elements_attributes/image/default_destination.md)


## Prep

Download the PETCTFusion-Tutorial-Data dataset as described in the [sample data sets](index.md#sample-data) section.

Extract the PETCTFusion-Tutorial-Data to a subfolder under ImageVolumes/ as shown.

```
.
└─ ImageQuizzerData/
      └─ ImageVolumes/
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

## Script examples

Layout="FourUp"

```
<Session>
	<Page ID="Patient1" Descriptor="PET-CT" Layout="FourUp">
		<Image DicomRead="Y" Type="Volume" ID="CT">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\PETCTFusion-Tutorial-Data\PETCTFusion\CT1\26556672</Path>
		</Image>
		<Image DicomRead="Y" ID="CT" Type="Volume">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Coronal</DefaultOrientation>
			<Path>ImageVolumes\PETCTFusion-Tutorial-Data\PETCTFusion\CT1\26556672</Path>
		</Image>
		<Image DicomRead="Y" ID="CT" Type="Volume">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Sagittal</DefaultOrientation>
			<Path>ImageVolumes\PETCTFusion-Tutorial-Data\PETCTFusion\CT1\26556672</Path>
		</Image>
	</Page>
</Session>
```
![FourUp](assets/layout_fourup.png)

```
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
```

Layout="SideBySideRedYellow"
```
<Session>
	<Page ID="Patient1" Descriptor="PET-CT" Layout="SideBySideRedYellow">
		<Image DicomRead="Y" Type="Volume" ID="CT">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Sagittal</DefaultOrientation>
			<Path>ImageVolumes\PETCTFusion-Tutorial-Data\PETCTFusion\CT1\26556672</Path>
		</Image>
		<Image DicomRead="Y" Type="Volume" ID="PET">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Sagittal</DefaultOrientation>
			<Path>ImageVolumes\PETCTFusion-Tutorial-Data\PETCTFusion\PET1\26558596</Path>
		</Image>
	</Page>
</Session>
```

![SideBySideRedYellow](assets/layout_sidebysideredyellow.png)



```
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
```

Layout="TwoOverTwo"
```
<Session>
	<Page ID="Patient1" Descriptor="PET-CT" Layout="TwoOverTwo">
		<Image DicomRead="Y" Type="Volume" ID="CT">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\PETCTFusion-Tutorial-Data\PETCTFusion\CT1\26556672</Path>
		</Image>
		<Image DicomRead="Y" ID="CT" Type="Volume">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Coronal</DefaultOrientation>
			<Path>ImageVolumes\PETCTFusion-Tutorial-Data\PETCTFusion\CT1\26556672</Path>
		</Image>
		<Image DicomRead="Y" ID="CT" Type="Volume">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Sagittal</DefaultOrientation>
			<Path>ImageVolumes\PETCTFusion-Tutorial-Data\PETCTFusion\CT1\26556672</Path>
		</Image>
		<Image DicomRead="Y" ID="PET" Type="Volume">
			<DefaultDestination>Slice4</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Coronal</DefaultOrientation>
			<Path>ImageVolumes\PETCTFusion-Tutorial-Data\PETCTFusion\PET1\26558596</Path>
		</Image>
	</Page>
</Session>
```

![TwoOverTwo](assets/layout_twoovertwo.png)

```
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
```

Layout="OneUpRedSlice"
```
<Session>
	<Page ID="Patient1" Descriptor="CT" Layout="OneUpRedSlice">
		<Image DicomRead="Y" Type="Volume" ID="CT">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Sagittal</DefaultOrientation>
			<Path>ImageVolumes\PETCTFusion-Tutorial-Data\PETCTFusion\CT1\26556672</Path>
		</Image>
	</Page>
</Session>
```

![OneUpRedSlice](assets/layout_oneupredslice.png)

