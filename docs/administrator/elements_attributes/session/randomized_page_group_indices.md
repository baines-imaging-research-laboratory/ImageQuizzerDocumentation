---
hide:
- toc
---
# RandomizedPageGroupIndices

## Specs

| || Details |
|---|---|:---:|
| **Name** | RandomizedPageGroupIndices ||
| **Classification** | element ||
| **Parent** | <[Session](index.md)\> ||
| **Required** | no | **use with caution** to change Page display order |
| **Associations** | [RandomizePageGroups](randomize_page_groups.md) |  |



## Description

This is a special element available to administrators to force the display of Pages to be in a specified order.
It holds a list of integers reflecting the order for displaying PageGroups.

This element is related to Image Quizzer's randomization functionality. Normal use would be to set the [RandomizePageGroups](randomize_page_groups.md) attribute of Session to "Y"
and let the module generate a randomized list of PageGroup numbers which is then stored in the quiz results file in the
RandomizedPageGroupIndices element. See also [Quiz Results](../../results.md#randomizedpagegroupindices) for this element.

## Forcing a page group order - overriding XML sequential Page layout

There are certain instances where you may want to display the quiz pages in a certain order that does not follow the sequential layout in the XML Master Quiz.
To do this, set the **RandomizePageGroups** attribute to "Y" in your master quiz and add a **RandomizedPageGroupIndices** element with the 
desired order of the page group numbers. This element must follow all the Page elements in the master quiz file.

Even though you have enabled **RandomizePageGroups** to "Y", the application assumes randomization has already
been done with the existence of the **RandomizedPageGroupIndices** element. 
The quiz will use the order laid out in this element. (Note: Any Pages with PageGroup="0" will always be displayed first. )

### Example

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
	<RandomizedPageGroupIndices>3,1,2</RandomizedPageGroupIndices>
</Session>
```

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
