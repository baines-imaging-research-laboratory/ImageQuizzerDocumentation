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

## Description

By setting the RandomizePageGroups attribute to "Y", the Image Quizzer module will to randomize the 
indices Page elements defined in the quiz XML file. Then when the user runs the quiz,
the pages will be displayed in the randomized order. This can be useful if your 
observer study needs to have images presented to different observers in a random way.

The randomized indices 
are recorded in the results quiz file in the [RandomizedPageGroupIndices](../../results.md#randomizedpagegroupindices) element 
so that the administrator knows the order in which the pages were presented to the user.



## Setup

In order to randomize the pages in the quiz, each [Page](../page/index.md) element must have a [PageGroup](../page/pagegroup.md) attribute.


## Example

```
			This function will shuffle the original list as read in from the quiz xml,  that holds the
            "[page number,questionset number, page group number, rep number]" according to the randomized index list input.
            The question sets always follow with the page, they are never randomized.
            The page groups are randomized. 
                 If more than one page has the same group number, they will remain in the order they were read in.
            
            eg.     Original XML List         Randomized Page Group indices      Shuffled Composite List
                       Page   QS   Grp   Rep             Indices                   Page   QS   Grp   Rep
                       0      0     1     0                 2                       2     0     2     0
                       0      1     1     0                 3                       2     1     2     0
                       1      0     1     0                 4                       3     0     2     0
                       2      0     2     0                 0                       4     0     3     0
                       2      1     2     0                 1                       4     1     3     0
                       3      0     2     0                                         0     0     1     0
                       4      0     3     0                                         0     1     1     0
                       4      1     3     0                                         1     0     1     0
```


Page 0

Grouping of patients (pages) groups and subgroups

randomizing indeces

!!! note
    Pages are coded 0 based in the code and the captured indeces that are stored
	in the results file reflects the counting of Page elements starting at 0.
	However, the Page folders stored in the Users results folder starts at index 1.
	
!!! bug
    BUG - indices are not updated when reps are added !!!!!!!
	
