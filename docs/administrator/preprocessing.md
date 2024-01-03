---
hide:
- toc
---
# Preprocessing utilities


## ConvertDicomToNiiVolume

This conversion utility will convert a dicom series image into a single NIfTI file.
It can be run on a single dicom series or in batch mode.

The utility can be found here:

```
.
└─ ImageQuizzer/
	  └─ PrePost_Processing/
	      └─ ConvertDicomToNiiVolume.py
```
	
### How to run

#### From a command terminal

This assumes you have Python (minimum version 3) installed on your PC.


```
Run cmd.exe

>>>cd path/to/ImageQuizzer/PrePost_Processing

		for single run - one dicom series
>>>py ConvertDicomToNiiVolume.py -i path/to/input/dicom/folder -o path/to/output/folder

		for multiple runs
>>>py ConvertDicomToNiiVolume.py -b path/to/batchfile.csv


```

#### From Slicer's Python Interactor

If you don't have Python installed on your PC, you can use the Python Interactor in Slicer. Following 
are the python commands to run the conversion.


```
Open Slicer
View > Python Interactor

>>>import sys
>>>os.chdir("path/to/ImageQuizzer/PrePost_Processing")

		for single run - one dicom series
>>>sys.argv=["ConvertDicomToNiiVolume.py","-i","path/to/input/dicom/folder","-o","path/to/output/folder"]
>>>exec(open("ConvertDicomToNiiVolume.py").read())

		for multiple runs
>>>sys.argv=["ConvertDicomToNiiVolume.py","-b","path/to/batchfile.csv"]
>>>exec(open("ConvertDicomToNiiVolume.py").read())

```

#### Batch file syntax

To run this conversion utility multiple times, create a comma separated values (csv) file
with the syntax as follows:

```
parent database folder, input dicom folder 1, output nii volume folder 1
parent database folder, input dicom folder 2, output nii volume folder 2
# Comment line
parent database folder, input dicom folder 3, output nii volume folder 3
parent database folder, input dicom folder 4, output nii volume folder 4
...
	(continue for each dicom series to convert)
	
```

Lines beginning with '#' are comment lines and are ignored.

After a batch run, a log file is created in the same directory where the csv batch file is located.
It has the same name as the batch file with 'Log' as the suffix.


####Utility syntax help

```
>>>py ConvertDicomToNiiVolume.py -h

usage: ConvertDicomToNiiVolume.py [-h] [-i PATH] [-o PATH] [-b CsvFilePATH]

ConvertDicomToNiiVolume preprocessor

optional arguments:
  -h, --help            show this help message and exit
  -i PATH, --input-folder PATH
                        Folder of input DICOM files (can contain sub-folders)
  -o PATH, --output-folder PATH
                        Folder to save converted datasets
  -b CsvFilePATH, --batch-csv CSVFILEPATH
                        Full path to csv file for batch processing

```
