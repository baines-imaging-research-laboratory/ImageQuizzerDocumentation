---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->

# Sample Data

If you wish to run the Image Quizzer example quizzes, you can download and save the image volumes
using the instructions below.

Some datasets are accessed directly through the Slicer application and others
through the tutorial links provided.

## Suggested tree structure

This is the tree structure we use for testing and building the example scripts.
If you are using a tree structure with customized folder names,
you will have to modify the image **Path** element in the scripts to match your tree layout.

We recommend saving your data in a subfolder (e.g. ImageVolumes) since, in the parent database directory (ImageQuizzerData)
two other subfolders will be created:

1. The **Users** folder which will hold the observer results files.
1. The **SlicerDicomDatabase** folder that Slicer automatically creates to store pointers to the loaded DICOM files.

```
.
└─ ImageQuizzerData/
    │ └─ ImageVolumes/
    │     ├─ MRHead/
    │     │     └─ MRHead.nrrd
    │     ├─ MRBrain/
    │     │     └─ MRBrain.nrrd
    │     ... etc.
    │     ├─ ExtractedSampleData1/
    │     ├─ ExtractedSampleData2/
	
	(automatically created)
    │	  
	├─ Users/
	└─ SlicerDicomDatabase/

```

When logging in to the Image Quizzer, users point to **ImageQuizzerData** as the image database folder.
All paths in the scripts are relative to this folder and begin with **ImageVolumes/...**.


## Slicer sample datasets

Some of the sample datasets referenced to run the example scripts can be downloaded directly from the Slicer application.
These include:

* CTChest
* MRHead
* MRBrain Tumor1
* MRBrain Tumor2
* CT-MR Brain
* CT Cardio Volume Sequence

### Download and save

Following is a brief set of commands to download and save 
any of the image datasets available through the Slicer application.

* Open 3D Slicer. 
* In the Welcome to Slicer module, select **Download Sample Data**
* Select the image dataset to download.
* Select File>Save in Slicer's menu bar
* Unselect all check marks under File Name except for the image volume being saved.
* The default file format for saving data is *.nrrd which will match the script examples.
* Browse to the folder that you wish to save the sample data.
* Click on the Save button.

Refer to Slicer's documentation [download and save](https://slicer.readthedocs.io/en/latest/user_guide/data_loading_and_saving.html) for more more details.




## Tutorial data links

Some example scripts refer to data that can be downloaded and extracted using these links.

[DICOM dataset1_TorsoCT](https://spujol.github.io/SlicerDICOMTutorial) 

[PETCTFusion dataset](http://www.na-mic.org/Wiki/index.php/Events:RSNA_CTSA_2009#Tutorial_Data) see link for "Data for Quantitative PET/CT tutorial"


Once downloaded, extract the sample data into the suggested tree structure for plug and play examples.


