---
hide:
- toc
---
# GoToBookmark

## Specs

| || Details |
|---|---|:---:|
| **Name** | GoToBookmark ||
| **Classification** | attribute ||
| **Parent** | <[Page](index.md)\> ||
| **Required** | no ||
| **Syntax** | GoToBookmark="*bookmarkid button_name*" |two strings separated by a space|
| **Associations** | |  |
|  | [BookmarkID](bookmark_id.md)| set on previous page |
|  | [AllowMultipleResponse](allow_multiple_response.md)| |
|  | [PageGroup](pagegroup.md) | |
|  | [RandomizePageGroups](../session/randomize_page_groups.md) | |


## Description
The GoToBookmark attribute belongs to the Page element.
On this page, a button will be visible, giving the user the choice to either proceed with the quiz or navigate back 
to the first preceding page that shares a corresponding BookmarkID string.
If the page to return to has the *AllowMultipleResponse* attribute set to "Y", the user 
will be able to modify their responses.

The syntax for the GoToBookmark attribute is 2 strings separated by a space, enclosed in quotes.
The first string must match the bookmark ID defined on a previous page - where you want the
quiz to restart.
The second string is a label that will appear on the button that is displayed.

If the pages of the study are to be randomized using the Session attribute *RandomizePageGroups* to "Y",
then the PageGroup attribute on this page and on the *GoToBookmark* page must be the same. An exception is when the
PageGroup is "0" for the Page with BookmarkID.

If the Session attribute *RandomizePageGroups* = "N", the PageGroup attribute numbers can be different (or not defined at all).
Before beginning the quiz, the quiz validator will check that the BookmarkID is on a page that preceeds the page with the GoToBookmark attribute.

## Example

See [Bookmarks example](../../examples/example_bookmarks.md)



