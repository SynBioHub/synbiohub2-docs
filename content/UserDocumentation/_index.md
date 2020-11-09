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
 
2. **Search**, 

3. **Share**, 

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

* The next 3 sections are igem main page, Igem design page and the experience page.

* Then is the section that contains, **Sequence Visualisation** of that particular resource.

* Finally, we have the component Sankey and component bar.   


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
----------------------------------------------------------------------------------------



## 4. Submitting, Managing & Updating Submissions

### 4.1 Submitting 

For submitting your designs to SynBioHub, following steps need to be followed:

1. Go to SynBioHub's [home page](https://synbiohub.org/).

2. Click on **Submit** and it'll direct you to the Submit page. 

3. You can either submit your designs to an existing collection or create a new one. On the submit page, select the *Create a new collection* option.

4. Then, give your collection a name and a description.

5. Subsequently, provide a collection ID, version as well as the Citations(if any).

6. Then upload your file in the form of SBOL/GENBANK/GFF3/FASTA/ZIP file and select the handler.

7. Finally, you may choose to Overwrite the existing objects by checking the box given in the end.

8. Click on Submit.



### 4.2 Managing

1. To view the designs that you've uploaded, visit [this](https://synbiohub.org/manage) page.

2. Here, you can view your collections, make them public as well as delete the collection.

3. To make your collection public, click on **Make Public**.

4. To delete your collection, click on **Remove**.

5. Click on the collection's name, to view your design's.

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










 

