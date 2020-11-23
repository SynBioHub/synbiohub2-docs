---
title: "User Documentation"
date: 2020-09-04T20:30:59+05:30
draft: true
weight: 20
---

This section contains instructions on how you can implement various operations ranging from registering onto SynBioHub to uploading your genetic designs on SynBioHub, by using the user interface of SynBioHub. The sub-sections are as follows:

## 1. Searching for Information

There are a variety of ways to search for information in SynBioHub, such as using keywords, sequences, advanced searches and  SPARQL queries. They're explained in detail as follows:

### 1.1 Keyword Search

To search amongst various records, follow these steps:

1. Navigate to SynBioHub's home page.

2. In the search box, enter the keywords for the record you want to search for and click on the search button.

3. Subsequently, you shall be directed to a list of records matching the keywords that you've entered. For each record, the first thing that is displayed is the name. Just below the name, the ID, version and type of the record shall be displayed. Just below, you'll be able to see a brief description about the record provided by the owner of that particular record. On the right hand side, there is an indicator displaying whether it is a **public**, **private** or a **remote** record. Being private means that the record is available on a private repository i.e, to a specific user only and if it is labeled as public means it is available to all the users of SynBioHub. If the record is available to all the users but on another instance of SynBioHub, then it shall be labeled as remote

4. If you see the record you want, you can select it else, you can select next or any of the other page numbers to navigate to the other pages to look for the record you desire amongst other records.

5. On this page, you're also able to see other search options, such as sequence, advanced or SPARQL search, which are described in detail in the upcoming sections.

### 1.2 Sequence Search

On the search results page, there is button labeled as **sequence search**. Clicking on that button will direct you to a page containing a list of sequence search options. To search using a sequence, you can provide the values for the options, as described in the table below:


| Option Name         |              Description     |
|---------------------|------------------------------|
| Enter Sequence      | Enter the sequence or upload a **[FASTA](https://en.wikipedia.org/wiki/FASTA)/[FASTQ](https://en.wikipedia.org/wiki/FASTQ_format)** file, by clicking the choose file option just below the box. This shall search only for exact matches of the sequence. Your entry must be the first key/value pair   |
| Search Method       | You can choose the perspective of your search. You can perform a **global** search or an **exact** search. The exact search shall display, those records which are an exact match to the sequences that you've entered and the global search search will display those results which have even the smallest of the similarities to the sequence that you've entered.  |
|  Number of Results                   | You may customise the number of results, the value for which must not exceed 10,000. This translates into the maximum number of hits to accept before stopping the search. Kindly note that, higher the value, the longer the runtime.  |
| Minimum Sequence Length |You need to enter the minimum sequence length. This value basically specifies the minimum length of the sequence, which you want to search for. Values for this parameter should not exceed 100,000. |
| Maximum Sequence Length|You need to enter the maximum sequence length. This value basically specifies the maximum length of the sequence, which you want to search for. Values for this parameter should not exceed 100,000. |
| # of failed hits before stopping|Then, you need to enter the maximum number of non-matching target sequences, that are to be considered before the search is halted. This option works in pair with the flag above. The search process sorts the target sequences by decreasing number of k-mers they have in common with the query sequence, using that information as a proxy for sequence similarity. After pairwise alignments, if none of the first x examined target sequences pass the acceptation criteria, the search process stops for that query (no hit). If this flag is set to a higher value, more target sequences are considered. If the flag above and this flag are both set to 0, the complete database is searched. |
| Percent Match | Then, we have is the *percentage match*, which has a value between 0 and 1. This is the value of pairwise identity that must match with the sequence, otherwise the sequence is rejected. |
| Pairwise Identity Definition | You may select the value for this attribute from the following options: 1) **Default**: Edits distance excluding the terminal gaps,   2) **CD-HIT definition**: Considers the following ratio: (matching columns) / (shortest sequence length),   3) **Marine Biological Lab definition**: counts each gap opening (internal or terminal) as a single mismatch, whether or not the gap was extended: 1.0 - [(mismatches + gap openings)/(longest sequence length)],   4) **BLAST Definition**: equivalent to edit distance for global pairwise alignments    |
-------------------------------------------------------------------------------
After filling up the desired options, press the **search** button to get the search results.



                                                                                               


### 1.3 Advanced Search

On the search results page, there is button labeled as **advanced search**. Clicking on that button will direct you to a page containing a list of advanced search options. To search using advanced parameters, you can provide the values for the option as described in the table below. The records that'll be displayed will match all of the criteria, that you'll fill in. Kindly note that you **don't** need to fill in all of the options. The options are as follows:


