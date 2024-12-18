---
hide:
- toc
---
# Question

## Specs

| |Value|Details|
|---|---|---|
| **Name** | Question |  |
| **Classification** | element ||
| **Parent** | <[QuestionSet](../index.md)\> ||
| **Required** | no ||
| **Syntax** | <Question\>...</Question\>|... represents Question subelements|


## Description

A Question element is a child of a QuestionSet. It contains Option elements which present the question in the quiz display.
It has a Type attribute that defines how to present the [Option](option.md) elements.


### Types and Attributes

All Question elements must have the [Type](type.md) and [Descriptor](descriptor.md) attributes. 
Depending on the type of question, additional attributes may be available. 
For more details, refer to the [Type](type.md) documentation.


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
