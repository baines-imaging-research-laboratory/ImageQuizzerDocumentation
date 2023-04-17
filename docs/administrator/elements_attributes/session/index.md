---
hide:
- toc
---
# Session

## Specs

| |||
|---|---|---|
| **Name** | Session ||
| **Classification** | element ||
| **Parent** | - ||
| **Required** | yes ||
| **Syntax** | <Session\>...</Session\>|... represents Session subelements|

See also: [Page](../page/index.md)

## Description
Session is the root element in the XML tree. It is must exist in the XML quiz file as the outermost element. 
It encompasses all the child [Page](../page/index.md) elements defined for the study.


## Example
```
<Session>
	<Page>
		...
	</Page>
	<Page>
		...
	</Page>
</Session>
```