| Option Name   | Description   |
|---------------|---------------|
|  Object Type |  The type of the record you want to search for i.e, a collection, design, activity, etc... |
|  Creator | The username of the record's creator  |
|  Created After and Created Before  | the timeframe between which the record was created. Make sure to enter the dates in the **YYYY-MM-DD** format  |
| Modified After Modified Before  | The timeframe between the record may had been modified. Make sure to enter the dates in the **YYYY-MM-DD** format|
| ID/Name/Description | Enter the ID or the name or the description of the record, which you want to search for|
| Type | Select the *type* of the record, from the following available options in the dropdown menu, for an example: No filter, biopax:Complex, biopax:DnaRegion, biopax:Protein, so:circular, etc...|
| Role | select the **role** of the record from this dropdown menu. It contains various sub-categories of **[igem](https://igem.org/Main_Page)** or **[SO](http://www.sequenceontology.org/miso/current_release/term/SO:0000316)**.|
| Collections| You may select any number of collections, based on your convenience. To select a collection, click on the value attribute of collection and select it from the drop down menu|
| Customisable Filters | You may apply customised filters for the design you want to search for. For that purpose, a few blank filtering columns have been provided. As soon as you'll click on an empty filter on the left hand side, a drop down menu shall appear having various parameters for filtering. These parameters are basically, the properties for filtering the records. Select the property that you want your record to be filtered by, and then click on filter. This shall reload the page and then select the value of the filter, from the drop down on the right hand side. You may provide as many as 5 customised filters which'er optional|
-----------------------------------------------------------------------------


After selecting the desired options for performing a search using advanced parameters, click **search**. This will return the records after comprehending all the details that you've entered.

* Just below, there is an option to create a **new collection** as well. If you wish to create a collection from your search results, you need to fill in the following items:

|Option Name |   Description |
|------------|---------------|
| Collection Name| This is the name string that’ll be assigned to the submission.|
| Collection Description| This is the description string that briefly explains your submission.|
| Collection ID | This is a user-defined alphanumeric string identifier for the submission and it should contain alphanumeric and underscores characters only.|
| Collection Version| This is the alphanumeric string which is associated with the submission.|
--------------------------------------------------------------------------------------------

After you've filled in all the available options, click on **create collection**. This will return the search results to you, in the form a private collection.







### 1.4 SPARQL Search

On the search results page, there is button labeled as **[SPARQL](https://www.w3.org/TR/sparql11-query/)**. Clicking on that button will direct you to the SPARQL page. Since, SPARQL is a query language, hence it'll query Synbiohub's databases for the designs that you're looking for. On the SPARQL page, you can select the graph that is from **private** or **public**. Here, **public** means searching amongst the public submissions, that can be viewed by and **private** means, the ones that are your personal collections.

In the box provided just below graphs dropdown, enter the SPARQL query. Following is an example that selects all sbol components that have an SO role type. It returns the part title, part role, part display id, part uri, and the total number of parts returned by the query. If you want to search for other types of designs, just replace SBOL with your preferred type:

```

# Some common prefix's are also provided below, which you can use in your SPARQL queries.
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX sbh: <http://wiki.synbiohub.org/wiki/Terms/synbiohub#>
PREFIX prov: <http://www.w3.org/ns/prov#>
PREFIX sbol: <http://sbols.org/v2#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX purl: <http://purl.obolibrary.org/obo/>
SELECT  # makes up the headers of the table
?def # directs you to the design for which you're looking for 
?displayId # This statement displays the Id the design
?title # displays the title of the design
(count(?def) as ?count) # displays the count parameter for the design
?role # displays the role of the design    
WHERE { 
?s sbol:component ?comp # Searching for **sbol** components
?comp sbol:definition ?def # provides the link to that component
filter (regex(?role, 'http://identifiers.org/so/SO:')) 
OPTIONAL {?def sbol:role ?role} # Defines the role
OPTIONAL {?def sbol:displayId ?displayId} # gives the ID of that particular record
OPTIONAL {?def dcterms:title ?title} 
  }

```

After writing your SPARQL query, just click **submit query**. After you click on **submit query**, a list of records matching with SPARQL query shall be displayed.





### 1.5 Searching on a Record Page

On a record page, under the search button, you may find the following options:-

#### 1.5.1 Searching for Uses

This returns other records that refers to this particular record which you're currently viewing. For example, if this is an engineered region, then it will return all other components that use this as a sub-component.

#### 1.5.2 Search for Twin Components

If the record being viewed is a component, then you'll also have the option to search for **twin** components. A twin is another component that has the same sequence as the object being viewed. So, selecting this option will return all the records having the same sequence as the object that you'd be currently viewing.


#### 1.5.3 Search for Similar Components

If the record being viewed is a component and SBOLExplorer is being run on that particular SynBioHub instance, then you'll also have the option to search for **similar** components. A component is similar, when the sequences are close enough, that SBOlExplorer has clustered those 2 components together into the same cluster.

## 2. Viewing & Downloading the Information



### 2.1 Viewing the Information

There are various types of records on SynBioHub. They've been divided into the following sub-categories:

#### 2.1.1. Viewing a Record

This page consists of a general description of 

#### 2.1.2 Viewing a collection
Once you've navigated successfully to the collections home page, the following steps need to be followed:

1. On the collection's home page, you'll be able to view to view the following parameters in this order:

* Name: Represents the name of the collection, which you want to view.

* ID and version: The next line represents the ID and the version of the collection. Every collection has a specific ID associated with it and a version which represents the number of times; it has been modified.

* Resource type: This represents the type of record. For this section, it should be a **collection**.

* Created by: Displays the name of the collection's creator.

* Date created: Displays the date and time when the record was created.

* Subsequently, we have a brief description of the collection that is provided by the creator of the collection. 

* Then, we've got two clickable options, that are **[download](https://synbiohub.github.io/userdocumentation/#32-downloading-the-information)** and **back**. Back navigates you to the search page. 


* Then, you can view the members of that specific collection. There is also an option to filter the members. Click on the option to filter, and a drop down menu shall appear. You may choose the filters based on your convenience. There is also an option to search for a specific member of the collection by entering the name or ID of the member into the search box and clicking search. You may also choose the number of entries that you want to display on that page.
The list of members is sortable and can be sorted on the basis of name, identifier, type as well as description.
The list consists of the name, identifier, type as well as description of respective the members. 

* You can also view details about that specific collection, in the next section. This section contains references as well as citations. 

* Subsequently, you can also view various other properties concerning a particular collection. This specifically conatains information about the various owners of that collection.

* Finally, you can also view the various attachments that are there in that particular collection.

#### 2.1.3 Viewing a component

Once you've successfully navigated to the record's home page, you'll be able to view the parameters in this order:

* Name: Represents the name of that particular record.

* ID and version: The next line represents the ID and the version of that record. Every record has a specific ID associated with it and a version which represents the number of times; it has been modified.

* Generated from: Represents the source from where that record had been generated from.

* Then, we've got five clickable options, that are:

   * **[Download](https://synbiohub.github.io/userdocumentation/#32-downloading-the-information)**
 
   * **[Search](https://synbiohub.github.io/userdocumentation/#1-searching-for-information)**

   * **[Share](https://synbiohub.github.io/userdocumentation/#6-data-sharing-mechanisms)**

   * **Back**: This option navigates back to the main page of the collection, which that particular record is a part of.


   * **[Add to a collection](https://synbiohub.github.io/userdocumentation/#43-updating)** 

 
* Next we have is the VisBOL Navigator, with zooming capabilities. This, graphically represents the structure of the engineered region. By hovering your pointer over this structure, you can view the following attributes of that particular engineered region: type of resource, identifier, name and role of the engineered region. 

*  Then we have the details of that engineered region. This consists of the following:

	* **[Type](https://dissys.github.io/sbol-owl/sbol-owl.html#type)**: This specifies the category of biochemical or physical entity. For example DNA, protein, or small molecule that a ComponentDefinition object abstracts for the purpose of engineering design. 

	* **[Role](https://dissys.github.io/sbol-owl/sbol-owl.html#role)**: Clarifies the potential function of an entity in a biochemical or physical context. When it is used for ComponentDefinitions, it MUST identify terms from ontologies that are consistent with the types property of the ComponentDefinition.

	* **[Sequence](https://dissys.github.io/sbol-owl/sbol-owl.html#Sequence)**: The purpose of the Sequence class is to represent the primary structure of a ComponentDefinition object and the manner in which it is encoded. This representation is accomplished by means of the elements property and encoding property. 

	* Also, you can view reference as well as citations.

* Then, we have the section named, **other properties**. This consists of the following attributes:

	* **[Ontology for Biomedical Investigations(OBI)](www.ontobee.org/ontology/OBI?iri=http://purl.obolibrary.org/obo/OBI_0002110)**: A centrally registered identifier symbol used to uniquely identify objects given by International DOI Foundation. The DOI system is particularly used for electronic documents such as journal articles. 


	* SynBioHub#Owned_by: Username of the design owner.

	* SynBioHub#TopLevel

* Subsequently, we have the section titled as, **Member of these collections**. This section contains the list of collection's to which that particular resource belongs to.

* Then, we have the **attachments** page. In this section, you can view the various attachments, of a resource.

* Then, we have the clickable option of **[interactions](https://dissys.github.io/sbol-owl/sbol-owl.html#Interaction)**. Interactions Provide more detailed description of how the FunctionalComponent objects of a ModuleDefinition are intended to work together. This section is further divided into 3 sections, which are as follows:
  * **[Interaction](https://dissys.github.io/sbol-owl/sbol-owl.html#Interaction)/[Participation](https://dissys.github.io/sbol-owl/sbol-owl.html#Participation)**: *Interaction* basically provides more detailed description of how the FunctionalComponent objects of a ModuleDefinition are intended to work together whereas each *participation* represents how a particular FunctionalComponent behaves in its parent Interaction.
  
  * **[Participant Definition](https://dissys.github.io/sbol-owl/sbol-owl.html#definition)**:The definition property is a REQUIRED URI that refers to the ComponentDefinition of the ComponentInstance. As described in the previous section, this ComponentDefinition effectively provides information about the types and roles of the ComponentInstance.

  * **[Type](https://dissys.github.io/sbol-owl/sbol-owl.html#type)/[Role](https://dissys.github.io/sbol-owl/sbol-owl.html#role)**: Type specifies the category of biochemical or physical entity. For example DNA, protein, or small molecule that a ComponentDefinition object abstracts for the purpose of engineering design. For DNA or RNA entities, additional types fields are used to describe nucleic acid topology (circular / linear) and strandedness (double- or single-stranded). 
       Role basically clarifies the potential function of an entity in a biochemical or physical context. When it is used for ComponentDefinitions, it MUST identify terms from ontologies that are consistent with the types property of the ComponentDefinition. For example, the roles property of a DNA or RNA ComponentDefinition could contain URIs identifying terms from the Sequence Ontology (SO).

* There may be additional clickable sections after the attachments menu. These have been added via, **[visualisation plugins](https://github.com/SynBioHub/Plugin-Visual-Seqviz)** and they're as follows:

	* **iGEM main page**, 

	* **iGEM design page** and

	* **iGEM experience page**. 

	* Then, we have a section, titled **Member of these collection**, which displays the collection, of which that particular record is a part of.   

	* Then is the section that contains, **Sequence Visualisation** of that particular resource. Finally, we have the **component sankey** and the **component bar**. The iGEM parts are plugins, hence they are not part of every instance and the Sequence Visualization, Sankey, and Component bar are additional plugins, hence they've been explained in detail [here](https://github.com/SynBioHub/Plugin-Visual-Seqviz).


### 2.2 Downloading the Information
Once you would've navigated successfully to the records's home page, there would be a download option on the left, in a dropdown format.
 
Following are the types of formats that you may be able to download a record:

**Note: Not all the record types may be downloaded in all formats.**

 |  Type             | Description  |
    |-------------------|--------------|
    |  **[SBOL](https://sbolstandard.org/datamodel-about/)**             | The Synthetic Biology Open Language (SBOL) has been developed as a standard to support the         specification and exchange of biological design information in synthetic biology.          |
    |  **[Combine Archive](http://co.mbine.org/documents/archive)**  | A COMBINE archive is a single file containing the various documents (and in the future, references to documents), necessary for the description of a model and all associated data and procedures. This includes for instance, but not limited to, simulation experiment descriptions, all models needed to run the simulations and associated data files. The archive is encoded using the Open Modeling EXchange format (OMEX).            |
| **[GFF3](http://asia.ensembl.org/info/website/upload/gff3.html)**       | The GFF (General Feature Format) format consists of one line per feature, each containing 9 columns of data, plus optional track definition lines. |
 | **[FASTA](https://en.wikipedia.org/wiki/FASTA_format)**       | In bioinformatics and biochemistry, the FASTA format is a text-based format for representing either nucleotide sequences or amino acid (protein) sequences, in which nucleotides or amino acids are represented using single-letter codes. The format also allows for sequence names and comments to precede the sequences. The format originates from the FASTA software package, but has now become a near universal standard in the field of bioinformatics.|
  | Image     | An image is an artifact that depicts visual perception, such as a photograph or other two-dimensional picture, that resembles a subject—usually a physical object—and thus provides a depiction of it. In the context of signal processing, an image is a distributed amplitude of color(s). A pictorial script is a writing system that employs images as symbols for various semantic entities, rather than the abstract signs used by alphabets|
----------------------------------------------------------------------------------------

Additional download options can be through the use of **[download plugins](https://synbiohub.github.io/plugins/#34-download)**.





## 3. Registering & Updating an Account

### 3.1 Registering an Account

Following Steps need to be followed for registering onto SynBioHub:

1. Navigate to SynBioHub's home page.

2. Click on the **Login or Register** option on the top right hand side of your Screen.

3. Enter the following details to complete your registration process: 

| Option Name | Description   |
|-------------|----------|
| Full Name   | Enter the name of the user|
| Affiliation(Optional)| You can enter the name of the university/institute that you're currently affiliated to| 
| Email Address| Enter the Email Address, through which you want to get registered. If in future you forget your login credentials, then this shall be used for sending a recovery password for your account| 
| Username | You have to enter a username of your own choice. This shall be displayed on the record page of every record that you submit|
|Password | Enter a password (preferably a strong one) for keeping your user account safe|
---------------------------------------------------------------------------------------------------
4. When you need to login into your SynBioHub account, click on the "login or Register" option. Then you need to enter your email address and your password to access your account.

### 3.2 Updating an Account

If you ever need to update your account, the following steps need to be followed:

1. You need to be logged in order to update your account. Follow the previous set of steps to login, if you aren't logged in to your account.

2. Then, click on the **profile** option. It'll redirect you onto a page, which contains your profile.

3. On this page, update whichever section you want to, and then click on the **save** option at the bottom to successfully update your profile.



## 4. Submitting, Managing & Updating Submissions

### 4.1 Submitting 

For submitting your designs to SynBioHub, following steps need to be followed:

1. Navigate to SynBioHub's home page.

2. Click on the **Submit** option and it'll direct you to the Submit page. 

Now, there are 2 ways you make your submissions i.e, creating a new collection and then submitting your resource or submitting to an existing collection.

#### 4.1.1 Creating a new collection

1. Select the **create a new collection** option.

2. Following are the attributes that need to be filled up :

* **Name**: This is the name string that'll be assigned to the submission.

* **Collection Description**: This is the description string that briefly explains your submission.

* **Collection ID**: This is a user-defined string identifier for the submission and it should contain alphanumeric and underscores characters only.

* **Collection Version**: This is the version string which is associated with the submission.

* **Citations** (optional): This is a list of comma separated pubmed IDs of citations to store with the submission, just for reference. It is an optional attribute.

* **SBOL/GENBANK/GFF3/FASTA/ZIP file** (OPTIONAL): You can optionally submit a file. The file should be of the following types:


 |  Type             | Description  |
    |-------------------|--------------|
        |  **[SBOL](https://sbolstandard.org/datamodel-about/)**             | The Synthetic Biology Open Language (SBOL) has been developed as a standard to support the         specification and exchange of biological design information in synthetic biology.           |
    | **[GFF3](http://asia.ensembl.org/info/website/upload/gff3.html)**       | The GFF (General Feature Format) format consists of one line per feature, each containing 9 columns of data, plus optional track definition lines.|
    | **[FASTA](https://en.wikipedia.org/wiki/FASTA_format)**      | In bioinformatics and biochemistry, the FASTA format is a text-based format for representing either nucleotide sequences or amino acid (protein) sequences, in which nucleotides or amino acids are represented using single-letter codes. The format also allows for sequence names and comments to precede the sequences. The format originates from the FASTA software package, but has now become a near universal standard in the field of bioinformatics. |
| **[zip](https://en.wikipedia.org/wiki/Zip_(file_format))** | ZIP is an archive file format that supports lossless data compression. A ZIP file may contain one or more files or directories that may have been compressed. |
----------------------------------------------------------------------------------------------------------------

* **Handler**: You also need to select a handler. Following options are available:
    
    * Default          

    * Excel Library
    
    * Excel Composition

    * Snapgene        

* Finally, you have an option to overwrite the existing objects in that collection i.e, removing all the existing objects in the collection and adding new ones or keeping the old resources and adding the new ones.

3. At last, click on **submit**.

#### 4.1.2 Submitting to an existing collection

1. Select the **add to existing collection** option.

2. Then, select your desired collection, to which you want to add your submission from the dropdown menu.

3. Subsequently, upload the files which you want to submit. The file should be of the following types:


 |  Type             | Description  |
    |-------------------|--------------|
        |  SBOL             | The Synthetic Biology Open Language (SBOL) has been developed as a standard to support the         specification and exchange of biological design information in synthetic biology. To know more about SBOl, visit [this page](https://sbolstandard.org/datamodel-about/)           |
        | Annotated zip | ZIP is an archive file format that supports lossless data compression. A ZIP file may contain one or more files or directories that may have been compressed. To know more about zip, visit [this page](https://en.wikipedia.org/wiki/Zip_(file_format))|
    | GFF3       | The GFF (General Feature Format) format consists of one line per feature, each containing 9 columns of data, plus optional track definition lines. To know more about GFF3, click [here](http://asia.ensembl.org/info/website/upload/gff3.html).|
    | FASTA       | In bioinformatics and biochemistry, the FASTA format is a text-based format for representing either nucleotide sequences or amino acid (protein) sequences, in which nucleotides or amino acids are represented using single-letter codes. The format also allows for sequence names and comments to precede the sequences. The format originates from the FASTA software package, but has now become a near universal standard in the field of bioinformatics. To know more about FATSA file format, click [here](https://en.wikipedia.org/wiki/FASTA_format)|
| Zip | ZIP is an archive file format that supports lossless data compression. A ZIP file may contain one or more files or directories that may have been compressed. To know more about zip, visit [this page](https://en.wikipedia.org/wiki/Zip_(file_format))|
----------------------------------------------------------------------------------------------------------------

4. Finally, you have an option to overwrite the existing objects in that collection i.e, removing all the existing objects in the collection and adding new ones or keeping the old resources and adding the new ones.

5. At last, click on **submit**.


### 4.2 Managing

1. Navigate to SynBioHub's home page.

2. Click on **submissions**. It'll direct you to a page titled **manage submissions**. On this page you'll be able to see collections to be divided, broadly under 2 categories. The 1st one being, **private collections**, which you've created and only you have access to them and 2nd one being, **public collections**, to which all the users have access to.

3. You can view your collection by clicking on the collection name. 

4. In order to make your collection public, click on **make public**. This shall enable that other users to view your collection and its contents.

5. To delete your collection, click on **Remove**. This will remove the collection as well as the resources contained, in that specific collection, namely promoters, activators, modules, components, engineered region, etc.


### 4.3 Updating

1. On the submit page, click on *Submit to an existing collection* option.

2. Then, select to the collection you want to submit your design to.

3. Select the design that you want to submit.

4. You may choose to *overwrite the existing objects* in a collection.

5. Then, click on submit.


## 5. Editing a Submission

To edit your submissions, following steps need to be followed:

1. Go to the submissions page.

2. Select the collection that you want to edit.

3. First of all, you can edit the **name** and **description** of the record.

4. Then, you can add a **source** for your record.

5. Subsequently, you may add a brief description for your record.This may contain details that can be described in brief about that particular record.

6. As you scroll down, you'll find a clickable menu, titled **details**. Under this section, you can find the following options which you can edit. They're as follows:

* **Add Description**: Here, you can provide a detailed description for your record. 

* **Add notes**: In this section, you can provide additional notes for explaining your record. 

	Here you can use the basic text formatting options, such as **bold**, *italic* and underlining. Also, you may include an image as well links with the use of html tags.


* **Source**: Here, you can enter various links from referring, to the place from where your record has been generated from.

* **Citations**: You just need to add pubmedID's separated by commas, using which you can cite several research papers.

7. Then, we have the section titled, **other properties**. Under this section, you can add/edit various properties, other than Synbiohub#owner and Synbiohub#Toplevel. 

8. Finally, we have the attachments sections. Herein, you can upload as well as lookup for an attachment.The process for both the options, is described in detail, as follows:

1. **Upload attachments**: For uploading an attachment, you just need to click, **select file(s)** option and a popup shall appear. Now you need to select the attachments from your machine based on your convenience. 

2. **Lookup attachment**: Under this option, you can search for attachments. For this, you need to provide a URL for the attachment as well as its name. Then you need to select the type of attachment, for which you want to search for. The types are as follows: .nib, 2bit, A2M, ABI, etc...



## 6. Data Sharing Mechanisms

There are a couple of ways to share data in SynBioHub. They're mentioned as follows:

### 6.1 Using the Share option

1. Select the collection/design that you want to share.

2. Click the **share** option. Once you click on the share option, a link shall appear.

3. Now, copy that link & you can share the link, thereby sharing the resource.

### 6.2 Adding an owner

You can also share your design by giving any number of persons access by adding them as an owner for your design. This will give them full administrative access to your resources.
The steps to do so are as follows:

1. Select the collection/design that you want to share.

2. Click on the **add an owner** option.

3. Select the Username of the person, with whom you want to share your resources.

4. Click on **grant ownership**.


## 7. Administration

Note: **The administration section will only be available, if you're using a SynBioHub local instance. If you're using a global instance, such as [this](https://synbiohub.org/) one, then the administration section won't be available unless you have privileged access to SynBioHub.**

To access the admin page, the following steps need to be followed:

1. Navigate to the home page of your SynbioHub local instance.

2. Click on **admin**, in order to access the administrative settings of your instance. This will direct you to the administrative page. It has been divided into several sub-sections, for your convenience. They're discussed in detail, as follows:

#### 7.1 Status

Several parameters essential for the smooth functioning of SynBioHub, are mentioned in this sub-section. They're as follows:

| parameter | Description                                                 |
| ----------|-------------------------------------------------------------|
| 1. **Platform**: Linux x64; 4.19.76-linuxkit | This parameter represents the platform on which SynBioHub was built.|
| 2. **Node Version**: vXX.X.X | This represents the node.js version, on which your local instance is running|
| 3. **Instance Name**:  name_of_your_choice | This represents the name of your SynBioHub instance. This can be changed based on your convenience.|
|4. **Listen Port: 7777** | When Oracle HTTP Server is started, by default, it listens for requests on port 7777 (non-SSL). If port 7777 is occupied, Oracle HTTP Server listens on the next available port number between a range of 7777-7877. Thus, if port 7777 is busy, it would listen on port 7778, and so on. To get more information on this, click [here](https://docs.oracle.com/cd/B12037_01/server.101/b12255/netconf.htm#:~:text=When%20Oracle%20HTTP%20Server%20is,port%207778%2C%20and%20so%20on.).|
| 5. **SPARQL Endpoint**: http://virtuoso:8890/sparql | A SPARQL Endpoint is a Point of Presence on an HTTP network that's capable of receiving and processing SPARQL Protocol requests. It is identified by a URL commonly referred to as a SPARQL Endpoint URL. To know more about SPARQl endpoints, click [here](https://www.w3.org/wiki/SparqlEndpointDescription). |
| 6. **Graph Store Endpoint**: http://virtuoso:8890/sparql-graph-crud-auth/ |           |
| 7. **Default Graph**: http://localhost:7777/public |             |
| 8. **Graph Prefix**: http://localhost:7777/ |                   |
| 9. **Thread Pool Size**:    |                    |
| 10. **Upload Limit**: X mb| Shows the maximum limit of files that you can upload at once to your instance|

#### 7.2 Graphs

This section basically displays the graph URI and its corresponding triples. You can select the number of graphs you want to view on one page as well as search for any specific graphs, with the help of search box. You can also sort the graphs on the basis of number of triples.

#### 7.3 Log

This section displays the log file for your SynBioHub local instance. You can view 4 types of logs, which are as follows:

1. **Error**

2. **Warn**

3. **Info**

4. **Debug**

You may use the pointer to view differs types of logs.

#### 7.4 Mail

On this page, you have 2 options, that are [sendgrid](https://sendgrid.com/wp-content/uploads/2016/09/SendGrid-Implementation-Review.pdf) API key and sendgrid from email.

In the first column, you need to fill the API key, that you'd need to generate from sendgrid. SendGrid is a cloud-based SMTP provider that allows you to send email without having to maintain email servers. SendGrid manages all of the technical details, from scaling the infrastructure to ISP outreach and reputation monitoring to whitelist services and real time analytics.

##### 7.4.1 Setting up Sendgrid 

In order to enable SynBioHub to send account-related emails, you need a sendgrid account and API key. The following steps need to be executed, for setting up sendgrid:-

1. Visit [this](www.sendgrid.com) website.

2. Select the *Sign up* option, in case you're using it for the first time.

3. Enter you Email Address and password as well as select the captcha for verification. 

4. Fill up all the details about yourself on the "Tell Us About Yourself" page.

5. Then, after filling up all the details correctly it'll re-direct you to your dashboard and send a confirmational Email.

6. Click on the *Settings* options on left hand side of the page.

7. Then, select the *Create an API key option*.

8. It'll prompt you to give your API key a name. Also, you can customize the API key permissions.

9. After completing these steps, click on Create and View. 

10. The API key is shown only for once due to security reasons, so try to save it at a safe place.

11. Your API key has been created, and hence ready to use!!





1. **SendGrid API key**: For generating an API key, you need to have a sendgrid account. To sign-up for sendgrid and hence generating an API key, click [here](https://synbiohub.github.io/setup/#setting-up-sendgrid).
2. **SendGrid From Email**:  Here, you can enter the email, which you can use for sending emails.

#### 7.5 Plugins

On this page, you can configure the **[plugins ](https://synbiohub.github.io/plugins/)** which you want to use. Plugins are modular stand-alone additions to SynBioHub. They function in a way that is similar to browser extensions. They can be installed separately from the browser/SynBioHub and provide additional ‘custom’ functionality to the browser/SynBioHub experience despite having a completely separate code base from the browser/SynBioHub. Though, they seem integrated to the user.

They're broadly classified into 3 types, which are as follows:

1. Submit: Submit plugins are available to use from the submit endpoint. They work by taking in the file that is uploaded in the submit and processing it to return SBOL to the SynBioHub endpoint.

2. Visual: Visual plugins are available on all ‘endpoint’ pages, for example pages for components, sequences, activities, etc. Visual plugins return html to be displayed on the page.

3. Download: Download plugins are available on all ‘endpoint’ pages, for example pages for components, sequences, activities, etc. Download plugins return some kind of file which is downloaded by the user.



As mentioned above, the plugins are divided into 3 categories all having the same attributes. The attributes, which need to be filled up are as follows:

* Name: This is the name which you want to give to your plugin.

* URL: In this column, you need to enter the URL for your plugin.

After filling both of the columns click on **save**, in order to save your plugin.

#### 7.6 Registries

SynBioHub also supports the Web of Registries concept i.e, the idea of multiple separate repositories linked together by shared common semantics. In the case of SynBioHub, SBOL is used to support the common exchange of data, thus positioning SynBioHub to support the development of synthetic biology workflows by acting as a source and a storage facility for designs.

Hence, Web Of registries enables communication between SynBioHub instances. Sharing designs between instances of SynBioHub is also further facilitated via the Web of Registries service. Federated SynBioHub instances can reference parts in the public graph of other federated instances. In order to support this federation, the Web of Registries service maintains information about all SynBioHub registries, such as their name, description, administrator email, URI prefix, and uniform resource locator(URL). 

Any SynBioHub can access the Web Of Registries to determine information about all registered SynBioHub instances. If a design references a part within another synbiohub instance, the information about this part can be fetched in order to render this design information locally and provide links to the corresponding design information page for this part.

When a new SynBioHub instance wishes to join the Web of Registries, it sends its information to the Web of Registries service, and all the Web of Registries curators are alerted via email that there is a new repository pending approval. Once the repository has been approved, its information is broadcast to all other registries in the Web of Registries. Anybody can access the current list of registries through an HTTP GET request. Once registered, an instance of SynBioHub is able to locate designs within any other instance that is registered with the Web of Registries.



SynBioHub demonstrates the application of this harmonized data exchange through existing repositories, hence envisaging a wider, integrated ecosystem of biological part information shared across a plethora of different repositories with different capabilities.


* On this page, you can configure the registry for your local instance. To configure the registry for your local instance, enter the administrator email in the column just besides the web-of-registries link. After entering the admin email, click on **submit** and this would configure the admin email for the registries.

* There are 2 options given just below the local web of registries sub-section, which are:

1. **Retrieve from web of registries**: This option shall retrieve the web of registries that are already existing globally, locally onto you instance, if in case you delete them. 

2. **Add registry**: This shall enable you to add a registry onto your instance. For adding, click on this option. Then, a popup shall appear. Subsequently, enter the registry URI prefix and the Registry URL. Finally, click on **submit**.
 

* Several local web-of-registries are also given on this page alongside their Synbiohub URL. Here, you have an option to **save** as well as **delete** the already existing registries.  

#### 7.7 Remotes

There are 2 types of remotes you can configure for SynBioHub i.e, **Benchling** and **ICE**. They're discussed in detail as follows:

1. **[Benchling](http://benchling.com/academic)**: Benchling is an integrated software solution for experiment design, note-taking, and molecular biology. It is a free, intelligent research platform with tools for note-taking, molecular biology, and sample tracking. Benchling includes an electronic lab notebook, a molecular biology suite for design and analysis, and a bioregistry to track inventory. 

2. **[ICE](https://ice.jbei.org/)**: ICE is a registry platform that provides robust data storage for DNA components, integrated tools for part characterization, as well as mechanisms for secure access and information sharing with other users and software tools. 

Upon opening this page for the first time you'll see a message stating: *No remotes configured*. To configure a remote for your instance, follow the following steps:

##### 7.7.1 Configuring a benchling remote

1. When you'll click on the type box, a dropdown menu shall appear containing 2 options, ice and benchling. For configuring a benchling remote, select **benchling**. Then click on **add remote**. 

2. As soon as you'll click on add remote, a popup shall appear asking you to fill up certain set of attributes. They're as follows:


| Attribute  | Description  |
|------------|--------------|
| 1. ID          | Enter ID of the benchling remote.             |
| 2. Type   |  This shall display the type of remote that you would've chosen, initially. |
| 3. URL  |  Enter the URL for the benchling remote. |
| 4. Sequence Suffix  | This represents the suffix to use for the sequences found on benchling.   |
| 5. Default Folder ID |  Enter the default folder on benchling to access. |
| 6. Public  |  Should be checked, if you want the remote to be visible publicly. If not, then it should not be checked.  |
| 7. Reject Unauthorized | Should be checked, if you want to the SSL certificates to be checked. If not, then it should not be checked.  |
| 8. Folder Prefix |  Represents the prefix to use for folders on benchling. |
| 9. Root Collection Display ID  | Represents the display id for the root collection on the remote.   |
| 10. Root Collection Name  |  This represents the name for the root collection on the remote. |
| 11. Root Collection Description |  A brief description about the root collection on the remote. |
| 12. Benchling API Token | The token generated by benchling should be entered here.  |
---------------------------------------------------------------------------------

Once you are through with all the attributes, click on submit. 

3. Once you've clicked on submit, you'll be able to see a fully configured remote on the left. You can also delete and edit your remote. To delete any of your configured remotes, click on delete. To edit any of the information, click on edit. Once you've edited the information, click on submit.   

##### 7.7.2 Configuring an ICE remote

1. When you'll click on the type box, a dropdown menu shall appear containing 2 options, ice and benchling. For configuring an ICE remote, select **ICE** and then click on **add remote**.

2. As soon as you'll click on add remote, a popup shall appear asking you to fill up certain set of attributes. They're as follows:


| Attribute  | Description  |
|------------|--------------|
| 1. ID          | Enter ID of the benchling remote.             |
| 2. Type   |  This shall display the type of remote that you would've chosen, initially. |
| 3. URL  |  Enter the URL for the benchling remote. |
| 4. Sequence Suffix  | This represents the suffix to use for the sequences found on benchling.   |
| 5. Default Folder ID |  Enter the default folder on benchling to access. |
| 6. Public  |  Should be checked, if you want the remote to be visible publicly. If not, then it should not be checked.  |
| 7. Reject Unauthorized | Should be checked, if you want to the SSL certificates to be checked. If not, then it should not be checked.  |
| 8. Folder Prefix |  Represents the prefix to use for folders on benchling. |
| 9. Root Collection Display ID  | Represents the display id for the root collection on the remote.   |
| 10. Root Collection Name  |  This represents the name for the root collection on the remote. |
| 11. Root Collection Description |  A brief description about the root collection on the remote. |
| 12. ICE API Token | The token generated by ICE should be entered here. |
| 13. ICE API Token Client |       |
| 14. ICE API Token Owner |         |
| 15. ICE Collection   | Name of the ICE collection. |
| 16. Group ID |       |
| 17. PI | 	Principal Investigator name should be entered. |
| 18. PI Email | Principal Investigator email should be entered.|
| 19. Part Number Prefix | Prefix that is to be used for the parts. |
---------------------------------------------------------------------------------


3. Once you've clicked on submit, you'll be able to see a fully configured remote on the left. You can also delete and edit your remote. To delete any of your configured remotes, click on delete. To edit any of the information, click on edit. Once you've edited the information, click on submit.   

#### 7.8 SBOLExplorer

SBOLExplorer is a service that simplifies the process of analysing and searching for parts within genetic design repositories.

Once you click on the **SBOLExplorer** option, you can view the following options:
1. The first option is that of **SBOLExplorer** endpoint. Here, you can enter and save your SBOLExplorer endpoint for your local instance. Also, make sure that any of the endpoints you enter end with **\\**.
2. Then on the right, you shall see the **searching using SBOL explorer***. You need to Check the this option to enable the SBOLExplorer. 
3. Then, you'll be able to see the option of selecting between, **[Usearch](https://academic.oup.com/bioinformatics/article/26/19/2460/230188)** and **[Vsearch](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5075697/)**. They're explained in detail as follows:

* Usearch: UBLAST and USEARCH are new algorithms enabling sensitive local and global search of large sequence databases at exceptionally high speeds. They are often orders of magnitude faster than BLAST in practical applications, though sensitivity to distant protein relationships is lower. UCLUST is a new clustering method that exploits USEARCH to assign sequences to clusters. UCLUST offers several advantages over the widely used program CD-HIT, including higher speed, lower memory use, improved sensitivity, clustering at lower identities and classification of much larger datasets.

* Vsearch: VSEARCH is an open source and free of charge multithreaded 64-bit tool for processing and preparing metagenomics, genomics and population genomics nucleotide sequence data. It is designed as an alternative to the widely used USEARCH tool for which the source code is not publicly available, algorithm details are only rudimentarily described, and only a memory-confined 32-bit version is freely available for academic use.

4. Next, you can view the start and the end of the last index update. 

5. Subsequently, you can choose whether you want to allow the automatic updating of index or not. If you check this option, the you'll also have the option of choosing the frequency of index update.'

6. Then, you have the option of, whether you want to allow the option of a distributed search or not. 

7. Subsequently, you can select the  value of **[page rank tolerance](https://neo4j.com/docs/graph-algorithms/current/algorithms/page-rank/)**. PageRank basically is an algorithm that measures the transitive influence or connectivity of nodes. It can be computed by either iteratively distributing one node’s rank (originally based on degree) over its neighbours or by randomly traversing the graph and counting the frequency of hitting each node during these walks.

8. There is also an option of choosing a value of **[UClust clustering identity](https://en.wikipedia.org/wiki/UCLUST)**. UCLUST is an algorithm designed to cluster nucleotide or amino-acid sequences into clusters based on sequence similarity. The algorithm was published in 2010 and implemented in a program also named UCLUST. The algorithm is described by the author as following two simple clustering criteria, in regard to the requested similarity threshold T. The first criterion states that any given cluster's centroid sequence will have a similarity smaller than T to any other clusters' centroid sequence. The second criterion states that each member sequence in a given cluster will have similarity to the cluster's centroid sequence that is equal or greater than T.

9. Then you can also input a value for the **[elasticsearch endpoints](https://www.elastic.co/guide/en/cloud-enterprise/1.1/ece-administering-endpoints.html)**. For applications without SSL or HTTPS protocol support, you can use a local endpoint with the HTTP protocol, which in turn connects to your Elastic Cloud Enterprise cluster or to Kibana either using the HTTP or the HTTPS protocol.

10. Finally, you have to input a value for the **[SPARQL/Virtuoso endpoints](https://medium.com/virtuoso-blog/what-is-a-virtuoso-sparql-endpoint-and-why-is-it-important-5244df738a3e)**. A Virtuoso SPARQL Endpoint is a feature of every Virtuoso RDBMS instance that offers an HTTP-based Query Service that operates on Entity Relationship Types (Relations) represented as RDF sentence collections using the SPARQL Query Language. These operations may be read- and/or write-oriented and distributed without compromising security, performance, or scalability.

11. Then, click on the **save** button to save all the details for the SBOLExplorer.

####  7.9 SPARQL 

To perform a **[SPARQL](https://www.w3.org/TR/sparql11-query/)** Search, the following steps should be followed:

1. Navigate to SynBioHub's SPARQL Search Page. 

2. Since, SPARQL is a query language, hence it'll query Synbiohub's databases for the designs that you're looking for.

3. Following is an example how a sample SPARQL query is written:

```
  SELECT  # makes up the headers of the table
	
        ?def # directs you to the design for which you're looking for 
	
        ?displayId # This statement displays the Id the design
	
        ?title # displays the title of the design
	
        (count(?def) as ?count) # displays the count parameter for the design
	
        ?role # displays the role of the design    

  WHERE { 
  	 ?s sbol:component ?comp # Searching for **sbol** components

  	 ?comp sbol:definition ?def # provides the link to that component

         filter (regex(?role, 'http://identifiers.org/so/SO:')) 

	 OPTIONAL {?def sbol:role ?role} # Defines the role

	 OPTIONAL {?def sbol:displayId ?displayId} # gives the ID of that particular record

	 OPTIONAL {?def dcterms:title ?title} 
  }
```
*The query selects all sbol components that have an SO role type. It returns the part title, part role, part display id, part uri, and the total number of parts returned by the query. If you want to search for other types of designs, just replace SBOL with your preferred type.* 

---------------------------------------------------------------------

#### 7.10 Theme 

On this several options are available to alter the User interface of your local instance. 

* You can choose to change the logo of your local instance i.e, replace it with the desalt one bu uploading a picture of your choice. To do so, click on choose file. On doing so, a popup shall appear displaying the .png or the .jpeg files on your computer. Choose the file offs per your convenience and then click on submit.

* You can also change the name of your Synbiohub local instance, by typing in the name of your choice in the given **instance name** box. 

* There is also an option to change the text that appears on the front page as soon as you open the front page of your local instance. To edit that text, a box is given, wherein the default text is already written. You can simply edit the text, in that very box with the text of your choice. 

* Subsequently, there is a section titled **instance settings**. Under that, you can change the base colour of your Synbiohub instance, which by default hex. To search for more HTML colour codes, click [here](https://htmlcolorcodes.com/). 
Also, you can also enable module interactions as well as remove the public enabled.

To save all changes click on **save**.

#### 7.11 Users

This page basically lists all the users currently registered onto your local instance. 

* There is an option to add a user for your local instance. To do so, click on **add user**. This'll direct you to page, wherein you'll be required to fill the following details:

1. **Full Name**: Enter the name of the person, whose account you want to add.

2. **Affiliation**: This is an optional attribute. Enter the university/college, to which that member belongs to. 

3. **Email**: Enter the Email of the new member.

4. **Username**: Assign a username to the member. 

5. **Grant Administrative Access**: There is an option to provide the administrator access, to this particular member. This shall enable, him/her to edit each and every setting on your local instance including the admin ones as well. To grant this particular access, check the grant administrative privileges box.

6. **Grant Member Privileges**: There is an option to provide the member access. 
To grant this particular access, check the grant member privileges box.

7. **Grant Curator Privileges**: There is an option to provide the member access. 
To grant this particular access, check the grant curator privileges box.

* You can also search for a particular user by entering the username in the search box. 

* You can choose the number of users, that you want to display on a particular page ranging from 10 to 100.

* Then, a sortable list of users is displayed. Following is the list of details that is mentioned:

1. **Full Name**: Enter the name of the person, whose account you want to add.

2. **Affiliation**: This is an optional attribute. Enter the university/college, to which that member belongs to. 

3. **Email**: Enter the Email of the new member.

4. **Username**: Assign a username to the member.

5. **Member**: A checked or an empty box is displayed. A checked box means, that the user has member rights and if not, that means the user doesn't have member access. 

6. **Curator**: A checked or an empty box is displayed. A checked box means, that the user has curator rights and if not, that means the user doesn't have curator access.

7. **Admin** : A checked or an empty box is displayed. A checked box means, that the user has admin rights and if not, that means the user doesn't have admin access.

8. **Save**: Clicking on the save option, will permanently save that profile to your local instance.
 

Finally, there is a check box at the end corresponding to allowing public account creation. Enabling this option will allow anyone to create an account on your local instance and hence contribute to your design repository. 
 















 

