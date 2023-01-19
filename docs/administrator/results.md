# Results file

When the user first logs in to the Image Quizzer, a results file is created with the same
name as the original file. This file is placed in the User/Username folder that gets created
on the first login.

For example, *Observer1* has logged in to run the *ObserverContouringStudy* quiz.
The administrator has placed all the image volumes for this study in the folder *ImageDatabase*.
When the user logs in to the quiz session, he/she has to browse to the *ImageDatabase* folder.

TODO: Login screen shot

The results file will be found here:

```
.
└─ImageDatabase/
   ├─SlicerDicomDatabse/
   └─Users/
     └─Observer1/
       └─ObserverContouringStudy.xml
```
	
This is a copy of the original quiz as set up by the administrator.
As the quiz progresses throughout the user's login session, elements and attributes
are added to capture various pieces of information (responses, login times, username etc.)
as described below.

!!! note
    The SlicerDicomDatabase folder is created automatically by Slicer to
	manage information about DICOM data.

## UserName

Once a user has logged in to the Image Quizzer, the attribute _UserName_ will be added to the element
capturing the Windows defined user name. This allows you to keep track of who the
results file belongs to, as long as each user has his/her own login profile.

```
<Session UserName="Observer1">
	<Page>
		...
	</Page>
</Session>
```
## Login element

When the user first logs in, a <Login\> element is added to the results XML file.
It holds the login and logout times for the user's session. 

```
<Login LoginTime="20221129_16:35:07.894893" LogoutTime="20221129_17:37:36.548557"/>
``` 

When the user completes the assigned quiz, a *QuizComplete="y"* attribute is added to this element.

```
<Login LoginTime="20221129_16:35:07.894893" LogoutTime="20221129_17:37:36.548557" QuizComplete="Y"/>
``` 

##  RandomizedPageGroupIndices

The <RandomizedPageGroupIndices\> element is added to the results XML file if
the RandomizePageGroups attribute was set to "Y" in the Session element. The
element holds the list of integers used to direct the order of display of the quiz pages.