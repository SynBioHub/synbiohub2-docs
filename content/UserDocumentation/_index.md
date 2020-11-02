---
title: "User Documentation"
date: 2020-09-04T20:30:59+05:30
draft: true
weight: 20
---

This section contains instructions on how you can implement various operations ranging from Registering onto SynBioHub to uploading your genetic designs on SynBioHub, by using the User Interface of SynBiohub. The Sub-sections are as follows:

## 1. Registering & Updating your account

### 1.1 Registering your Account

Following Steps need to be followed for registering onto SynBioHub:

1. Go to [SynBioHub](https://synbiohub.org/).

2. Click on the **Login or Register** option on the top Right Hand Side of your Screen.

3. Enter the following details to complete your registration process: Full Name, Affiliation(Optional), Email Address, Username & the password. 

4. When you need to login into your SynBioHub Account, click on the "Login or Register" option. Then you need to enter your Email Address and your password to Access your account.

### 1.2 Updating your Account

If you ever need to update your Account, the following steps need to be followed:

1. You need to be logged in to perform the updation, so follow the previous set of steps to login, if you aren't logged in to your account.

2. Then, click on the **Profile** option. It'll redirect you onto a page, which contains your profile.

3. On this page, update whichever section you want to, and the click on the **Save** option at the bottom to successfully update your profile.

## 2. Searching for Information

### 2.1 Searching with the help of Keywords

To Search amongst various Designs and Collections, follow these steps:

1. Go to SynBioHub's [Home Page](https://synbiohub.org/).

2. In the Search box, enter the Keywords for the design you want to search for and click on the search button.

3. Subsequently, a list of results matching the keywords that you've entered shall appear on your screen.

4. Select the desired Collection/Design from the list.

### 2.2 Sequence Search

To Search using a Sequence, follow these steps:
1. Click on the *Sequence Search* option, available right below the Search Box, which appears after you search for a keyword.

2. Enter the Sequence in the box given at the top or upload a *FASTA/FASTQ* file, by clicking the choose file option just below the box.

3. Then, choose the type of *Search method* from **Global** or **Exact**.

4. Subsequently, customise the *Number of Results*, *Minimum length of the Sequence* & the *Maximum length of the Sequence*.

5. Then, set the value for *Number of failed hits* before stopping. To understand its significance, hover the pointer over the info button to its immediate right.

6. Fill up the *percentage match*, by entering a value between 0 & 1.

7. Finally, select the *Pairwise Identity definition*. To understand its significance, hover the pointer over the info button to its immediate right.

### 2.3 Advanced Search

To perform an Advanced Search, follow these steps:
1. Click on *Advanced Search* option, available right below the Search Box, which appears after you search for a keyword.

2. Now, select the *Object Type* & *Creator* for the design you want to search for.

3. Then, fill up the *Created After* & the *Created Before* options.

4. Also, fill up the *Modified After* & the *Modified Before* options.

5. Fill up an ID/Name/Description for the design you want to search for.

6. Select it's *type* as well as the *role* from the dropdown.

7. Also, try to select some *collections*, that you think that design might be a part of.

8. You may apply customized filters for the design you want to search for. For that purpose, a few blank filtering columns have been provided.

### 2.4 SPARQL Search

To perform a SPARQL Search, the following steps should be followed:

1. Go to SynBioHub's [SPARQL Search Page](https://synbiohub.org/sparql).

2. Since, SPARQL is a query language, hence it'll query Synbiohub's databases for the designs that you're looking for.

3. You need to provide a **SELECT** statement, the syntax for which is as follows:

```
  SELECT  # makes up the headers of the table
	
        ?def # directs you to the design for which you're looking for 
	
        ?displayId # This statement displays the Id the design
	
        ?title # displays the title of the design
	
        (count(?def) as ?count) # displays the count parameter for the design
	
        ?role # displays the role of the design    

```
4. Next, you need to provide a **Where** statement, which shall contain all the specific details with respect to the **SELECT** statement. The Syntax is as follows:

``` 
WHERE { 
  	 ?s sbol:component ?comp # Searching for **sbol** components

  	 ?comp sbol:definition ?def # provides the link to that component

         filter (regex(?role, 'http://identifiers.org/so/SO:')) 

	 OPTIONAL {?def sbol:role ?role} # Defines the role

	 OPTIONAL {?def sbol:displayId ?displayId} # gives the ID of the design

	 OPTIONAL {?def dcterms:title ?title} 
  }
```
*In the previous section, we've discussed the case of searching for SBOL components. Therefore, if you want to search for other types of designs, just replace SBOL with your prefered type.* 


## 3. Viewing & Downloading the Information

### 3.1 Viewing the Information

1. Go to [SynBioHub's home page](https://synbiohub.org/).

2. Search for the design or click on *browse the collections*.

3. In case of collections, you can search and view the various designs under each respective collection. Also, several other details such as references, attachments, & various other properties can be viewed.

4. In the case of designs, select the design for which you want to view the Information. Similar to collections, you can view the various details such as references, functional components, interactions, the collection to which this design belongs to, attachments and various other properties. 

### 3.2 Downloading the Information

1. Go to [SynBioHub's home page](https://synbiohub.org/).

2. Scroll down and Click on *browse the collections* option.

3. On this page you'll see several public as well as private(optional) collections.

4. Select the collection which you want to view/download. 

5. On the left hand side of the page you'll see the **Download** option.

6. Based on your requirement, you can download the whole collection or just a specific design.

7. To download a design, hover over the download option and a dropdown containing various options for downloading the design will be there. Select your preferred option and the download will begin automatically.


## 4. Submitting, Managing & Updating Submissions

### 4.1 Submitting 

For submitting your designs to SynBioHub, following steps need to be followed:

1. Go to SynBioHub's [home page](https://synbiohub.org/).

2. Click on **Submit** and it'll direct you to the Submit page.

3. You van either submit your designs to an existing collection or create a new one.

#### 4.1.1 Creating a new Collection

1. On the submit page, select the *Create a new collection* option.

2. Then, give your collection a name and a description.

3. Subsequently, provide a collection ID, version as well as the Citations(if any).

4. Then upload your file in the form of SBOL/GENBANK/GFF3/FASTA/ZIP file and select the handler.

5. Finally, you may choose to Overwrite the existing objects by checking the box given in the end.

6. Click on Submit.

#### 4.1.2 Submitting to an existing collection

1. On the submit page, click on *Submit to an existing collection* option.

2. Then, select to the collection you want to submit your design to.

3. Select the design that you want to submit.

4. You may choose to overwrite the existing objects in a collection.

5. Then, click on submit.

### 4.2 Managing

1. To view the designs that you've uploaded, visit [this](https://synbiohub.org/manage) page.

2. Here, you can view your collections, make them public as well as delete the collection.

3. To make your collection public, click on **Make Public**.

4. To delete your collection, click on **Remove**.

5. Click on the collection's name, to view your design's.

### 4.3 Updating


#### 4.3.1 Updating Collections

1. To update your collections, click on the collection that you want to update.

2. You can delete a specific design, by selecting the delete, just besides the name of that design.

3. If you want to edit, the collection's name or its description, you can do so by clicking on the edit sign just beside them.

4. You can also add description, notes, sources or references to the collection by clicking on the the *Details* sub-section just by scrolling down.

5. Also, you may upload attachments to the collection by clicking on the *Attachments* sub-section, then uploading the files that you want to attach and then selecting the *Attach* option.

6. You may add an owner to your collection, who can see as well edit your collection.

#### 4.3.2 Updating Designs

1. Navigate to the page of that collection, whose design you want to update.

2. Then, select the design that you want to update.

3. Follow the steps 3-6 as given in section 4.3.1 to update your design.

## 5. Editing you Submissions




 

