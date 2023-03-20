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
| **Syntax** | Path="*string*" | relative/path/to/image/filename |

## Description

This element holds the path to the image file to be loaded. It is relative to the image database folder
that the user selects when logging in to the Image Quizzer.

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
