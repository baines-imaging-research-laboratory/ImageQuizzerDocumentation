---
hide:
- toc
---
# Image

## Specs

| |Value|Details|
|---|---|---|
| **Name** | Image |  |
| **Classification** | element ||
| **Parent** | <[Page](../page/index.md)\> ||
| **Required** | no ||
| **Syntax** | <Image\>||


See also: 


## Description
The Image element is a child of the Page element. There can be multiple images on a Page.
Each image is assigned a viewing window

Among the many attributes allowed for the Image element, ID and Type are required.

Image is not a required element. The administrator may choose to load a Page
with no images but with Question elements only. The Page can then be used to convey
instructions to the user or display questions that do not depend on images. 


## Example

```
<Session>
  <Page ID="Patient 1" Descriptor="MR">
    <Image ID="T1W" Type="Volume">
      ...
	</Image>
  </Page>
</Session>
```

## Attributes
#####[ID](id.md)
#####[DicomRead](dicom_read.md)
<!--
#####[Type](type.md)
#####[LabelMapID](pagegroup.md)
#####[DisplayLabelMapID](allowmultipleresponse.md)
#####[RotateToAcquisition](enable_segment_editor.md)
#####[ColorTable](segment_required_on_any_image.md)
#####[Opacity](markuplinesanyimage.md)
#####[SegmentRequired](looping.md)

-->