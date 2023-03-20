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
| **Syntax** | <Question\>||


## Description

A Question element is a child of a QuestionSet. It contains Option elements which present the question in the quiz display.
It has a Type attribute that defines how to present the Options.



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

## Attributes
#####[Descriptor](descriptor.md)
