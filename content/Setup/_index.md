---
title: "Setup"
date: 2020-09-04T20:30:59+05:30
draft: true
weight: 15
---

### Web-Of-Registries in SynBioHub

SynBioHub also supports the Web of Registries concept i.e, the idea of multiple separate repositories linked together by shared common semantics. In the case of SynBioHub, SBOL is used to support the common exchange of data, thus positioning SynBioHub to support the development of synthetic biology workflows by acting as a source and a storage facility for designs.

Hence, Web Of registries enables communication between SynBioHub instances. Sharing designs between instances of SynBioHub is also further facilitated via the Web of Registries service. Federated SynBioHub instances can reference parts in the public graph of other federated instances. In order to support this federation, the Web of Registries service maintains information about all SynBioHub registries, such as their name, description, administrator email, URI prefix, and uniform resource locator(URL). 

Any SynBioHub can access the Web Of Registries to determine information about all registered SynBioHub instances. If a design references a part within another synbiohub instance, the information about this part can be fetched in order to render this design information locally and provide links to the corresponding design information page for this part.

When a new SynBioHub instance wishes to join the Web of Registries, it sends its information to the Web of Registries service, and all the Web of Registries curators are alerted via email that there is a new repository pending approval. Once the repository has been approved, its information is broadcast to all other registries in the Web of Registries. Anybody can access the current list of registries through an HTTP GET request. Once registered, an instance of SynBioHub is able to locate designs within any other instance that is registered with the Web of Registries.



SynBioHub demonstrates the application of this harmonized data exchange through existing repositories, hence envisaging a wider, integrated ecosystem of biological part information shared across a plethora of different repositories with different capabilities.


### Setting up Sendgrid 

In order to enable SynBioHub to send account-related emails, you need a SendGrid account and API key. The following steps need to be executed, in order to setup Sendgrid:-

1. Visit [this](www.sendgrid.com) website.

2. Select the *Sign up* option, in case you're using it for the first time.

3. Enter you Email Address and password as well as select the captcha for verification. 

4. Fill up all the details about yourself on the "Tell Us About Yourself" page.

5. Then, after filling up all the details correctly it'll re-direct you to your dashboard and send a confirmational Email.

6. Click on the *Settings* options on left hand side of the page.

7. Then select the *Create an API key option".

8. It'll prompt you to give your API key a name. Also, you can customize the API key permissions.

9. After completing these steps, click on Create and View. 

10. The API key is shown only for once due to security reasons, so try to save it at a safe place.

11. Your API key has been created, and hence ready to use!!

