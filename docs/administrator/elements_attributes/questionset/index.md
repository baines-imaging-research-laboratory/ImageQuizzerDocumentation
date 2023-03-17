---
hide:
- toc
---
# QuestionSet

## Specs

| |Value|Details|
|---|---|---|
| **Name** | QuestionSet |  |
| **Classification** | element ||
| **Parent** | <[Page](../page/index.md)\> ||
| **Required** | no ||
| **Syntax** | <QuestionSet\>||


## Description

A QuestionSet element contains one or more Question elements. This is not a required element.
A Page can be set up to only display images.

There can be more than one question set element for a page. If so, when the user presses the Next button,
the displayed images remain and the next set of questions appear. This provides the administrator to break up
a long list of questions reducing the use of the scroll bar by the observer to display and respond to all questions.



## Example

```
<Session>
  <Page ID="Patient 1" Descriptor="CT">
    <QuestionSet ID="Post radiation" Descriptor="General Assessment">
	  ...
	</QuestionSet>
  </Page>
</Session>
```

## Attributes
#####[ID](id.md)
#####[Descriptor](descriptor.md)
