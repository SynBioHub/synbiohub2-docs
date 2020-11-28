+++ 
title = "2. Viewing and Downloading the Information" 
description = "" 
weight = 2
+++




## 2.1 Viewing the Information

There are various types of records on SynBioHub. They've been divided into the following sub-categories:

### 2.1.1 Viewing a Record

This section consists of a general description of all record pages i.e, this is what a general record page looks like. Additional sections (if any), are further explained in the further sections, under the respective record types. 
Once you've successfully navigated to the record's home page, you'll be able to view the parameters in this order:

* Name: Represents the name of that particular record.

* ID and version: The next line represents the ID and the version of that record. Every record has a specific ID associated with it and a version which represents the number of times; it has been modified.

* **[Type](https://dissys.github.io/sbol-owl/sbol-owl.html#type)**: This specifies the category of biochemical or physical entity. For example DNA, protein, or small molecule that a ComponentDefinition object abstracts for the purpose of engineering design.

* Generated from: Represents the source from where that record had been generated from.

* Then, we've got five clickable options, that are:

   * **[Download](https://synbiohub.github.io/userdocumentation/#32-downloading-the-information)**
 
   * **[Search](https://synbiohub.github.io/userdocumentation/#1-searching-for-information)**

   * **[Share](https://synbiohub.github.io/userdocumentation/#6-data-sharing-mechanisms)**

   * **Back**: This option navigates back to the main page of the collection, which that particular record is a part of.

   * **[Add to a collection](https://synbiohub.github.io/userdocumentation/#6-add-to-an-existing-collection)** 

 


*  Then we have the details of that record. This consists of the following:

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



* There may be additional clickable sections after the attachments menu. These have been added via, **[visualisation plugins](https://github.com/SynBioHub/Plugin-Visual-Seqviz)**.


* Then, we have a section, titled **Member of these collection**, which displays the collection, of which that particular record is a part of.   


### 2.1.2 Viewing a collection

**[Collection](https://dissys.github.io/sbol-owl/sbol-owl.html#Collection)**, basically groups together a set of TopLevel objects that have something in common. 

On a collection's home page, other than the details mentioned in the general section, you'll be able to view a section titled, **members**. 
This sections basically contains, the list of records that is included in this particular section.
A general description of this section is as follows:

* **Filtering the Table**: The first parameter in this section is of filtering the table of contents. This is basically a dropdown menu, which contains various parameters base upon which the table of contents can be filtered. It contains various options such as showing all objects, showing only root objects, biopic:complex, etc..  You may select the option of your choice, from this dropdown menu and then click on filter. This will filter the table and display only those contents which'er as per the parameter that you have selected.

* **Number of Entries**: This is also a dropdown menu, which contains certain integer strings. The number of records you want to be displayed on a single page, can be controlled by this option. So, you can choose the value as per your own convenience, which in turn shall display that many records on a single page.

* **Search**: By using this search option, you can search for the records of your own choice, just by providing its name. Therefore, for searching a record contained in the table, you need to provide its exact name string.

* **Table**: Then we have is the table of contents. It contains the records that are in that very particular collection. This is a sortable table and can be sorted on the basis of multiple parameters ranging from identifier, type or description.

The header of the table as explained as follows:

| Table Header        |  Description         |
|---------------------|----------------------|
| Name                | This contains the name of each and every record that is in that collection, that is provided by the user who had submitted that particular record. Just besides the header there is small figure, clicking on which shall sort this table on the basis of reverse priority of alphabets i.e, Z-A|
| Identifier         | This contains the ID or the identifier of that particular record,that is provided by the user who had submitted that particular record. ust besides the header there is small figure, clicking on which shall sort this table on the basis of reverse priority of alphabets i.e, Z-A|
| Type | This represents the type of the record, i.e. whether it is a module, sequence, activity, etc.|
|Description | This is a brief description, that is provided by the user, who'd submitted that particular records. This description, in brief describes, what that particular record does. |
--------------------------------------------------------------------
### 2.1.3 Viewing a Module

A **[Module](https://dissys.github.io/sbol-owl/sbol-owl.html#ModuleDefinition)**, basically represents a grouping of structural and functional entities in a biological design.
Once you've successfully navigated to the Module's home page, other than the parameters described in the general section, you'll be able to view a few other the parameters, as follows:

* Type: The record type, as is obvious will be displayed as **Module**. A **[Module](https://dissys.github.io/sbol-owl/sbol-owl.html#ModuleDefinition)**, basically represents a grouping of structural and functional entities in a biological design.

Just below the clickable options, the **[VisBol navigator](https://app.dimensions.ai/details/publication/pub.1055140785)** is located, which displays the structure of that particular module. VisBOL is a Web-based application that allows the rendering of genetic circuit designs, enabling synthetic biologists to visually convey designs in SBOL visual format. VisBOL designs can be exported to formats including PNG and SVG images to be embedded in Web pages, presentations and publications. The VisBOL tool enables the automated generation of visualizations from designs specified using the Synthetic Biology Open Language (SBOL) version 2.0, as well as a range of well-known bioinformatics formats including GenBank and Pigeoncad notation. VisBOL Navigator also has zooming capabilities. This, graphically represents the structure of the module. By hovering your pointer over this structure, you can view the following attributes of that particular module i.e, type of resource, identifier, name and role of the module.

Then, what we have is the section titled, **[functional components](https://dissys.github.io/sbol-owl/sbol-owl.html#FunctionalComponent)**. A FunctionalComponent is an instance of a ComponentDefinition being used as part of a ModuleDefinition. The ModuleDefinition describes how the that describes how the FunctionalComponent interacts with others and summarizes their aggregate function. The parameters included in this section are described in the table below:

|  Parameter Name        |        Description    |
|------------------------|-----------------------|
| **[Access](https://dissys.github.io/sbol-owl/sbol-owl.html#access)/[Direction](https://dissys.github.io/sbol-owl/sbol-owl.html#direction)** | 1) **Access**: The access property is a REQUIRED URI that indicates whether the ComponentInstance can be referred to remotely by a MapsTo on another ComponentInstance or Module contained by a different parent ComponentDefinition or ModuleDefinition (one that does not contain this ComponentInstance).  2) **Direction**:Each FunctionalComponent MUST specify via the direction property whether it serves as an input, output, both, or neither for its parent ModuleDefinition object. |
| **[Definition](https://dissys.github.io/sbol-owl/sbol-owl.html#definition)** and **[MapsTo](https://dissys.github.io/sbol-owl/sbol-owl.html#MapsTo)**    | 1) **Definition**: The definition property is a REQUIRED URI that refers to the ComponentDefinition of the ComponentInstance. ComponentDefinition effectively provides information about the types and roles of the ComponentInstance.  2) **MapsTo**: When ComponentDefinition and ModuleDefinition objects are composed into structural and functional hierarchies using ComponentInstance and Module objects, it is often the case that some ComponentInstance objects are intended to represent the same entity in the overall design. The purpose of the MapsTo class is to make these identity relationships clear and explicit. For example, consider a ModuleDefinition for a genetic inverter that includes a FunctionalComponent for an abstract repressor protein. When this ModuleDefinition is instantiated within a “higher level” ModuleDefinition that includes a FunctionalComponent for a LacI protein, the MapsTo object can be used to indicate that the repressor protein in the first ModuleDefinition is LacI in the context of the composite design. |
| **[Public](https://dissys.github.io/sbol-owl/sbol-owl.html#public)** and **[Inout](https://dissys.github.io/sbol-owl/sbol-owl.html#inout)** | 1) **Public**: Indicates that a ComponentInstance MAY be referred to by remote MapsTo objects. 2) **Inout**: Indicates that the FunctionalComponent is both an input and output.|
--------------------------------------------------------------------

Subsequently, just below the functional components we have the **[Interactions](https://dissys.github.io/sbol-owl/sbol-owl.html#Interaction)** section. Interaction basically, provides a more detailed description of how the FunctionalComponent objects of a ModuleDefinition are intended to work together. It has a table consisting of the following attributes:

| Name     |      Description      |
|-------------|---------------------|
| **[Interaction](https://dissys.github.io/sbol-owl/sbol-owl.html#Interaction)**/**[Participation](https://dissys.github.io/sbol-owl/sbol-owl.html#Participation)**| 1) **Interaction**: Provides more detailed description of how the FunctionalComponent objects of a ModuleDefinition are intended to work together.   2) **Participation**: Each Participation represents how a particular FunctionalComponent behaves in its parent Interaction. |
| **[Participant Definition](https://dissys.github.io/sbol-owl/sbol-owl.html#definition)** | The definition property is a REQUIRED URI that refers to the ComponentDefinition of the ComponentInstance. As described in the previous section, this ComponentDefinition effectively provides information about the types and roles of the ComponentInstance.|
| **[Type](https://dissys.github.io/sbol-owl/sbol-owl.html#type)**/**[Role](https://dissys.github.io/sbol-owl/sbol-owl.html#role)** | 1) **Type**: Specifies the category of biochemical or physical entity. For example DNA, protein, or small molecule that a ComponentDefinition object abstracts for the purpose of engineering design. For DNA or RNA entities, additional types fields are used to describe nucleic acid topology (circular / linear) and strandedness (double- or single-stranded).  2) **Role**: Clarifies the potential function of an entity in a biochemical or physical context. When it is used for ComponentDefinitions, it MUST identify terms from ontologies that are consistent with the types property of the ComponentDefinition. For example, the roles property of a DNA or RNA ComponentDefinition could contain URIs identifying terms from the Sequence Ontology (SO). It may be a product, genetic production, template, etc.|







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

Additional download options may be available via the use of **[download plugins](https://synbiohub.github.io/plugins/#34-download)**.



