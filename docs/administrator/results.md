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
