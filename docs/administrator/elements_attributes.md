# Overview

## Session

Session is the root element in the XML tree. It encompasses all the Page elements defined for the study.

```
<Session>
	<Page>
		...
	</Page>
</Session>
```

Once a user has logged in to the Image Quizzer, the attribute _UserName_ will be added to the element
capturing the Windows defined user name.

```
<Session UserName="Observer1">
	<Page>
		...
	</Page>
</Session>
```


Following are the attributes available for the Session element:

[ROIColorFile](session\roi_colorfile.md)

### Emailing results
[EmailResultsTo](session\email.md)