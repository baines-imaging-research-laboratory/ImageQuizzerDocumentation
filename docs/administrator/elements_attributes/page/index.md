---
hide:
- toc
---
# Page

## Specs

| |Value|Details|
|---|---|---|
| **Name** | Page |  |
| **Classification** | element ||
| **Parent** | <[Session](../session/index.md)\> ||
| **Required** | yes ||
| **Syntax** | <Page\>...</Page\>|... represents Page subelements|

See also: [Image](../image/index.md), [QuestionSet](../questionset/index.md), [Question](../questionset/question/index.md)

## Description
The Page element is a child of the Session element. There can be multiple pages in a quiz session.
Essentially, each Page represents a snap-shot of the screen that the user will see. It defines what Images
and QuestionSets (containing Questions) to display.


![Simple Script Layout](assets/PageLayout.png)




!!! Note "Restrictions"
	A Page element must contain a [QuestionSet](../questionset/index.md) element. This QuestionSet can be empty (no Questions).
	If the Page contains one or more [Image](../image/index.md) elements, the QuestionSet element(s) must be added after all Image elements are defined. 

	Also, if Image elements are assigned to a Page it is required that the combination
	of Page ID with the Image ID is unique across all the Page elements. 




## Page display options


### Questions only - no images

Image elements are not required.

```
Example
-------

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


### Images only - no questions

A QuestionSet element is required if an Image element exists; but, it can be empty
so that the user only sees images.


```
Example
-------

<Session>
  <Page ID="Patient 1" Descriptor="MR">
    <Image ID="T1W" Type="Volume">
      ...
	</Image>
    <Image ID="CT" Type="Volume">
      ...
	</Image>
	<QuestionSet></QuestionSet>
  </Page>
</Session>
```

### Images and questions

The QuestionSet element must follow the Image elements.

```
Example
-------

<Session>
  <Page ID="Patient 1" Descriptor="MR">
    <Image ID="T1W" Type="Volume">
      ...
	</Image>
    <Image ID="CT" Type="Volume">
      ...
	</Image>
	<QuestionSet ID="Observer Study" Descriptor="Brain">
		<Question Type="Radio" Descriptor="Classification">
			<Option>Primary</Option> 
			<Option>Metastasis</Option>
		</Question>
	</QuestionSet>
  </Page>
</Session>
```


## Observer study examples


### Example 1

In some observer studies, each Page represents a different patient.

```
<Session>
  <Page ID="Patient 1" Descriptor="CT">
    <Image ID="CT" Type="Volume">
      ...
	</Image>
	<QuestionSet></QuestionSet>
  </Page>
  <Page ID="Patient 2" Descriptor="CT">
    <Image ID="CT" Type="Volume">
      ...
	</Image>
	<QuestionSet></QuestionSet>
  </Page>

</Session>
```

### Example 2

It could also represent a time point of a Patient's clinical journey (planning, 3 month follow up, 6 month follow up etc.).

Note that each (Page ID , Image ID) is unique.


```
<Session RandomizePageGroups="Y">
	<Page ID="Intro" Description="Instructions" PageGroup="0">
		<Image ID="CT" Type="Volume">
		  ...
		</Image>
		<QuestionSet></QuestionSet>
	</Page>
	<Page ID="PatientA" Description="Planning" PageGroup="1">
		<Image ID="CT" Type="Volume">
		  ...
		</Image>
		<QuestionSet></QuestionSet>
	</Page>
	<Page ID="PatientA" Description="FollowUp 1" PageGroup="1">
		<Image ID="CT" Type="Volume">
		  ...
		</Image>
		<QuestionSet></QuestionSet>
	</Page>
	<Page ID="PatientB" Description="Planning" PageGroup="2">
		<Image ID="CT" Type="Volume">
		  ...
		</Image>
		<QuestionSet></QuestionSet>
	</Page>
	<Page ID="PatientB" Description="FollowUp 1" PageGroup="2">
		<Image ID="CT" Type="Volume">
		  ...
		</Image>
		<QuestionSet></QuestionSet>
	</Page>
	<Page ID="PatientC" Description="Planning" PageGroup="3">
		<Image ID="CT" Type="Volume">
		  ...
		</Image>
		<QuestionSet></QuestionSet>
	</Page>
	<Page ID="PatientC" Description="FollowUp 1" PageGroup="3">
		<Image ID="CT" Type="Volume">
		  ...
		</Image>
		<QuestionSet></QuestionSet>
	</Page>
</Session>
```

