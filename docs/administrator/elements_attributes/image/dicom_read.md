---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# DicomRead

## Specs

| ||Details|
|---|---|:---:|
| **Name** | DicomRead ||
| **Classification** | attribute ||
| **Parent** | <[Image](index.md)\> ||
| **Required** | no ||
| **Syntax** | DicomRead="*option*" |  |
| **Options** | Y | load image dicom slices|
|             | N |(default) load image as a data volume |
| **Dependencies**| [Path](path.md) | if DicomRead="Y", Path must point to one slice of the dicom series|

## Description

If this attribute is set to "Y", and the Path element must point to one DICOM slice for that image.
The Image Quizzer will look into that .dcm file and identify the DICOM series UID.
All DICOM slices that belong to that series will be loaded.
