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

The PageGroup attribute can be assigned by the administrator. If it hasn't been defined in the original XML master quiz file,
the Image Quizzer will add this attribute to the results quiz file and assign numbers consecutively starting at '1'. (This is
helpful for cross referencing the [user's annotations results subfolders](../../results.md#annotations-subfolders) which have the PageGroup numbers embedded in the name).

When setting up for randomizing, you can use the PageGroup numbers to group Pages together. For example, if you want to 
randomize patients but each patient has 3 Pages (baseline, follow-up1, follow-up2), you would assign 1 PageGroup number to all 3 Pages.
Another example could be if one patient has images from multiple lesions that are set up to display on different pages.


## PageGroup="0"

Any pages assigned a group number of 0 will always appear at the beginning of the quiz. 
If more than one Page has a page group number of 0, these pages will appear in the order read in.
The remaining pages are randomized. Following are some use cases for assigning pages to PageGroup="0"

* present instructional information that applies to the quiz that follows
* isolate certain images that all observers will see at the beginning of the quiz before randomization in order to establish a baseline


## Example

!!! Note
    See also [randomizing example](../../examples/example_randomizing.md) for a plug and play example.
	
	
Master quiz:

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

