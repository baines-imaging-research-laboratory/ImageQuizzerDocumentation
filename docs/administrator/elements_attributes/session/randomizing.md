---
hide:
- toc
---
# Randomizing Pages

## Specs

| || Details |
|---|---|:---:|
| **Name** | RandomizePageGroups ||
| **Classification** | attribute ||
| **Parent** | <[Session](index.md)\> ||
| **Required** | no ||
| **Syntax** | RandomizePageGroups="*option*" ||
| **Options** | N | (default) pages are not randomized |
|             | Y | pages are randomized |


See also:  [Page](../page/index.md), [PageGroup](../page/pagegroup.md),  [RandomizedPageGroupIndices](../../results.md#randomizedpagegroupindices)

## Description

The Image Quizzer provides the ability to randomize the presentation of images for different observers automatically.

By setting the RandomizePageGroups attribute to "Y", and assigning PageGroup numbers 
to the Page elements, the Pages are presented to each observer in a randomized order. 
The same randomized page order is maintained throughout the quiz.
If the user logs out of the quiz session and resumes at a later time, the Pages are not re-randomized.

The randomized PageGroup order is captured and stored in the results quiz file in the RandomizedPageGroupIndices element 
so that the administrator knows the order in which the pages were presented for any observer and can cross-reference the displayed order 
with the original master quiz file Pages.


## Setup

In order to randomize the pages in the quiz, each Page element must have a PageGroup attribute.
The quiz validator will make sure that if the RandomizePageGroups attribute is to "Y", there must be at least 2 unique PageGroup numbers
assigned to different Pages. If not every Page has an assigned PageGroup number, the module will assign the remaining Pages with PageGroup 
numbers consecutively. 

!!! Note
    Question sets defined within a Page are never randomized. They will always appear in the order
    as defined in the Page of the master quiz file.


## Example

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
