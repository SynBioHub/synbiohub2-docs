---
title: "Plugins"
date: 2020-09-04T20:30:59+05:30
draft: true

---


### Plugin Specifications
Plugins must provide three endpoints, /status, /evaluate, and /run. 

*Status endpoint*
The status endpoint should listen for HTTP GET requests and return an HTTP 200 OK and (optionally) a short message if the plugin service is ready to handle requests. Otherwise, an HTTP error code and short error message should be returned. 

*Evaluate endpoint*
The evaluate endpoint should listen for HTTP POST requests, and return an HTTP 200 OK if the request can be handled by the run endpoint. 
The body of evaluate requests sent to each plugin type is described below.

*Run endpoint*
The run endpoint should listen for HTTP POST requests, and return an HTTP 200 OK with the result of the plugin operation. 
The body of run requests sent to each plugin type is described below.

### Implementation
Plugins and SynBioHub will communicate using HTTP. The end user’s browser will not communicate with the plugin server.

#### Submission
For both the `evaluate` and `run` endpoints, SynBioHub will send a JSON object structured as follows:

` { manifest: { files: [ ... ] } } `

Each file in `files` will have the following parameters:

    1. `filename`: The name of the file

    2. `type`: the Content-Type of the file

    3. `url`: A URL where the file can be accessed

*Evaluate endpoint*

SynBioHub will send an HTTP POST request containing the manifest to the submit plugin's evaluate endpoint.
The plugin should respond with HTTP 200 OK if the plugin can handle the submission.

*Run endpoint*

SynBioHub will send an HTTP POST request containing the manifest to the submit plugin's run endpoint.
It will also send the `instanceUrl` parameter.
The plugin should respond with an HTTP response and file attachment, which represents the submission.

#### Download
*Evaluate endpoint*

SynBioHub will send an HTTP POST request to the download plugin's evaluate endpoint. The body of the request will contain a **JSON** containing:

    1. `type`: The RDF type of the top-level object

The plugin should respond with an HTTP 200 OK if the request can be handled.

*Run endpoint*

SynBioHub will send an HTTP POST request to the dwonload plugin’s run endpoint. The body of the request will contain a **JSON** object containing:

	1. `complete_sbol`: the single-use URL for the complete object to operate on

	2. `shallow_sbol`: the single-use URL for a summarized or truncated view of the object

	3. `top_level`: the top-level URL of the SBOL object

	4. `instanceUrl`: the top-level URL of the SBOL object 

	5. `size`: a number representing an estimate of the size of the object, probably triple count

The plugin should respond with an HTTP request and file attachment which represents the object.

#### Visualization
The response of visualization plugins should be **HTML** which will be displayed on the top-level page. Rendering responses may be cached to improve performance.

*Evaluate endpoint*

SynBioHub will send an HTTP POST request to the visualization plugin's evaluate endpoint. The body of the request will contain a **JSON** containing:

    1. `type`: The RDF type of the top-level object

*Run endpoint*

SynBioHub will send an HTTP POST request to the visualization plugin’s run endpoint. The body of the request will contain a **JSON** object containing:

	1. `complete_sbol`: the single-use URL for the complete object to operate on

	2. `shallow_sbol`: the single-use URL for a summarized or truncated view of the object

	3. `top_level`: the top-level URL of the SBOL object

	4. `instanceUrl`: the top-level URL of the SBOL object 

	5. `size`: a number representing an estimate of the size of the object, probably triple count

The plugin should respond with an HTML page to be rendered in-frame on the corresponding SynBioHub page. 

## Plugins-Table:

This is a sortable table with plugin information. Click on the header to sort by that column.
{{<table>}}

|Name|Type|Port|Language|Test|Description|Multi-Endpoint|Repository|File|
|--- |--- |--- |--- |--- |--- |--- |--- |--- |
|DownloadSnapgene|Download|8083|Python|No|||Plugin-Download-Snapgene|docker-compose.pluginDownloadSnapgene.yml|
|SubmitSnapgene|Submit|8084|Python|No|||Plugin-Submit-Snapgene|docker-compose.pluginSubmitSnapgene.yml|
|SubmitTest|Submit|8087|Python|Yes|Simply indicates that submit plugins are working and provides a framework to play with for plugin developers|No|Plugin-Submit-Test|docker-compose.pluginSubmitTest.yml|
|VisualComponentUse|Visual|8080|Python|No|Containing a co-use component sankey diagram, and the most used components bar graph endpoints|Yes|Plugin-Visual-Component-Use|docker-compose.pluginVisualComponentUse.yml|
|VisualIgem|Visual|3000|TypeScript|No|Containing endpoints for iGEM Main Page, iGEM Design Page, and iGEM Experience Page|Yes|Plugin-Visual-Igem|docker-compose.pluginVisualIgem.yml|
|VisualSeqviz|Visual|8085|Javascript|No|Shows the plasmid view and sequence view of components|No|sequence-view-plugin|docker-compose.pluginVisualSeqviz.yml|
|VisualServelet|Visual|8086|Javascript|Yes|Allows testing of file serving and provides a framework to play with for plugin developers|No|Plugin-Visual-Serve-Test-js|docker-compose.pluginVisualServelet.yml|
|VisualTest|Visual|8081|Python|Yes|Smply indicates that visualisation plugins are working and provides a framework to play with for plugin developers|No|Plugin-Visual-Test|docker-compose.pluginVisualTest.yml|
|VisualTestJS|Visual|8082|Javascript|Yes|Aimply indicates that submit plugins are working and provides a framework to play with for plugin developers|No|Plugin-Visual-Test-js|docker-compose.pluginVisualTestJS.yml|

{{</table>}}
