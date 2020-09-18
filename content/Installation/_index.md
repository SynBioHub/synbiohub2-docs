---
title: "Installation"
date: 2020-09-04T20:30:59+05:30
draft: true
---
## From Prebuilt Image

### Install Docker

Install [Docker](https://docs.docker.com/get-docker/) and [Docker-Compose](https://docs.docker.com/compose/install/) on your System.

### For Mac OS:

The following instructions are to be followed for installaing SynBioHub locally onto you system:-

a) Download git onto your Mac using ``` brew install git ``` and then configure you name and email using the following commands: 

`git config --global user.name "<your name>"`  and `git config --global user.name "<your email>" ` respectively.

b) Download Docker for Mac OS from [here](https://docs.docker.com/docker-for-mac/install/).

c) Start Docker-desktop.

d) Open your terminal and enter ` cd ` just to make sure that you're in your home directory at that instant.

e) Clone the synbiohub-docker repo using the following command :

 `git clone https://github.com/synbiohub/synbiohub-docker`.

f) Start a synbiohub instance with `docker-compose --file ./synbiohub-docker/docker-compose.yml up` or you may follow the alternate method, i.e using SBOL explorer. For installing SynBioHub through SBOL explorer use the following commands:-

`sysctl -w vm.max_map_count=262144`

`docker-compose --file ./synbiohub-docker/docker-compose.yml --file ./synbiohub-docker/docker-compose.explorer.yml up`.

g) In your browser search for localhost:7777 and it'll take you to a setup page when you'll run it for the very first time.


### General
The docker-compose files in this repository represent various configurations for deploying SynBioHub.
The files can be layered with Docker Compose's [multiple file](https://docs.docker.com/compose/reference/overview/#specifying-multiple-compose-file) capabilities. 

The base configuration, described with `docker-compose.yml`, is simply SynBioHub, its graph database Virtuoso, and an autohealer.

To run the base configuration:
1. Open terminal
2. `git clone https://github.com/synbiohub/synbiohub-docker`
3. `docker-compose --f ./synbiohub-docker/docker-compose.yml up`

### With Explorer
To add [SBOLExplorer](https://github.com/michael13162/SBOLExplorer), add the `docker-compose.explorer.yml` to the main docker-compose, i.e. for step 3 run `docker-compose --f ./synbiohub-docker/docker-compose.yml -f ./synbiohub-docker/docker-compose.explorer.yml up`

### With Plugins
To add plugins to the configuration change step 3 to: `docker-compose --f ./synbiohub-docker/docker-compose.yml -f ./synbiohub-docker/docker-compose.explorer.yml -f ./synbiohub-docker/docker-compose.<Plugin 1 File Name>.yml -f ./synbiohub-docker/docker-compose.<Plugin 2 File Name>.yml up`

Note that all plugins are added before the `up` and each is preceeded by `-f `. For example, to run the configuration with the VisualIgem plugins and the VisualSeqviz plugin run:

`docker-compose --f ./synbiohub-docker/docker-compose.yml -f ./synbiohub-docker/docker-compose.explorer.yml -f ./synbiohub-docker/docker-compose.pluginVisualIgem.yml -f ./synbiohub-docker/docker-compose.pluginVisualSeqviz.yml up`

### With Developmental SynBioHub
The `docker-compose.version.yml` can be added to another configuration, and simply contains the latest version of the SynBioHub docker image. 
This version does not even contain the Virtuoso image, so it should only be used by someone who knows what they are doing. 

## Plugins
This is a sortable table with plugin information. Click on the header to sort by that column.

  

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

## From Source

Follow the instructions on the following [GitHub README](https://github.com/synbiohub/synbiohub) to install SynBioHub locally onto your system. 

## NGINX configuration

Instructions for managing nginx server blocks can be found [here](https://www.digitalocean.com/community/tutorials/how-to-set-up-nginx-server-blocks-virtual-hosts-on-ubuntu-16-04#step-three-create-server-block-files-for-each-domain).

The server block for a SynBioHub installation listening on port 7777 is to the right 

```
client_max_body_size 800m;
proxy_connect_timeout 6000;
proxy_send_timeout 6000;
proxy_read_timeout 6000;
send_timeout 6000;
server {
        listen 80;
        server_name _;

        location / {
                proxy_set_header X-Real-IP  $remote_addr;
                proxy_set_header X-Forwarded-Server $host;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
                proxy_set_header Host $host;
                proxy_pass http://127.0.0.1:7777$request_uri;
        }
}
```
This is most useful when you would like to host SynBioHub on a subdomain alongside other content (using nginx as an HTTP proxy) or using HTTPS. 


