## Automatic e-mail of results

A feature of the Image Quizzer is to have a user's results folder emailed to the administrator upon completion of the quiz.

In order to activate this feature, there are 2 steps required.

* A smtp_config.txt file must be created in the directory: __.../ImageQuizzer/Resources/Config__
Currently in this directory, you will find smtp_config_template.txt.

smtp_config_template.txt

```
#Image Quizzer email utility smtp config file

[smtp]
host=your_host_server
username=address_of_your_host_email_account@example.com
password=app_password_of_your_host_email_account
port=your_host_server_port_here


```

* The administrator must add the 'EmailResultsTo' attribute to the Session element in the quiz xml file. 

```
<Session EmailResultsTo="youremailaddress@example.com">
    <Page ID="Patient 1" Descriptor="Multiparametric_MRI">
        <Image Type="Volume" ID="T2W" >
    ...
```

With these pieces in place, once the user has completed the quiz and has pressed the 'Finish' button,
there will be a pop-up window to confirm that the user wants to exit the quiz.

![FinishButtonPopup](../assets/FinishButtonPopup.png)

Pressing the OK button to exit will mark the quiz as complete and all responses are locked.
Then the user is then prompted to email the results.

![EmailResultsPopup1](../assets/EmailResultsPopup.png)
![EmailResultsPopup2](assets/EmailResultsPopup.png)
![EmailResultsPopup3](./assets/EmailResultsPopup.png)
![EmailResultsPopup4](/administrator/assets/EmailResultsPopup.png)

If 'Yes' is pressed, the module will zip up the user's quiz results folder (quizname.zip)
and place it in the same folder where the quiz results are located.
```
.../path/to/defined/image/database/Users/username/quizname.zip
```
This zip file will be attached to the email contents and sent to the email address assigned to the
'EmailResultsTo' attribute.

If the user presses 'No' to the email prompt, the user can still reopen the quiz
to email the results at a later time. When restarting the Image Quizzer to review
a completed quiz, the following prompt will appsear:

![ReopenCompletedQuizWithEmail](../assets/ReopenCompletedQuizWithEmail.png)

If 'Yes' is pressed, the user can review the images but recorded responses can not
be modified. During the review the user can either press Exit to start the exit/email processes or
press Next until the last Page and QuestionSet is reached to start the exit/email stage.

If 'No' is pressed, the module will take you directly to the exit and email stage.