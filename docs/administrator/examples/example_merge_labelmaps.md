---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# Merging Label Maps

The MergeLabelMaps attribute works in association with the Page attribute Loop="Y". 
This is useful when you want the user to answer quiz questions for each ROI seen on an image
and then have all the ROI's for that image displayed on a subsequent page.

Merging can only be done in conjunction with the Loop="Y" attribute for a page. In order for the 
merge to happen, there are a number of conditions that must be met. See [Merge LabelMaps](../elements_attributes/image/merge_labelmaps.md) in the
scripting elements and attributes section for more details on the dependencies.



## Prep

Download and save Slicer's CTChest dataset as described in the [sample data](sample_data.md#slicer-sample-datasets) section.

Suggested folder structure to match script:
```
.
└─ ImageQuizzerData/
      └─ ImageVolumes/
          └─ CTChest/
                └─ CTChest.nrrd
```


## Script example

In this example, there are two pages. 
The first page has Loop="Y" with the Segment Editor enabled giving the user the ability to create contours.
The Repeat button, will present the same images and questions and the user can contour a different region of interest.

The second page turns off the Segment Editor and has the 'DisplayLabelMapID' and 'MergeLabelMapContours' attributes
assigned.


Both pages are assigned to the same Page Group number (required). This prevents contours
created from different Page Groups being merged together.

```
<Session>
	<Page ID="Patient 1" Descriptor="Create Contours" Layout="OneUpRedSlice" Loop="Y" EnableSegmentEditor="Y" PageGroup="1">
		<Image ID="CT" Type="Volume" LabelMapID="Lung ROI">
				<DefaultDestination>Red</DefaultDestination>
				<Layer>Background</Layer>
				<DefaultOrientation>Axial</DefaultOrientation>
				<Path>ImageVolumes\CTChest\CTChest.nrrd</Path>
		</Image>
		<QuestionSet ID="Repeating Page">
			<Question Type="InfoBox">
				<Option>Create contours to be merged</Option>
				<Option>Use REPEAT button to create next contour.</Option>
			</Question>
		</QuestionSet>
	</Page>
	<Page ID="Patient 1" Descriptor="Display Merged Contours" Layout="OneUpRedSlice" PageGroup="1">
		<Image ID="CT" Type="Volume" DisplayLabelMapID="Lung ROI" MergeLabelMaps="Y">
				<DefaultDestination>Red</DefaultDestination>
				<Layer>Background</Layer>
				<DefaultOrientation>Axial</DefaultOrientation>
				<Path>ImageVolumes\CTChest\CTChest.nrrd</Path>
		</Image>
		<QuestionSet ID="Merging conditions">
			<Question Type="InfoBox">
				<Option>Page displays contours created previously in the looping page.</Option>
				<Option></Option>
				<Option>Attribute and element value matching for this page and the previous page include:</Option>
				<Option>          DisplayLabelMapID = LabelMapID</Option>
				<Option>          PageGroup</Option>
				<Option>          ImagePath</Option>
			</Question>
		</QuestionSet>
	</Page>
</Session>
```

### Results

Following are screen shots of contours created using the example script above. 
Here, a contour was created on the first page displayed. Then after pressing the Repeat button,
another contour was created that was close to the original (some pixels overlapped).

The first two snapshots show the contours created using the Repeat button.
This is followed by the display of the merged contours.

!!! Note
	Pixel locations that have overlapping contours are rendered using the contour label associated with the greater label number.
	
![First contour](../assets/example_mergelabelmaps_contour1.png)
![Second contour](../assets/example_mergelabelmaps_contour2.png)
![Merged contours](../assets/example_mergelabelmaps_merged.png)