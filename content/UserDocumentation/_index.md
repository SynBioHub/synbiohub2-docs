---
title: "User Documentation"
date: 2020-09-04T20:30:59+05:30
draft: true
weight: 20
---

This section contains instructions on how you can implement various operations ranging from registering onto SynBioHub to uploading your genetic designs on SynBioHub, by using the user interface of SynBiohub. The sub-sections are as follows:

## 1. Searching for Information

### 1.1 Searching using keywords

To search amongst various resources, follow these steps:

1. Navigate to SynBioHub's home page.

2. In the search box, enter the keywords for the resource you want to search for and click on the search button.

3. Subsequently, a list of resources matching the keywords that you've entered shall appear on your screen.

4. Select the desired resource from the list.

### 1.2 Sequence Search

To search using a sequence, follow these steps:

1. Navigate to SynBioHub's home page. 

2. Click on the *search* option. It'll direct you to a page containing a list of resources. 

3. Located just below the search box are the various means through which you can search for the desired resources. In this case, click on *sequence search*.

4. Enter the sequence or upload a *FASTA/FASTQ* file, by clicking the choose file option just below the box. This shall search only for exact matches of the sequence. Your entry must be the first key/value pair. To know more about about FASTA files, click [here](https://en.wikipedia.org/wikiFASTA_format#:~:text=In%20bioinformatics%20and%20biochemistry%2C%20the,comments%20to%20precede%20the%20sequences).

5. Then, you can choose the perspective of your search. You can perform a **global** search or an **exact** search. The exact search shall display, those resources which are really close to the sequences that you've entered and the global search search will display those results which have even the smallest of the similarities to the sequence that you've entered. 

6. Subsequently, you may customise the number of results, the value for which must not exceed 10,000. Then you need to enter the minimum and the maximum length of the sequence for which you want to search for. Values for both of these parameters should not exceed 100,000. 

7. Then, you need to enter the maximum number of non-matching target sequences, that are to be considered before the search is halted. This option works in pair with the flag above. The search process sorts the target sequences by decreasing number of k-mers they have in common with the query sequence, using that information as a proxy for sequence similarity. After pairwise alignments, if none of the first x examined target sequences pass the acceptation criteria, the search process stops for that query (no hit). If this flag is set to a higher value, more target sequences are considered. If the flag above and this flag are both set to 0, the complete database is searched.

8. Fill up the *percentage match*, by entering a value between 0 & 1. This depicts the percentage that you want the result to match your query.

9. Finally, select the *pairwise identity definition*. You may select the value for this attribute from the following options:
 
| Value           |   Description                     |
|-----------------|-----------------------------------|
| Default       | Edits distance excluding the terminal gaps|
| CD-HIT definition| Considers the following ratio: (matching columns) / (shortest sequence length)|
|Marine Biological Lab definition               |counts each gap opening (internal or terminal) as a single mismatch, whether or not the gap was extended: 1.0 - [(mismatches + gap openings)/(longest sequence length)]|
| BLAST Definition                |  equivalent to edit distance for global pairwise alignments|



### 1.3 Advanced Search

To perform an Advanced Search, follow these steps:

1. Navigate to SynBioHub's home page. 

2. Click on the *search* option. It'll direct you to a page containing a list of resources. 

3. Located just below the search box are the various means through which you can search for the desired resources. In this case, click on *advanced search*.

4. Now, select the type of the resource you want to search for i.e, a collection, design, activity or a sequence.

5. Then, select the username of the design's creator.

6. Enter the timeframe between which the resource was created, by entering the *created after* and *created before* attributes. Make sure to enter the dates in the **YYYY-MM-DD** format.

7. If the resource has been modified, make sure to enter the *modified after* and *modified before* attributes as well. Make sure to enter the dates in the **YYYY-MM-DD** format.

8. Enter the ID or the name or the description of the resource, which you want to search for.

9. Select the *type* of the resource, from the following available options in the dropdown menu:

* No filter

* biopax:Complex

* biopax:DnaRegion

* biopax:Protein

* so:circular

	Subsequently, select the *role* of the resource from this dropdown menu. It contains various sub-categories of igem or 	SO. 
	To learn more about **igem**, visit [this page](https://igem.org/Main_Page) and for **SO**, visit [this page](http://www.sequenceontology.org/miso/current_release/term/SO:0000316)

10. You may select any number of collections, based on your convenience. To select a collection, click on the value attribute of collection and select it from the drop down menu.

11. You may apply customised filters for the design you want to search for. For that purpose, a few blank filtering columns have been provided. 
As soon as you'll click on an empty filter, a drop down menu shall appear having various parameters for filtering. Select your preference, and then click on filter. This shall reload the page and then select the value of the filter, from the drop down on the right hand side. You may provide as many as 5 customised filters which'er optional.


### 1.4 SPARQL Search

To perform a SPARQL Search, the following steps should be followed:

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
*The query selects all sbol components that have an SO role type. It returns the part title, part role, part display id, part uri, and the total number of parts returned by the query. If you want to search for other types of designs, just replace SBOL with your prefered type.* 

To learn more about SPARQL, visit [this page](https://www.w3.org/TR/sparql11-query/).



## 2. Registering & Updating an account

### 2.1 Registering an account

Following Steps need to be followed for registering onto SynBioHub:

1. Navigate to SynBioHub's home page.

2. Click on the **Login or Register** option on the top right hand side of your Screen.

3. Enter the following details to complete your registration process: 

* Full Name, 

* Affiliation(Optional), 

* Email Address, 

* Username & 

* Password

4. When you need to login into your SynBioHub account, click on the "login or Register" option. Then you need to enter your email address and your password to access your account.

### 2.2 Updating an Account

If you ever need to update your account, the following steps need to be followed:

1. You need to be logged in order to update your account. Follow the previous set of steps to login, if you aren't logged in to your account.

2. Then, click on the **profile** option. It'll redirect you onto a page, which contains your profile.

3. On this page, update whichever section you want to, and then click on the **save** option at the bottom to successfully update your profile.


## 3. Viewing & Downloading the Information

### 3.1 Viewing the Information

There are various types of resources on SynBioHub. They've been divided into the following sub-categories:

#### 3.1.1 Viewing a collection

1. Navigate to SynBioHub's home page.

2. Then, you can search for a specific collection or select **browse the collections** option. It'll direct you to a set of collections based on what you've searched for.

3. Select the collection which you want to view.

4. On the collection's home page, you'll be able to view to view the following parameters in this order:

* Name: Represents the name of the collection, which you want to view.

* ID and version: The next line represents the ID and the version of the collection. Every collection has a specific ID associated with it and a version which represents the number of times; it has been modified.

* Resource type: This represents the type of resource. For this section, it should be a **collection**.

* Created by: Displays the name of the collection's creator.

* Date created: Displays the date and time when the design was created.

* Subsequently, we have a brief description of the collection that is provided by the creator of the collection. 

* Then, we've got two clickable options, that are **download** and **back**. Back navigates you to the search page and the download option consists of the ways in which you can download the collection. They're as follows:

    |  Type             | Description  |
    |-------------------|--------------|
    |  SBOL             | The Synthetic Biology Open Language (SBOL) has been developed as a standard to support the         specification and exchange of biological design information in synthetic biology. To know more about SBOl, visit [this page](https://sbolstandard.org/datamodel-about/)           |
    |  Combine Archive  | A COMBINE archive is a single file containing the various documents (and in the future, references to documents), necessary for the description of a model and all associated data and procedures. This includes for instance, but not limited to, simulation experiment descriptions, all models needed to run the simulations and associated data files. The archive is encoded using the Open Modeling EXchange format (OMEX). To know more about Combine archive, visit [this page](http://co.mbine.org/documents/archive).            |
    |  Annotated Genbank| GenBank format (GenBank Flat File Format) consists of an annotation section and a sequence section. The start of the annotation section is marked by a line beginning with the word "LOCUS". The start of sequence section is marked by a line beginning with the word "ORIGIN" and the end of the section is marked by a line with only "//" To know more about Annotated genbank format, visit [this page](http://quma.cdb.riken.jp/help/gbHelp.html), |                   
    |  Annotated Plasmid Map        |  Plasmid maps are graphical representation of plasmids, that show the locations of major identifiable landmarks on DNA like restriction enzyme sites, gene of interest, plasmid name and length etc. To know more about plasmid map, visit [this page](https://en.wikipedia.org/wiki/Plasmid)              |
    | Plasmid map | Plasmid maps are graphical representation of plasmids, that show the locations of major identifiable landmarks on DNA like restriction enzyme sites, gene of interest, plasmid name and length etc. To know more about plasmid map, visit [this page](https://www.snapgene.com/resources/plasmid-files/). |
    | Annotated zip | ZIP is an archive file format that supports lossless data compression. A ZIP file may contain one or more files or directories that may have been compressed. To know more about zip, visit [this page](https://en.wikipedia.org/wiki/Zip_(file_format))|
----------------------------------------------------------------------------------------


* Then, you can view the members of that specific collection. There is also an option to filter the members. Click on the option to filter, and a drop down menu shall appear. You may choose the filters based on your convenience. There is also an option to search for a specific member of the collection by entering the name or ID of the member into the search box and clicking search. You may also choose the number of entries that you want to display on that page.
The list of members is sortable and can be sorted on the basis of name, identifier, type as well as description.
The list consists of the name, identifier, type as well as description of respective the members. 

* You can also view details about that specific collection, in the next section. This section contains references as well as citations. 

* Subsequently, you can also view various other properties concerning a particular collection. This specifically conatains information about the various owners of that collection.

* Finally, you can also view the various attachments that are there in that particular collection.

#### 3.1.2 Viewing an Engineered Region/Promoter/Activator

1. Navigate to SynBioHub's home page.

2. Then, you can search for a specific collection or select **browse the collections** option. It'll direct you to a set of collections based on what you've searched for.

3. Select the collection which you want to view. Then it'll direct you to the collection's home page. You can select the resource, which you want to view. 

4. On the resource's page, you'll be able to view to view the following parameters in this order:

* Name: Represents the name of that particular resource.

* ID and version: The next line represents the ID and the version of that resource. Every engineered region has a specific ID associated with it and a version which represents the number of time; it has been modified.

* Generated from: Represents the source from where that resource had been generated from.

* Then, we've got five clickable options, that are:
1. **Download**
 
2. **Search**

3. **Share**

4. **Back** 

5. **Add to a collection** 

 The download option consists of the ways in which you can download the resource. They're as follows:

 |  Type             | Description  |
    |-------------------|--------------|
    |  SBOL             | The Synthetic Biology Open Language (SBOL) has been developed as a standard to support the         specification and exchange of biological design information in synthetic biology. To know more about SBOl, visit [this page](https://sbolstandard.org/datamodel-about/)           |
    |  Combine Archive  | A COMBINE archive is a single file containing the various documents (and in the future, references to documents), necessary for the description of a model and all associated data and procedures. This includes for instance, but not limited to, simulation experiment descriptions, all models needed to run the simulations and associated data files. The archive is encoded using the Open Modeling EXchange format (OMEX). To know more about Combine archive, visit [this page](http://co.mbine.org/documents/archive).            |
    |  Annotated Genbank| GenBank format (GenBank Flat File Format) consists of an annotation section and a sequence section. The start of the annotation section is marked by a line beginning with the word "LOCUS". The start of sequence section is marked by a line beginning with the word "ORIGIN" and the end of the section is marked by a line with only "//" To know more about Annotated genbank format, visit [this page](http://quma.cdb.riken.jp/help/gbHelp.html), |                   
    |  Annotated Plasmid Map        |  Plasmid maps are graphical representation of plasmids, that show the locations of major identifiable landmarks on DNA like restriction enzyme sites, gene of interest, plasmid name and length etc. To know more about plasmid map, visit [this page](https://en.wikipedia.org/wiki/Plasmid)              |
    | Plasmid map | Plasmid maps are graphical representation of plasmids, that show the locations of major identifiable landmarks on DNA like restriction enzyme sites, gene of interest, plasmid name and length etc. To know more about plasmid map, visit [this page](https://www.snapgene.com/resources/plasmid-files/). |
    | Annotated zip | ZIP is an archive file format that supports lossless data compression. A ZIP file may contain one or more files or directories that may have been compressed. To know more about zip, visit [this page](https://en.wikipedia.org/wiki/Zip_(file_format))|
    | GFF3       | The GFF (General Feature Format) format consists of one line per feature, each containing 9 columns of data, plus optional track definition lines. To know more about GFF3, click [here](http://asia.ensembl.org/info/website/upload/gff3.html).|
    | FASTA       | In bioinformatics and biochemistry, the FASTA format is a text-based format for representing either nucleotide sequences or amino acid (protein) sequences, in which nucleotides or amino acids are represented using single-letter codes. The format also allows for sequence names and comments to precede the sequences. The format originates from the FASTA software package, but has now become a near universal standard in the field of bioinformatics. To know more about FATSA file format, click [here](https://en.wikipedia.org/wiki/FASTA_format)|
    | Image     | An image is an artifact that depicts visual perception, such as a photograph or other two-dimensional picture, that resembles a subject—usually a physical object—and thus provides a depiction of it. In the context of signal processing, an image is a distributed amplitude of color(s). A pictorial script is a writing system that employs images as symbols for various semantic entities, rather than the abstract signs used by alphabets|
----------------------------------------------------------------------------------------
 
Then is the **search** option. There are three ways you can use the search option. They're as follows:

1. Find Uses: This returns any other object that refers to this object that the user has given as an input, for example, if this is an engineered region, then it will return all other components that use this as a sub-component.

2. Find Twins:  This returns other components, if and only if they have the same sequence as the input by the user.

3. Find Similar: This returns other components that have similar sequences.

The third option is that of **sharing** your resource. There are 2 ways by which you can share your resource. They're as follows:

1.  Send to Benchling: For using Benchling to share your resource, you need to configure a Benchling remote. The Benchling Life Sciences R&D Cloud is an informatics platform to accelerate, measure, and forecast R&D from discovery through bioprocessing. To know more about Benchling and how you can configure a benching remote, click [here](https://www.benchling.com/).

2. Send to ICE: ICE is a registry platform that provides robust data storage for DNA components, integrated tools for part characterization, as well as mechanisms for secure access and information sharing with other users and software tools. 
ICE is built upon the idea of a Web of Registries, and thus provides strong support for distributed, interconnected use. It includes several useful graphical applications for sequence annotation, manipulation and analysis. To know more about ICE, click [here](https://public-registry.jbei.org/login).

Fourth is the **back** option. This option navigates back to the main page of the collection, which that particular resource is a part of.

Finally, we have the **Add to collection** option. This option adds your resource to a specific collection. Clicking on this option, would take you to a page that shall display the collections, that you would've created. Select the collection, to which you want to add this engineered region to and then click on add to collection. This shall add your resource to the selected collection.

* Next we have is the VisBOL Navigator, with zooming capabilities. This, graphically represents the structure of the engineered region. By hovering your pointer over this structure, you can view the following attributes of that particular engineered region: type of resource, identifier, name and role of the engineered region. 

* Then we have the details of that engineered region. This consists of the following:

1. Type: This specifies the category of biochemical or physical entity. For example DNA, protein, or small molecule that a ComponentDefinition object abstracts for the purpose of engineering design. To know more about Type, click [here](https://dissys.github.io/sbol-owl/sbol-owl.html#type).

2. Role: Clarifies the potential function of an entity in a biochemical or physical context. When it is used for ComponentDefinitions, it MUST identify terms from ontologies that are consistent with the types property of the ComponentDefinition.To know more about role, click [here](https://dissys.github.io/sbol-owl/sbol-owl.html#role).

3. Sequence: The purpose of the Sequence class is to represent the primary structure of a ComponentDefinition object and the manner in which it is encoded. This representation is accomplished by means of the elements property and encoding property. To know more about Sequences, click [here](https://dissys.github.io/sbol-owl/sbol-owl.html#Sequence).

4. Also, you can view reference as well as citations.

* Then, we have the section named, **other properties**. This consists of the following attributes:

1. Ontology for Biomedical Investigations(OBI): A centrally registered identifier symbol used to uniquely identify objects given by International DOI Foundation. The DOI system is particularly used for electronic documents such as journal articles. To know more about OBI, click [here](http://www.ontobee.org/ontology/OBI?iri=http://purl.obolibrary.org/obo/OBI_0002110).

2. data_1179

3. SynBioHub#Owned_by: Username of the design owner.

4. SynBioHub#TopLevel

* Subsequently, we have the section titled as, **Member of these collections**. This section contains the list of collection's to which that particular resource belongs to.

* Then, we have the **attachments** page. In this section, you can view the various attachments, of a resource.

* The next 3 sections are **iGEM main page**, **iGEM design page** and the **iGEM experience page**. Then is the section that contains, **Sequence Visualisation** of that particular resource. Finally, we have the **component sankey** and the **component bar**. The iGEM parts are plugins, hence they are not part of every instance and the Sequence Visualization, Sankey, and Component bar are additional plugins, hence they've been explained in detail in the [plugins section](https://synbiohub.github.io/plugins/).


### 3.2 Downloading the Information

#### 3.2.1 Downloading a collection

1. Navigate to SynBioHub's home page.

2. Then, you can search for a specific collection or select **browse the collections** option. It'll direct you to a set of collections based on what you've searched for.

3. Select the collection which you want to download. Then it'll direct you to the collection's home page. 

4. On the left there would be an option to download the collection, in drop down format. Following are the types in which you can download the collection:

|  Type             | Description  |
    |-------------------|--------------|
    |  SBOL             | The Synthetic Biology Open Language (SBOL) has been developed as a standard to support the         specification and exchange of biological design information in synthetic biology. To know more about SBOl, visit [this page](https://sbolstandard.org/datamodel-about/)           |
    |  Combine Archive  | A COMBINE archive is a single file containing the various documents (and in the future, references to documents), necessary for the description of a model and all associated data and procedures. This includes for instance, but not limited to, simulation experiment descriptions, all models needed to run the simulations and associated data files. The archive is encoded using the Open Modeling EXchange format (OMEX). To know more about Combine archive, visit [this page](http://co.mbine.org/documents/archive).            |
    |  Annotated Genbank| GenBank format (GenBank Flat File Format) consists of an annotation section and a sequence section. The start of the annotation section is marked by a line beginning with the word "LOCUS". The start of sequence section is marked by a line beginning with the word "ORIGIN" and the end of the section is marked by a line with only "//" To know more about Annotated genbank format, visit [this page](http://quma.cdb.riken.jp/help/gbHelp.html), |                   
    |  Annotated Plasmid Map        |  Plasmid maps are graphical representation of plasmids, that show the locations of major identifiable landmarks on DNA like restriction enzyme sites, gene of interest, plasmid name and length etc. To know more about plasmid map, visit [this page](https://en.wikipedia.org/wiki/Plasmid)              |
    | Plasmid map | Plasmid maps are graphical representation of plasmids, that show the locations of major identifiable landmarks on DNA like restriction enzyme sites, gene of interest, plasmid name and length etc. To know more about plasmid map, visit [this page](https://www.snapgene.com/resources/plasmid-files/). |
    | Annotated zip | ZIP is an archive file format that supports lossless data compression. A ZIP file may contain one or more files or directories that may have been compressed. To know more about zip, visit [this page](https://en.wikipedia.org/wiki/Zip_(file_format))|
----------------------------------------------------------------------------------------

#### 3.2.2 Downloading a Module/ Engineered Region/ Promoter/ Activator

1. Navigate to SynBioHub's home page.

2. Then, you can search for a specific collection or select **browse the collections** option. It'll direct you to a set of collections based on what you've searched for.

3. Select the collection which you want to download. Then it'll direct you to the collection's home page. From the collection's home page select resource which you want to download and click on that. This will direct you to the resource's home page.

4. Then, on the left there would be an option to download that resource, in drop down format. Following are the types in which you can download the collection:

 |  Type             | Description  |
    |-------------------|--------------|
    |  SBOL             | The Synthetic Biology Open Language (SBOL) has been developed as a standard to support the         specification and exchange of biological design information in synthetic biology. To know more about SBOl, visit [this page](https://sbolstandard.org/datamodel-about/)           |
    |  Combine Archive  | A COMBINE archive is a single file containing the various documents (and in the future, references to documents), necessary for the description of a model and all associated data and procedures. This includes for instance, but not limited to, simulation experiment descriptions, all models needed to run the simulations and associated data files. The archive is encoded using the Open Modeling EXchange format (OMEX). To know more about Combine archive, visit [this page](http://co.mbine.org/documents/archive).            |
    |  Annotated Genbank| GenBank format (GenBank Flat File Format) consists of an annotation section and a sequence section. The start of the annotation section is marked by a line beginning with the word "LOCUS". The start of sequence section is marked by a line beginning with the word "ORIGIN" and the end of the section is marked by a line with only "//" To know more about Annotated genbank format, visit [this page](http://quma.cdb.riken.jp/help/gbHelp.html), |                   
    |  Annotated Plasmid Map        |  Plasmid maps are graphical representation of plasmids, that show the locations of major identifiable landmarks on DNA like restriction enzyme sites, gene of interest, plasmid name and length etc. To know more about plasmid map, visit [this page](https://en.wikipedia.org/wiki/Plasmid)              |
    | Plasmid map | Plasmid maps are graphical representation of plasmids, that show the locations of major identifiable landmarks on DNA like restriction enzyme sites, gene of interest, plasmid name and length etc. To know more about plasmid map, visit [this page](https://www.snapgene.com/resources/plasmid-files/). |
    | Annotated zip | ZIP is an archive file format that supports lossless data compression. A ZIP file may contain one or more files or directories that may have been compressed. To know more about zip, visit [this page](https://en.wikipedia.org/wiki/Zip_(file_format))|
    | GFF3       | The GFF (General Feature Format) format consists of one line per feature, each containing 9 columns of data, plus optional track definition lines. To know more about GFF3, click [here](http://asia.ensembl.org/info/website/upload/gff3.html).|
    | FASTA       | In bioinformatics and biochemistry, the FASTA format is a text-based format for representing either nucleotide sequences or amino acid (protein) sequences, in which nucleotides or amino acids are represented using single-letter codes. The format also allows for sequence names and comments to precede the sequences. The format originates from the FASTA software package, but has now become a near universal standard in the field of bioinformatics. To know more about FATSA file format, click [here](https://en.wikipedia.org/wiki/FASTA_format)|
    | Image     | An image is an artifact that depicts visual perception, such as a photograph or other two-dimensional picture, that resembles a subject—usually a physical object—and thus provides a depiction of it. In the context of signal processing, an image is a distributed amplitude of color(s). A pictorial script is a writing system that employs images as symbols for various semantic entities, rather than the abstract signs used by alphabets|
    | Annotated Zip | ZIP is an archive file format that supports lossless data compression. A ZIP file may contain one or more files or directories that may have been compressed. To know more about zip, visit [this page](https://en.wikipedia.org/wiki/Zip_(file_format))|
----------------------------------------------------------------------------------------



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
        |  SBOL             | The Synthetic Biology Open Language (SBOL) has been developed as a standard to support the         specification and exchange of biological design information in synthetic biology. To know more about SBOl, visit [this page](https://sbolstandard.org/datamodel-about/)           |
        | Annotated zip | ZIP is an archive file format that supports lossless data compression. A ZIP file may contain one or more files or directories that may have been compressed. To know more about zip, visit [this page](https://en.wikipedia.org/wiki/Zip_(file_format))|
    | GFF3       | The GFF (General Feature Format) format consists of one line per feature, each containing 9 columns of data, plus optional track definition lines. To know more about GFF3, click [here](http://asia.ensembl.org/info/website/upload/gff3.html).|
    | FASTA       | In bioinformatics and biochemistry, the FASTA format is a text-based format for representing either nucleotide sequences or amino acid (protein) sequences, in which nucleotides or amino acids are represented using single-letter codes. The format also allows for sequence names and comments to precede the sequences. The format originates from the FASTA software package, but has now become a near universal standard in the field of bioinformatics. To know more about FATSA file format, click [here](https://en.wikipedia.org/wiki/FASTA_format)|
| Zip | ZIP is an archive file format that supports lossless data compression. A ZIP file may contain one or more files or directories that may have been compressed. To know more about zip, visit [this page](https://en.wikipedia.org/wiki/Zip_(file_format))|
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




## 5. Editing you Submissions

To edit your submissions, following steps need to be followed:

1. Go to the [Submissions](http://synbiohub.org/manage) page.

2. Select the collection that you want to edit.

3. You can edit the Name & description of the collection as well as add a source.

4. If you want to add a detailed description, source, reference or notes for the collection, just Scroll down to find those options under the **Details** section.

5. Subsequently, scroll down to find the Members of the collection. You may click on the *delete* sign just next to the description of the design, if you want to delete it or click on the member's name if you want to view its details.

6. Steps 3 & 4 can be followed, if you want to edit any of the member's details.


## 6. Data Sharing Mechanisms

There are a couple of ways to share data in SynBioHub. They're mentioned as follows:

### 6.1 Using the Share option

1. Select the collection/design that you want to share.

2. Click the **Share** option. A link will appear.

3. Now, copy that link & you can share the link, thus sharing the collection/design.

### 6.2 Adding an owner

You can also share your design by giving any number of persons access by adding them as an owner for your design. This will give them full administrative access to your collections/designs.
The steps to do so are as follows:

1. Select the collection/design that you want to share.

2. Click on the **Add an owner** option.

3. Select the Username of the person, with whom you want to share your collection/design.

4. Click on **Grant Ownership**.


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

On this page, you have 2 options, that are sendgrid API key and sendgrid from email.

In the first column, you need to fill the API key, that you'd need to generate from sendgrid. SendGrid is a cloud-based SMTP provider that allows you to send email without having to maintain email servers. SendGrid manages all of the technical details, from scaling the infrastructure to ISP outreach and reputation monitoring to whitelist services and real time analytics. To know more about sendgrid, click [here](https://sendgrid.com/wp-content/uploads/2016/09/SendGrid-Implementation-Review.pdf). 

1. **SendGrid API key**: For generating an API key, you need to have a sendgrid account. To sign-up for sendgrid and hence generating an API key, click [here](https://synbiohub.github.io/setup/#setting-up-sendgrid).
2. **SendGrid From Email**:  Here, you can enter the email, which you can use for sending emails.

#### 7.5 Plugins

On this page, you can configure the plugins which you want to use. Plugins are modular stand-alone additions to SynBioHub. They function in a way that is similar to browser extensions. They can be installed separately from the browser/SynBioHub and provide additional ‘custom’ functionality to the browser/SynBioHub experience despite having a completely separate code base from the browser/SynBioHub. Though, they seem integrated to the user.

They're broadly classified into 3 types, which are as follows:

1. Submit: Submit plugins are available to use from the submit endpoint. They work by taking in the file that is uploaded in the submit and processing it to return SBOL to the SynBioHub endpoint.

2. Visual: Visual plugins are available on all ‘endpoint’ pages, for example pages for components, sequences, activities, etc. Visual plugins return html to be displayed on the page.

3. Download: Download plugins are available on all ‘endpoint’ pages, for example pages for components, sequences, activities, etc. Download plugins return some kind of file which is downloaded by the user.

To know more about plugins in detail, visit the [plugins section](https://synbiohub.github.io/plugins/).

As mentioned above, the plugins are divided into 3 categories all having the same attributes. The attributes, which need to be filled up are as follows:

* Name: This is the name which you want to give to your plugin.

* URL: In this column, you need to enter the URL for your plugin.

After filling both of the columns click on **save**, in order to save your plugin.

#### 7.6 Registries

SynBioHub also supports the Web of Registries concept i.e, the idea of multiple separate repositories linked together by shared common semantics. In the case of SynBioHub, SBOL is used to support the common exchange of data, thus positioning SynBioHub to support the development of synthetic biology workflows by acting as a source and a storage facility for designs.

Hence, Web Of registries enables communication between SynBioHub instances. Sharing designs between instances of SynBioHub is also further facilitated via the Web of Registries service. Federated SynBioHub instances can reference parts in the public graph of other federated instances. In order to support this federation, the Web of Registries service maintains information about all SynBioHub registries, such as their name, description, administrator email, URI prefix, and uniform resource locator(URL).

To know more about web-of-registries, visit [this](https://synbiohub.github.io/setup/#web-of-registries-in-synbiohub) page.

* On this page, you can configure the registry for your local instance. To configure the registry for your local instance, enter the administrator email in the column just besides the web-of-registries link. After entering the admin email, click on **submit** and this would configure the admin email for the registries.

* There are 2 options given just below the local web of registries sub-section, which are:

1. **Retrieve from web of registries**: This option shall retrieve the web of registries that are already existing globally, locally onto you instance, if in case you delete them. 

2. **Add registry**: This shall enable you to add a registry onto your instance. For adding, click on this option. Then, a popup shall appear. Subsequently, enter the registry URI prefix and the Registry URL. Finally, click on **submit**.
 

* Several local web-of-registries are also given on this page alongside their Synbiohub URL. Here, you have an option to **save** as well as **delete** the already existing registries.  

#### 7.7 Remotes

There are 2 types of remotes you can configure for SynBioHub i.e, **Benchling** and **ICE**. They're discussed in detail as follows:

1. **Benchling**: Benchling is an integrated software solution for experiment design, note-taking, and molecular biology. It is a free, intelligent research platform with tools for note-taking, molecular biology, and sample tracking. Benchling includes an electronic lab notebook, a molecular biology suite for design and analysis, and a bioregistry to track inventory. To know more about benching, click [here](http://benchling.com/academic).

2. **ICE**: ICE is a registry platform that provides robust data storage for DNA components, integrated tools for part characterization, as well as mechanisms for secure access and information sharing with other users and software tools. To know more about ICE, click [here](https://ice.jbei.org/).

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

##### 7.1.2 Configuring an ICE remote

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

Here, you can enter and save your SBOLExplorer endpoint for your local instance. You need to Check the "Searching Using SBOLExplorer" to enable the SBOLExplorer. Also, make sure that any of the endpoints you enter are enabled and end with **\\**.


####  7.9 SPARQL 

To perform a SPARQL Search, the following steps should be followed:

1. Navigate to SynBioHub's [SPARQL Search Page](https://synbiohub.org/sparql).

2. Since, SPARQL is a query language, hence it'll query Synbiohub's databases for the designs that you're looking for.

3. Following is an example how a sample SPARQL query is written:

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
*The query selects all sbol components that have an SO role type. It returns the part title, part role, part display id, part uri, and the total number of parts returned by the query. If you want to search for other types of designs, just replace SBOL with your prefered type.* 

To learn more about SPARQL, visit [this page](https://www.w3.org/TR/sparql11-query/).

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
 















 

