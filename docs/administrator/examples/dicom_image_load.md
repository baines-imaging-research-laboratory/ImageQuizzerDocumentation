---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->
# Loading DICOM images

The Image Quizzer can load DICOM images although this can be slow depending on the number of .dcm files to be read in.

!!! tip
    If these images can be converted to a data volume (e.g. .nii or .nrrd), the load will be much faster.


The main attributes of interest used for this example include:

- DicomRead="*option*"
    - an attribute in the Image element
	- if set to "Y", images will be loaded using dicom functionality
	- if set to "N" (default) images are loaded as data volumes
	
- Path
    - an element that is a child of the Image element
    - directory path to one dicom slice for the image
	


## Prep

Use the test data provided in the Image Quizzer download:
 
```
.
└─ ImageQuizzerProject/
   └─ ImageQuizzer
         └─ ImageQuizzerData/
               └─ ImageVolumes/
                   └─ TinyRtStudy/
```

## Script example

```
<Session>
	<Page ID="TinyPatient" Descriptor="DicomSeries">
		<Image DicomRead="Y" Type="Volume" ID="CTSeries">
			<DefaultDestination>Red</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Axial</DefaultOrientation>
			<Path>ImageVolumes\TinyRtStudy\image0000_1.2.826.0.1.3680043.8.274.1.1.2750954856.34924.5415589575.496.dcm</Path>
		</Image>
		<Image DicomRead="Y" Type="Volume" ID="CTSeries">
			<DefaultDestination>Yellow</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Sagittal</DefaultOrientation>
			<Path>ImageVolumes\TinyRtStudy\image0000_1.2.826.0.1.3680043.8.274.1.1.2750954856.34924.5415589575.496.dcm</Path>
		</Image>
		<Image DicomRead="Y" Type="Volume" ID="CTSeries">
			<DefaultDestination>Green</DefaultDestination>
			<Layer>Background</Layer>
			<DefaultOrientation>Coronal</DefaultOrientation>
			<Path>ImageVolumes\TinyRtStudy\image0000_1.2.826.0.1.3680043.8.274.1.1.2750954856.34924.5415589575.496.dcm</Path>
		</Image>
	</Page>
</Session>
```

