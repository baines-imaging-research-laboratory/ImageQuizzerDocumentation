---
hide:
- toc
---
# Image

## Specs

| |Value|Details|
|---|---|---|
| **Name** | Image |  |
| **Classification** | element ||
| **Parent** | <[Page](../page/index.md)\> ||
| **Required** | no ||
| **Syntax** | <Image\>...</Image\>|... represents Image subelements|




## Description
The Image element is a child of the Page element. There can be multiple images on a Page.
Each image is assigned to a viewing window.

The Image element is not required; however, a QuestionSet element must follow if Image elements exist.
This QuestionSet element can be empty if you wish only to display Images on the Page.

Among the many attributes allowed for the Image element, ID and Type are required.


See also [Page display options](../page/index.md#page-display-options)



## Example

```
<Session>
  <Page ID="Patient 1" Descriptor="MR">
    <Image ID="T1W" Type="Volume">
      ...
	</Image>
	<QuestionSet></QuestionSet>
  </Page>
</Session>
```
