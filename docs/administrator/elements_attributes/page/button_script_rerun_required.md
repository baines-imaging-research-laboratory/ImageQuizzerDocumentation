---
hide:
- toc
---
# ButtonScriptRerunRequired

## Specs

| || Details |
|---|---|:---:|
| **Name** | ButtonScriptRerunRequired ||
| **Classification** | attribute ||
| **Parent** | <[Page](index.md)\> ||
| **Required** | no ||
| **Syntax** | ButtonScriptRerunRequired="*option*" |  |
| **Options** | N | (default) Button script rerun is not required |
|             | Y | Button script rerun is required |
| **Dependencies** | [AllowMultipleResponse](allow_multiple_response.md) | set to "Y" allows for re-click of Button type question|
| **Associations** | [Question Type](../questionset/question/type.md)| set to "Button" |


## Description
ButtonScriptRerunRequired is an attribute of the Page element. 
When set along with the AllowMultipleResponse="Y" attribute, it forces the user to re-execute the linked script
for a Button-style Question whenever this Page is visited. This revisit may occur when resuming the quiz, or
when selecting the Previous or GoToBookmark buttons. 

