---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# Path

## Specs

| ||Details|
|---|---|:---:|
| **Name** | Path ||
| **Classification** | element ||
| **Parent** | <[Image](index.md)\> ||
| **Required** | yes ||
| **Syntax** | <Path\>*string*</Path\> | relative/path/to/image/filename |
| **Associations** | [Page ID](../page/id.md) | uniqueness validation |
||[Image ID](id.md) | uniqueness validation |



## Description

This element holds the path to the image file to be loaded. It is relative to the image database folder
that the user selects when logging in to the Image Quizzer.


#### Uniqueness
The ID attribute for the Image is combined with the ID attribute
of the Page to create a unique node name when loaded into Slicer. 
There can be multiple Image elements within a Page with the same Path (e.g., one image
loaded into different viewing windows). Each of these elements must
have the same Image ID attribute. This is checked during quiz validation.


## Example

An example script is shown for the following tree structure. ImageDatabaseFolder is the folder defined
by the user to hold the image files for the observer strudy.

```
.
└─ ImageDatabaseFolder/
      └─ ImageVolumes/
          └─ Brain/
                └─ BrainCT.nrrd
```

Script

```
<Session>
	<Page ID="Patient-1" Descriptor="DicomSeries">
		<Image  Type="Volume" ID="CTSeries">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\Brain\BrainCT.nrrd</Path>
		</Image>
	</Page>
</Session>
```
