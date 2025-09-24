# HTML-Server

## Overview
This is a project focused on creating a webserver for development of html, css and javascript. De html server is based on nginx and runs in a container environment. The image is available for download on docker hub. If you want to check the sourcecode or want to build the image yourself, the source is available at github.

Below you will find the url's for both dockerhub and github.

Dockerhub URL :  <https://hub.docker.com/repository/docker/revention/htmlserver/general>  
Github URL:     <https://github.com/Revention/htmlserver/>

## The structure of the project
The structure of the project exists of three directories. One parent directory and two child directories.  

> ~/htmlserver/  
>     ~/htmlserver/html  
>     ~/htmlserver/src  

### Directory description

> htmlserver\\
 
This is the parent directory

> html\\

This directory is used when building the dockercontainer and should have all the html, css and javascript files you need to display your website.  Copy your html file(s) to this directory here!

> src\\

The sourcefile directory which holds the docker files needed to build the image

### Directory overview
To create the structure for the project you should create those directories unless the already exist. To do this you can use the following: Go into the directory where you want to start from, I would suggest your home directory.

#### Goto home directory  
This will be the place where the sourcecode and the htmlfiles will be placed.  
`cd ~ `

#### Clone the github repository  
To download the sourcecode files and create the directory structure.  
`git clone https://github.com/Revention/htmlserver.git`

#### html directory
The html directory is not in the cloned source therefore we need to create it. The html files needed to run your website should be placed here. I would expect at least an index.html file and probably an css file and/or a javascript file. 

`mkdir  htmlserver/html`

## Build command
To build the image from the commandline you can download the dockerfile from github and run the build command.

`docker build -f src/Dockerfile -t dev-html .`

> -f location of the dockerfile  
> -t tag of the docker image  

## Run command
`docker run -d --name htmlserver -p 8080:80 -v "$(pwd)/html":/usr/share/nginx/html:ro dev-html`

> -d container runs in detached mode  
> --name naam van de container  
> -p poortnummers gemapt van poort 80 (intern container) naar 8080 op localhost  
> -v volume voor het dynamisch updaten van de webserver bij aanpasing
