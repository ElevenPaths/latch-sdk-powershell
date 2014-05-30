#LATCH SDK INSTALLATION GUIDE FOR PowerShell


##INSTALLING THE MODULE LATCH
###PREREQUISITES 
- PowerShell 3.

- Net Framework 4.

- To get the **"Application ID"** and **"Secret"**, (fundamental values for integrating Latch in any application), it’s necessary to register a developer account in [Latch's website](https://latch.elevenpaths.com). On the upper right side, click on **"Developer area"**. 


###DOWNLOADING THE SDK
 * When the account is activated, the user will be able to create applications with Latch and access to developer documentation, including existing SDKs and plugins. The user has to access again to [Developer area](https://latch.elevenpaths.com/www/developerArea), and browse his applications from **"My applications"** section in the side menu.

* When creating an application, two fundamental fields are shown: **"Application ID"** and **"Secret"**, keep these for later use. There are some additional parameters to be chosen, as the application icon (that will be shown in Latch) and whether the application will support OTP  (One Time Password) or not.

* From the side menu in developers area, the user can access the **"Documentation & SDKs"** section. Inside it, there is a **"SDKs and Plugins"** menu. Links to different SDKs in different programming languages and plugins developed so far, are shown.

###INSTALLING AND CONFIGURING THE SDK

- To install the SDK at sesión level it must be imported with the following command **Import-Module**:
 `Import Module “[path_to_downloaded_files]\LatchPowershellSDK.dll”`

- After importing the libray, one can see the available commands by typing: **Get-Module**.

- Some commands in the list are not shown due to window size, to see them all save the command’s output on a variable.

- One of the commands is **Get-Pair** which is used to pair the Latch user with the Powershell application.

- To run the command, certain parameters are required. Those are the *Application ID* and the *Secret* generated previously when creating our application in the developer area. For simplicity, it’s recommended to save them on separate variables because they will be used in every API call.

- Next, we will use the **Get-Pair** command to pair our new user. The response from the server should be saved in a variable to use it later and access the data.

- When executing the command, a token needs to be provided. This is generated by the user in his mobile application for pairing the service. Once the command is run, if everything goes well, the user will receive a *Service Paired* notification.

- The user’s Latch account is now paired with our PowerShell application. An *AccountId* has been generated accordingly to identify the user in our application. This identificator should be stored in a secure way, it will be used from now on to uniquely identify the user when consulting the Latch API.

- The *AccountId* is present in the response of the **Get-Pair** command. Access it and store it in a secure way.

- The user can now configure the status of his Latch (on/off) and we consult it using the Get-Status command. This command uses the *ApplicationID*, *Secret* and the *AccountId* of the user whose status is to be checked. The server’s response contain’s a *Data* object that contains the requested operation’s status, or an *Error* object with a code and an error message.

- There is more information available about Latch’s API in: [https://latch.elevenpaths.com/www/developers/doc_api](https://latch.elevenpaths.com/www/developers/doc_api).



###UNPAIRING A USER IN PowerShell
To unpair an user from our application execute the **Get-Unpair** command. You will be promted to introduce the *Application ID*, *Secre*t and *AccountId*. Alternatively provide them as parameters. The user will receive a notification indicating that the service has been unpaired. 


##RESOURCES
- For basic information about the use of Latch read our step by step guide.
	1. [English version](https://latch.elevenpaths.com/www/public/documents/howToUseLatchNevele_EN.pdf)
	1. [Spanish version](https://latch.elevenpaths.com/www/public/documents/howToUseLatchNevele_ES.pdf)
