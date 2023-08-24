---
hide:
- toc
---
# PageGroup

## Specs

| |Value|Details|
|---|---|---|
| **Name** | PageGroup |  |
| **Classification** | attribute ||
| **Parent** | <[Page](index.md)\> ||
| **Required** | yes |if <Session\> has the RandomizePageGroups attribute set to "Y"|
| | no |if <Session\> does not have the RandomizePageGroups attribute or it is set to "N" |
| **Syntax** | PageGroup="*value*" | positive integer value |

See also: [Randomizing pages](../session/randomize_page_groups.md),  [RandomizedPageGroupIndices](../../results.md#randomizedpagegroupindices)

## Description

This attribute can be used to keep Pages together and is particularly valuable if you intend to randomize
the presentation of patient images.


For example, consider the situation where patient randomization is desired, and each patient
has 3 Pages (baseline, follow-up1, follow-up2). Assigning a common PageGroup number 
to all three Pages would prevent the separation of these images during the randomization process.
and as a result, the images would be presented sequentially within the quiz.


Another application of the PageGroup attribute is for implementing the Merge Label Maps functionality.
When employing the [MergeLabelMap](../image/merge_labelmaps.md) attribute, it is essential to designate identical PageGroup numbers
to both the Page where contouring is initiated and the Page where the combined contours are displayed.


 If the PageGroup attribute is not defined in the original XML master quiz file,
the Image Quizzer will add this attribute to the results quiz file and assign numbers consecutively starting at '1'.
(This is helpful for cross referencing the [user's annotations results subfolders](../../results.md#annotations-subfolders) which have the PageGroup numbers embedded in the name).


## PageGroup="0"

Any pages assigned a group number of 0 will always appear at the beginning of the quiz. 
If more than one Page has a page group number of 0, these pages will appear in the order read in.
The remaining pages are randomized. Following are some use cases for assigning pages to PageGroup="0"

* present instructional information that applies to the quiz that follows
* isolate certain images that all observers will see at the beginning of the quiz before randomization in order to establish a baseline


## Example

Following is an overview of PageGroup assignments if setting up for randomizing:

```
<Session RandomizePageGroups="Y">
	<Page ID="Intro" Description="Instructions" PageGroup="0">
		...
	</Page>
	<Page ID="PatientA" Description="Planning" PageGroup="1">
		...
	</Page>
	<Page ID="PatientA" Description="FollowUp 1" PageGroup="1">
		...
	</Page>
	<Page ID="PatientB" Description="Planning" PageGroup="2">
		...
	</Page>
	<Page ID="PatientB" Description="FollowUp 1" PageGroup="2">
		...
	</Page>
	<Page ID="PatientC" Description="Planning" PageGroup="3">
		...
	</Page>
	<Page ID="PatientC" Description="FollowUp 1" PageGroup="3">
		...
	</Page>
</Session>
```


Randomized Page Groups for User 1 :  RandomizedPageGroupIndices="3,1,2"
(The unique PageGroup numbers are the indices that are randomized).

The user would see Pages presented in this order:

```
Intro_Instructions
PatientC_Planning
PatientC_Followup 1
PatientA_Planning
PatientA_Followup 1
PatientB_Planning
PatientB_Followup 1
```

### See also:

- [merging label maps example](../../examples/example_merge_labelmaps.md)
- [randomizing example](../../examples/example_randomizing.md)
	
