---
hide:
- toc
---
# BookmarkID

## Specs

| || Details |
|---|---|:---:|
| **Name** | BookmarkID ||
| **Classification** | attribute ||
| **Parent** | <[Page](index.md)\> ||
| **Required** | no ||
| **Syntax** | BookmarkID="*string*" ||
| **Associations** | |  |
|  | [GoToBookmark](go_to_bookmark.md)| set on subsequent page |
|  | [AllowMultipleResponse](allow_multiple_response.md)| |
|  | [PageGroup](pagegroup.md) | |
|  | [RandomizePageGroups](../session/randomize_page_groups.md) | |


## Description
BookmarkID is an attribute for the Page element. It is used in conjuction with the GoToBookmark attribute
allowing the user to return to this bookmarked page. If the attribute *AllowMultipleResponse* is set to "Y"
on this page, the user could then modify the original responses.

If the pages of the study are to be randomized using the Session attribute *RandomizePageGroups* to "Y",
then the PageGroup attribute on this page and on the *GoToBookmark* page must be the same.

## Example

See [Bookmarks example](../../examples/example_bookmarks.md)

### Use Case Examples

For instance, users could answer questions on one page initially.
Following that, subsequent pages introduce specific skills.
Once users explore this content, they are provided with the chance to 
revisit the bookmarked page and modify their responses.
