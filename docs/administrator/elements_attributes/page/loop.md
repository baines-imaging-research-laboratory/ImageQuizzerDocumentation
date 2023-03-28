---
hide:
- toc
---
# Loop

## Specs

| ||Details|
|---|---|---|
| **Name** | Loop ||
| **Classification** | attribute ||
| **Parent** | <[Page](index.md)\> ||
| **Required** | no ||
| **Syntax** | Loop="*option*" |  |
| **Options** | N | (default) looping is disabled |
|             | Y | looping is enabled |

## Description

Looping is useful for example in situations where you are presenting images with a number of lesions and
want the observer to contour and answer questions for as many as he/she can find.

### For the user

When a page has looping enabled, the user will see a **Repeat** button next to the 'Next' button.
By pressing 'Repeat', this allows the observer to repeat the quiz questions and required annotations for another region of interest.
Once the information for all ROIs has been completed the user presses 'Next' to move on to the next page of images and questions. 


### For the administrator

When the user presses **Repeat**, the module will capture the responses of the current Page then make a copy of the Page
and insert it into the results quiz file. The copied page has a suffix attached to the Page ID attribute to identify it
as a repeated page. This prefix includes a repition number (e.g. PageID-Rep1).  Any
Response elements, LabelMapPath and MarkupLinePath elements are stripped out of the copied Page - ready
for the user's new responses.


## Example

See [Looping example](../../examples/example_looping.md#script-example) for a plug and play script example.

You can also see what the [results file](../../examples/example_looping.md#results) looks like 
with the added attributes after the user has used the repeat button.
