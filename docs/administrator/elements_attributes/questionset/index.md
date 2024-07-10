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
| **Required** | yes | |
| **Syntax** | <QuestionSet\>...</QuestionSet\>|... represents QuestionSet subelements|
| | |  QuestionSet can be empty|


## Description

A QuestionSet element contains one or more Question elements. 
QuestionSet is a required element and it must follow all Image elements if they exist.


There can be more than one question set element for a page. If so, when the user presses the Next button,
the displayed images remain and the next set of questions appear. This provides the administrator with the ability to break up
a long list of questions reducing the use of the scroll bar by the observer when responding to questions.

See also [Page display options](../page/index.md#page-display-options)



## Example

```
<Session>
  <Page ID="Patient 1" Descriptor="CT">
		<QuestionSet ID="Observer Study" Descriptor="Brain">
			<Question Type="Radio" Descriptor="Classification">
				<Option>Primary</Option> 
				<Option>Metastasis</Option>
			</Question>
		</QuestionSet>
  </Page>
</Session>
```

