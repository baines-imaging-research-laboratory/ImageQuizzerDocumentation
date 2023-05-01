---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# VolumeSequence 4D Images

This example shows how to load 4D image volumes using the  Type="VolumeSequence" attribute.
Using this attribute, the time sequence controls will be enabled 
allowing the user to play the image frames as a movie.


## Prep

For the following example, we will use the CT Cardio Volume Sequence sample dataset that is available when you open Slicer.	

Download and save the dataset as described in the [sample data](sample_data.md#slicer-sample-datasets) section
to a subfolder under ImageVolumes folder as shown.



```
.
└─ ImageQuizzerData/
      └─ ImageVolumes/
          └─ CT Cardio Volume Sequence/
               ├─ CTCardioSeq.nrrd
               └─ CTCardioSeq.seq.nrrd
```

## Script example

This script has 3 pages.

* The first loads the volume that contains all time points as Type="VolumeSequence". The time sequence controls are enabled and will play the image frames as a movie.
* The second page loads the volume that contains only the first time point and loads it as Type="VolumeSequence".
You will see the time Sequence controls are enabled but they don't play the time series since there is only one frame.
* The third page loads again loads the volume that contains only the first time point but loads it as Type="Volume"
You will see that the image looks the same as presented in Page 2 but the time sequence controls are greyed out.



```
<Session>
	<Page ID="CardioPatient" Descriptor="VolumeSequence load">
		<Image Type="VolumeSequence" ID="CTSeries">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\CT Cardio Volume Sequence\CTCardioSeq.seq.nrrd</Path>
		</Image>
		<Image Type="VolumeSequence" ID="CTSeries">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Sagittal</DefaultOrientation>
			<Path>ImageVolumes\CT Cardio Volume Sequence\CTCardioSeq.seq.nrrd</Path>
		</Image>
		<Image Type="VolumeSequence" ID="CTSeries">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Coronal</DefaultOrientation>
			<Path>ImageVolumes\CT Cardio Volume Sequence\CTCardioSeq.seq.nrrd</Path>
		</Image>
		<QuestionSet ID="QS-Info" Descriptor="VolumeSequence load">
			<Question Type="InfoBox" Descriptor="All time series">
				<Option>Image loaded as VolumeSequence</Option>
				<Option>Controls activated</Option>
				<Option>9 Time points (frames)</Option>
			</Question>
		</QuestionSet>
	</Page>
	<Page ID="CardioPatient" Descriptor="VolumeSequence Time Point 0">
		<Image Type="VolumeSequence" ID="CTSeries">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\CT Cardio Volume Sequence\CTCardioSeq.nrrd</Path>
		</Image>
		<Image Type="VolumeSequence" ID="CTSeries">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Sagittal</DefaultOrientation>
			<Path>ImageVolumes\CT Cardio Volume Sequence\CTCardioSeq.nrrd</Path>
		</Image>
		<Image Type="VolumeSequence" ID="CTSeries">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Coronal</DefaultOrientation>
			<Path>ImageVolumes\CT Cardio Volume Sequence\CTCardioSeq.nrrd</Path>
		</Image>
		<QuestionSet ID="QS-Info" Descriptor="VolumeSequence load">
			<Question Type="InfoBox" Descriptor="Time point 0">
				<Option>Image with time point 0 loaded as VolumeSequence</Option>
				<Option>Controls visible but do not play (only one frame)</Option>
			</Question>
		</QuestionSet>
	</Page>
	<Page ID="CardioPatient" Descriptor="Volume load">
		<Image Type="Volume" ID="CTSeries">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\CT Cardio Volume Sequence\CTCardioSeq.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="CTSeries">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Sagittal</DefaultOrientation>
			<Path>ImageVolumes\CT Cardio Volume Sequence\CTCardioSeq.nrrd</Path>
		</Image>
		<Image Type="Volume" ID="CTSeries">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Coronal</DefaultOrientation>
			<Path>ImageVolumes\CT Cardio Volume Sequence\CTCardioSeq.nrrd</Path>
		</Image>
		<QuestionSet ID="QS-Info" Descriptor="Volume load">
			<Question Type="InfoBox" Descriptor="Time point 0">
				<Option>Image with time point 0 loaded as Volume</Option>
				<Option>Controls not enabled</Option>
			</Question>
		</QuestionSet>
	</Page>
</Session>

```




