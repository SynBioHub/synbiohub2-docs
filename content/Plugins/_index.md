---
title: "Plugins"
date: 2020-09-04T20:30:59+05:30
draft: true
weight: 40
---

## What are plugins?
Plugins are modular stand-alone additions to SynBioHub. They function in a way that is similar to browser extensions. They can be installed separately from the browser/SynBioHub and provide additional ‘custom’ functionality to the browser/SynBioHub experience despite having a completely separate code base from the browser/SynBioHub. Though, they seem integrated to the user.

### Types of Plugins
Currently there are three types of plugins available: 
1. Submit: Submit plugins are available to use from the [submit endpoint](https://synbiohub.github.io/api-docs/?python#submission-endpoints). They work by taking in the file that is uploaded in the submit and processing it to return SBOL to the SynBioHub endpoint.

2. Visual: Visual plugins are available on all ‘endpoint’ pages, for example pages for components, sequences, activities, etc. Visual plugins return html to be displayed on the page.

3. Download: Download plugins are available on all ‘endpoint’ pages, for example pages for components, sequences, activities, etc. Download plugins return some kind of file which is downloaded by the user.

## Overview
* All plugins in actual sense are servers (i.e, a piece of software in a network that is used to provide services such as access to files or the routing of an e-mail to other pieces of software or hardware (clients) in the network). 

* All plugins have at least 3 endpoints: *Status*, *Evaluate*, and *Run*. SynBioHub sends a status request to the status endpoint, if the response is that the plugin is up and running, SynBioHub then sends an evaluate request. The evaluate request tests whether the plugin can handle the data that SynBioHub wishes to send. If the plugin responds positively, SynBioHub then sends data to the run endpoint and uses the final results in the appropriate manner for the plugin type. 

* Note that plugins are asynchronous meaning that the full SynBioHub page can load without having to wait for the plugin to have returned the  results. Subsequently, when the results are returned SynBioHub substitutes the received information for the placeholder it had used when loading the page initially.

## Installation
As the plugins are standalone servers & they don't have to be used in conjunction with SynBioHub. Though plugins have been developed to interface directly with SynBioHub, it is possible to install them and then interact with them via the API (from the command line or via a GUI interface such as [Postman](https://www.postman.com/)). Different methods of installation are discussed below. For those who're less-experienced with Programming, it is suggested that you should be using plugins with SynBioHub.

### 1. Using SynBioHub
To install plugins with synbiohub the easiest way is to use Docker Compose’s multiple file capabilities. (Note you will need to install docker desktop and open it as an administrator before the commands bellow can be carried out, hence refer to the installation page.) Carry out the following commands: -

1. Open the terminal.
2. Change to a directory to where can pull the SynBioHub-docker files. 
3. Enter the folllowing command: `git clone https://github.com/synbiohub/synbiohub-docker`
4. After executing the previous command, then paste the following command:-

`docker-compose --f ./synbiohub-docker/docker-compose.yml -f ./synbiohub-docker/docker-compose.explorer.yml -f ./synbiohub-docker/docker-compose.<Plugin 1 File Name>.yml -f ./synbiohub-docker/docker-compose.<Plugin 2 File Name>.yml up`

Note that all plugins are added before the up and each is preceeded by -f . This -f denotes files. For example, to run the configuration with the VisualIgem plugins and the VisualSeqviz plugin run the following command:-

`docker-compose --f ./synbiohub-docker/docker-compose.yml -f ./synbiohub-docker/docker-compose.explorer.yml -f ./synbiohub-docker/docker-compose.pluginVisualIgem.yml -f ./synbiohub-docker/docker-compose.pluginVisualSeqviz.yml up`

A full list of plugin file names and their descriptions can be found [here](https://synbiohub.github.io/synbiohub-docker/#plugins).

#### Common problems

The most common problems that you may face while executing the commands mentioned above are as follows:-

1. The plugins might try to use ports that are already in use. If upon running the above commands and then using `docker ps` not all of the ‘images’ that you expect are present then try the following command: `docker ps –a`. 
If you now see the image(s) you were missing with the status ‘created’ it suggests that they have a port clash. If this is the case you can go in the docker-compose file for the appropriate plugin and change the port number (the first four digit number under “ports”). Then try running step 4 of the above commands again.


2. If you've locally installed SynBioHub using the above commands it might cause issues in some plugins, that will receive urls that look like: ``http://localhost:7777/xxxxxxx``. Localhost in docker containers refers to the container itself. The problem is explained further [here](https://medium.com/it-dead-inside/docker-containers-and-localhost-cannot-assign-requested-address-6ac7bc0d042b). On Linux this problem is solvable and the solution cab be found on [stack overflow](https://stackoverflow.com/questions/31324981/how-to-access-host-port-from-docker-container) and on [docker](https://docs.docker.com/network/host/).


#### Adding plugins to the admin panel

After getting the plugins up and running you still have to add them to the admin panel in SynBioHub. Navigate to the plugin section of the admin panel. Choose the appropriate section i.e, rendering, submit, or download and give the plugin a descriptive name. Then in the url section there are several different options depending on exactly how the plugin was brought up:

* If plugins were brought up using docker compose:
Use `http://localhost:<port>/` e.g. `http://localhost:8093/` for the Excel Submit Library plugin Or use the following alternative: `http://<docker container name>:5000/` e.g. `http://synbiohub-docker_pluginSubmitExcelLibrary_1:5000/` for the Excel Submit Library plugin.

* Another alternative that is not recommended but still can be used is to enter `http://<synbiohub docker network ip address>:<port> /` e.g. `http://172.18.0.1:8093/` for the Excel Submit Library plugin when the synbiohub-docker network is "172.18.0.1".

* Find out the synbiohub-docker network ip by typing into the terminal the following command `docker inspect synbiohub-docker_default` and the address following ‘Gateway’ is the ip address you want. Note that this will change every time you run the docker compose command.

* If in the case that plugins are hosted elsewhere on a public server then simply use the url to access them e.g.: https://seqviz.synbiohub.org/ for the seqviz plugin (this method is also possible if you have named and exposed internal ports from your docker compose (this requires [caddy](https://caddyserver.com/)).

### 2. Using a Standalone Docker Container
If you just want to bring up the plugin as a stand-alone Docker container you can simply pull the image from docker hub. 

* First make sure you have docker-desktop installed for your OS. Then it should be open and running with admininstrative permissions. 

* Then in the terminal run the following command `docker run --publish <publish port>:5000 --detach --name <nickname of your choice> synbiohub/<docker image name>`.

e.g: `docker run --publish 8093:5000 --detach --name submit-plug synbiohub/plugin-submit-excel-library:snapshot` for the excel library submit plugin.
It is suggested that the same publish ports are used when using docker compose. The list of those ports can be found [here](https://synbiohub.github.io/synbiohub-docker/#plugins).


#### Common Problems
The most common problems that you may face while executing the commands mentioned above are as follows:-

1. Localhost:-  If the plugin is being run as a docker container that localhost may cause problems as localhost is considered within the container and won’t point to the localhost on your computer. The problem is explained further [here](https://medium.com/it-dead-inside/docker-containers-and-localhost-cannot-assign-requested-address-6ac7bc0d042b). On Linux this problem is solvable and solution can be found on [stack-overflow](https://stackoverflow.com/questions/31324981/how-to-access-host-port-from-docker-container and https://docs.docker.com/network/host/).

### 3. Using Standalone methods

Plugins can also be run without using docker. How this is done depends on the programming language and packages used to create the server. We've provided the documentation for two of the most common server choices, i.e python using flask and javascript using express.

#### A) Python Flask Servers
**NOTE**: You might have to add pandas to the requirements if you are running the plugins as standalone (this is not needed if you are running the plugin via docker since, we use a base image which contains pandas pre-installed as it is extremely difficult and highly buggy to install via docker on a python base image).

##### For Anaconda

1. Open the terminal
2. Clone the repository for the plugin (For example:-  `git clone https://github.com/SynBioHub/Plugin-Submit-Excel-Library.git`)
3. Change directory into the repository folder using the command ` cd <repo-name>`(For repo-name enter your local repository name).
Now, open the anaconda prompt and carry out the rest of the commands in the anaconda prompt.
4. Enter the following commmand: conda install --file requirements.txt
5. Then, enter the following command: `set FLASK_APP=app.py`
6. **OPTIONAL command**:  `set FLASK_ENV=development`
7. flask run --port 5000 (the -- port 5000 is optional instead of 5000 there any port numbercan be entered)
8. The server should then be accessible at http://localhost:5000/status. Hence, open your browser an the enter`http://localhost:5000/status'.

##### For Python

###### 1. Mac OS/Linux
1. Open the terminal.
2. Clone the repository using the command `git clone <Repo-Link>`(For Example:`git clone https://github.com/SynBioHub/Plugin-Submit-Excel
Library.git`)
3. Change directory into the repository folder using the command ` cd <repo-name>`(For repo-name enter your local repository name).
4. Enter the following command: `pip install -r requirements.txt`
5. Then, enter the following command: `export FLASK_APP=app`
6. Finally to start flask, enter the following command: `flask run`
7. The server should then be accessible at http://localhost:5000/status. Hence open your browser and enter `http://localhost:5000/status`

##### 2. Windows OS
1. Open the terminal
2. Clone the repository using `git clone <Repo-link>` (For Example `git clone https://github.com/SynBioHub/Plugin-Submit-Excel-Library.git`)
3. Change directory into the repository folder using the command ` cd <repo-name>`(For repo-name enter your local repository name).
4. Enter the following command: `pip install -r requirements.txt`
5. In the **Powershell**, enter the follwing command: $env:FLASK_APP = "hello", Command: set FLASK_APP=hello
6. Finally to run flask, enter the following commmand: `flask run`
7. The server should then be accessible at http://localhost:5000/status. Hence open your browser and enter `http://localhost:5000/status`.


For more information see [this](https://flask.palletsprojects.com/en/1.1.x/cli/).

#### B) Javascript Node.js with Express Servers

The following steps should be followed:-

1. Open the terminal.
2. Clone the repository using `git clone <Repo-Link>`(For example `git clone https://github.com/SynBioHub/ Plugin-Submit-Test-js.git`)
3. Change directory into the repository folder using the command ` cd <repo-name>`(For repo-name enter your local repository name).
4. Enter `npm install` (This installs all the requirements that requires npm to be installed onto your system: https://nodejs.org/en/download/).
5. Enter node app.js
The server should then be accessible at http://localhost:5000/status. Hence open your browser and enter `http://localhost:5000/status`.

## Writing Plugins

The following section explains everything you need to know about the syntax of writing plugins.

### Naming convention
For github repositories, the naming convention for plugin repositories is: 

Plugin-"Type"-"Description"-"Test"-"language"

**Note**: The words are separated by a dash (-) and every word but the program language is Proper case (Initial letter is capitalized and the further letters aren't).

For *Type* it is: Submit, Visual, Download

For *Test*: add the Test to the name if it is a framework plugin simply showing off how to write a particular plugin type

For *language*:

Python: no addition

Javascript: add "js"

Examples:
* Plugin-Submit-Excel-Library
* Plugin-Download-Test-js
* Plugin-Visual-Component-Use
The same name is then used for both the docker-compose and the docker image name:
Example.:
Repository: Plugin-Visual-Component-Use
Docker Compose File: docker-compose.pluginVisualComponentUse.yml (Note that the plugin is lowercase and then the rest of the words are capitalized but there aren't any spaces or dashes).

Docker Image Name: synbiohub/plugin-visual-component-use:snapshot (Note that there are no capitals in the docker image name).
















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

## Plugins-Table

The sortable table has already been implemented and can be found [here](https://synbiohub.github.io/synbiohub-docker/#plugins).
