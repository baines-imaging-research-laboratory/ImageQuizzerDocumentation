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
there will be a pop-up window asking if the user is ready to email the results.

![FinishButtonPopup](../assets/email/FinishButtonPopup.png)

![EmailResultsPopup](../assets/email/EmailResultsPopup.png)
