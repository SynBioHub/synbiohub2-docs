---
title: "Setup"
date: 2020-09-04T20:30:59+05:30
draft: true
weight: 15
---

When you'll first install SynBioHub locally and navigate to ```http://localhost:7777/```, you shall be directed to the setup page.

Over there you'll see a welcome message saying, **Congratulations, SynBioHub is successfully installed!**

Then, you need to fill out some details for configuring your local instance, which are as follows:

## 1. Branding Your SynBioHub

| Parameter  | Description  |
|---|---|
| Instance Name | You can give a name to your local instance as per your convenience. Try to provide something descriptive to identify the kind of parts your SynBioHub instance will store. This parameter can even be changed later.    |
| Pick a color  | You can also choose a colour for you SynBioHub instance. This color shall be used to theme your SynBioHub instance. The default colour for SynBioHub is hue. If you want to change it just click on the color bar. A dropdown shall appear, enabling you to choose the color your own choice. |
| Write a Welcome Message |  You could also provide a welcome message for the users of your instance. This may contain a brief description of what parts does your SynBioHub contain or any other brief message that you want to give to the users about your local instance. This shall be displayed on the home page of your local instance. Html tags can also be used while writing the welcome message.|
| Upload a logo| Then, is the option of uploading a logo for your instance. For uploading a logo of your choice, just click on **upload file**. A popup menu shall appear and then you can choose the picture from your machine. Kindly make sure that for best results, upload a SVG or high resolution PNG image.|
| Allow public account creation | Just below the upload a logo option, is situated a check box displaying the message, **allow public account creation**. This shall enable all the users accessing your instance, to create an account on it and hence perform function such as creating collection, submitting various types of records, etc.. To enable public account creation, just check the box, right besides this message.|
---------------------------------------------------

## 2. Technical Details


| Parameter | Description |
|-----------|-------------|
| Instance URL | This displays where this SynBioHub instance is hosted on your machine, so we can assign URLs to your submissions. By default, it has been assumed that your instance is hosted at ```localhost:7777/```. If your instance is not hosted over there, then you can change it.|
| URI Prefix | There is a need to know need to know how to prefix URIs of objects stored in this SynBioHub. Its default is the same as the URL, and should only be changed if you are shadowing another instance. Hence, you can change it as per your convenience. |
| [Virtuoso INI](http://olafhartig.de/brTPF-ODBASE2016/virtuoso.ini) | This basically is configuration file for the OpenLink Virtuoso VDBMS Server. There is a need to know where the Virtuoso INI is stored. By default it is guessed to be ```/etc/virtuoso-opensource-7/virtuoso.ini```. If this is not true, you can change it as per your convenience.|
| Virtuoso Data Directory |  Displays the location of Virtuoso DB directory. By default it is set to ```/virtuoso```. If this is incorrect, you can change it as per your convenience.| 
---------------------------------------------------------------

## 3. Creating Your First User Account

You need to create a user account that will have the first privileged access to your SynBioHub local instance. For that you need to enter certain details, which are as follows:

| Option Name | Description   |
|-------------|----------|
| Full Name   | Enter the name of the user|
| Affiliation(Optional)| You can enter the name of the university/institute that you're currently affiliated to| 
| Email Address| Enter the Email Address, through which you want to get registered. If in future you forget your login credentials, then this shall be used for sending a recovery password for your account| 
| Username | You have to enter a username of your own choice. This shall be displayed on the record page of every record that you submit|
|Password | Enter a password (preferably a strong one) for keeping your user account safe|
---------------------------------------------------------------------------------------------------

## 4. Setting up External Authorisation Provider

External authentication basically, is the use of third-party authentication sources to decide whether a user should be allowed access to a system, and often what level of access an authenticated user enjoys on a system.

For a SynBioHub local instance, you've got 2 options i.e, **none** or **google**. If you'll select none as your preferred authorisation provider then, you simply have to click **continue**. 

To be able to use Google for authentication, you first need to register with them. This is done at their developer **[console](https://console.developers.google.com/)**. To learn more about using google as your service provider, click **[here](https://docs.identityserver.io/en/release/quickstarts/4_external_authentication.html#adding-google-support)**. Now, if you select google as your preferred authorisation provider, then the you have to provide certain values for the following options:

| Option Name         | Description        | 
|---------------------|--------------------|
| Client ID | This is an identification string that is provided to every user by google. This number is unique for each user. For an example: **XXXXXXXXXXXXXXXXXXXX.apps.googleusercontent.com**, this is how a client ID provided by google looks.|
| Client Secret | Client secret values are created for the app by the external authentication provider when the app is registered with the provider and it is a unique identification string. |
| Redirect URL | This is the path in your application that users are redirected to after they have authenticated with Google. The path will be appended with the authorisation code for access. It must have a protocol and cannot contain URL fragments or relative paths. Also, make sure it is not a public IP address.|
-------------------------------------------------------------------------------

Once, you've filled all the details, click **continue**. This will redirect you to the home page of your SynBioHub local instance.   






