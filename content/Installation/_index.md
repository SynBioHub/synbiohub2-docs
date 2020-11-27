---
title: "Installation"
date: 2020-09-04T20:30:59+05:30
draft: true
weight: 10
---

### General
The docker-compose files in this repository represent various configurations for deploying SynBioHub.
The files can be layered with Docker Compose's [multiple file](https://docs.docker.com/compose/reference/overview/#specifying-multiple-compose-file) capabilities. 

The base configuration, described with `docker-compose.yml`, is simply SynBioHub, its graph database Virtuoso, and an autohealer.

To run the base configuration:

1. Before trying to run SynBioHub locally on your PC, Make sure that you've Git and Docker installed.

  * Git:-
    
       For MacOS, click [here](https://git-scm.com/download/mac).
    
       For Windows OS, click [here](https://git-scm.com/download/win)
    
       For Linux/Unix OS, click [here](https://git-scm.com/download/linux).
    
    
  * Docker:-
       
       For MacOS, click [here](https://docs.docker.com/docker-for-mac/install/).
    
       For Windows OS, click [here](https://docs.docker.com/docker-for-windows/install/).
    
       For Linux OS, click [here](https://docs.docker.com/engine/install/).
       

2. Open the terminal/cmd.

3. Navigate to the directory where you want to install SynBioHub.

   For Mac/Linux/Windows OS use the following command to navigate: 
   
   	```cd directory_name```
   

4. Subsequently, enter the following command into your terminal:

	```git clone https://github.com/synbiohub/synbiohub-docker```

5. Then, enter the following command to start the local instance of SynBioHub:
      
        
	```docker-compose -f ./synbiohub-docker/docker-compose.yml up```

   
6. In your browser search for localhost:7777 and it'll take you to a setup page when you'll run it for the very first time.

   [In case of Linux OS, if you face any permission errors, then simple insert **sudo** before every statement]

7. The following command stops a local instance of SynBioHub:

      ```docker-compose -f ./synbiohub-docker/docker-compose.yml down```
  	

### With SBOLExplorer
You can also run SynBioHub, by using SBOlExplorer.
To add [SBOLExplorer](https://github.com/michael13162/SBOLExplorer), add the `docker-compose.explorer.yml` to the main docker-compose, i.e. for step 5 run the following command: 

``` sysctl -w vm.max_map_count=262144 ```

``` docker-compose -f ./synbiohub-docker/docker-compose.yml -f ./synbiohub-docker/docker-compose.explorer.yml up```

**Presently, the command ```sysctl -w vm.max_map_count=262144``` runs only on linux, due to OS upgrades on Mac OS***
### With Plugins
To add plugins to the configuration, change the command mentioned in step 5 to: 

``` docker-compose -f ./synbiohub-docker/docker-compose.yml -f ./synbiohub-docker/docker-compose.explorer.yml -f ./synbiohub-docker/docker-compose.<Plugin 1 File Name>.yml -f ./synbiohub-docker/docker-compose.<Plugin 2 File Name>.yml up ```

Note that all plugins are added before the `up` and each is preceeded by `-f `. For example, to run the configuration with the VisualIgem plugins and the VisualSeqviz plugin run:

```docker-compose -f ./synbiohub-docker/docker-compose.yml -f ./synbiohub-docker/docker-compose.explorer.yml -f ./synbiohub-docker/docker-compose.pluginVisualIgem.yml -f ./synbiohub-docker/docker-compose.pluginVisualSeqviz.yml up```

A table of currently available plugins can be found **[here](https://synbiohub.github.io/synbiohub-docker/#plugins)**.





## Installation from source

Follow the instructions on the following [GitHub README](https://github.com/synbiohub/synbiohub) to install SynBioHub locally onto your system. 



