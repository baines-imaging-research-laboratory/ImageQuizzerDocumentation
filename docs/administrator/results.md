---
hide:
- toc
---
# Response capture

## Location

When the user first logs in to the Image Quizzer, a results XML file is created with the same
name as the original master XML file. This file is placed in the Users/Username folder that gets created on the first login. 
You will find the Users folder under the directory you defined to be the database directory.

For example, *Observer1* has logged in to run the *ObserverContouringStudy* quiz.
The administrator has placed all the image volumes for this study in the folder named *ImageQuizzerData* (the database directory).
When the user logs in to the quiz session, he/she has to browse to the *ImageQuizzerData* database folder.

![Login screen shot](assets/login-observer1.png)

The results XML file will be found here:

```
.
└─ImageQuizzerData/
   ├─ImageVolumes/
   ├─SlicerDicomDatabse/
   └─Users/
     └─Observer1/
       └─ObserverContouringStudy.xml
```
	
This is a copy of the original master quiz as set up by the administrator.
As the quiz progresses throughout the user's login session, elements and attributes
are added to capture various pieces of information (responses, login times, username etc.)
as described below.

Each time the user exits and resumes the quiz, this results file is copied and renamed with a timestamp suffix
in order to safeguard against hardware issues or power failures.
The file without a timestamp suffix will be the most recent and most complete results file.

!!! note
    The SlicerDicomDatabase folder is created automatically by Slicer 
	when the user logs in to manage information about DICOM data.

## New Elements

### Response

The Response element is created as a child of each Option element.
The type of response captured depends on the [Question Type](elements_attributes/questionset/question/type.md) attribute. 

If the Type is an InfoBox, the response captured for the Option is null.
For  Radio or CheckBox types, the response is a "Y" or "N" value depending on whether the radio button or checkbox has been selected.
If the Type is a Text, IntegerValue, or FloatValue Types the response element will hold the text that the user input into that box.

Also captured as attributes in the Response element are timestamps LoginTime and the ResponseTime.

```
Examples for Response element based on Question Type:

InfoBox:
	<Question Descriptor="Introduction" Type="InfoBox">
		<Option>
			Using the Segment Editor tab, create a contour for displayed image
			<Response LoginTime="20230317_15:56:40.964017" ResponseTime="20230317_15:58:27.114871"/>
		</Option>
	</Question>
	
Radio
	<Question Descriptor="Assessment" Type="Radio">
		<Option>
			Injury
			<Response LoginTime="20230317_15:56:40.964017" ResponseTime="20230317_16:00:22.706985">Y</Response>
		</Option>
		<Option>
			Recurrence
			<Response LoginTime="20230317_15:56:40.964017" ResponseTime="20230317_16:00:22.706985">N</Response>
		</Option>
	</Question>

CheckBox
	<Question Descriptor="High Risk Features:" Type="CheckBox">
		<Option>
			Enlarging opacity
			<Response LoginTime="20230317_15:56:40.964017" ResponseTime="20230317_15:57:08.896963">Y</Response>
		</Option>
		<Option>
			Bulging margin
			<Response LoginTime="20230317_15:56:40.964017" ResponseTime="20230317_15:57:08.896963">Y</Response>
		</Option>
		<Option>
			Sequential enlargement
			<Response LoginTime="20230317_15:56:40.964017" ResponseTime="20230317_15:57:08.896963">N</Response>
		</Option>
	</Question>
    

```

### Login

When the user first logs in, a <Login\> element is added to the response XML file.
It holds the login and logout times for the user's session. 

```
<Login LoginTime="20221129_16:35:07.894893" LogoutTime="20221129_17:37:36.548557"/>
``` 

When the user completes the assigned quiz, a *QuizComplete="y"* attribute is added to this element.

```
<Login LoginTime="20221129_16:35:07.894893" LogoutTime="20221129_17:37:36.548557" QuizComplete="Y"/>
``` 

###  RandomizedPageGroupIndices

The <RandomizedPageGroupIndices\> element is added to the response XML file under the <Session\> element
if the RandomizePageGroups attribute was set to "Y" in the Session element. The
element holds the list of integers reflecting the randomized order of Page Groups used to direct the order of display of the quiz pages.
If this element is not present, then randomizing of pages was not done and the Image Quizzer
presented each page in the order defined in the original master quiz XML file.

## New Attributes

### UserName

Once a user has logged in to the Image Quizzer, the attribute _UserName_ will be added 
to the Session element
capturing the Windows defined user name. This allows you to keep track of who the XML
results quiz file belongs to, as long as each user has his/her own login profile.

```
<Session UserName="Observer1">
	<Page>
		...
	</Page>
</Session>
```
