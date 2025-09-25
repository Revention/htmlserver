# HTML-Server

## Overview

This is a project focused on creating a webserver for development of html, css and javascript. De html server is based on nginx and runs in a container environment. The image is available for download on docker hub. If you want to check the sourcecode or want to build the image yourself, the source-code is available at github.

Below you will find the url's for both dockerhub and github.

Dockerhub URL :  <https://hub.docker.com/repository/docker/revention/htmlserver/general>  
Github URL:     <https://github.com/Revention/htmlserver/>

You can create the htmlserver by downloading the pre-build image from dockerhub. This wil ensure that everything is working as intended and is recommended if you prefer simplicity and quickly starting on your website developement. [Pre-build](#the-docker-route)

If you want to have full control and have the ability to check or change the sourcecode you are advised to start with cloning the github repository. [Sourcecode](#the-github-route)

### The structure of the project

The structure of the project exists of three directories. One parent directory and two child directories.  

> ~/htmlserver/  
>     ~/htmlserver/html  
>     ~/htmlserver/src  

#### Directory description

> htmlserver\\
 
This is the parent directory

> html\\

This directory is used when building the dockercontainer and should have all the html, css and javascript files you need to display your website.  Copy your html file(s) to this directory here!

> src\\

The sourcefile directory which holds the docker files needed to build the image

## The Docker route
You should have some experience with the commandline and have docker installed.

### Get the image
On dockerhub there is an image available which can be used.  
`docker pull revention/htmlserver`

### Run the container
`docker run -d --name htmlserver -p 8080:80 -v "$(pwd)/html":/usr/share/nginx/html:ro revention/htmlserver`

> -d container runs in detached mode  
> --name naam van de container  
> -p poortnummers gemapt van poort 80 (intern container) naar 8080 op localhost  
> -v volume voor het dynamisch updaten van de webserver bij aanpasing

### Add your website files
You should manually copy the html, css and javascript files including the directory structure to the html directory. The html file should be (re)named to index.html.

`cp -R ~/some_website_directory ~/html/`

### Check the website in your browser
To see if everything works goto `http://localhost:8080` in your prefered browser.

## The Github route
This is the part of the manual which you need if you want to build the developers website from scratch. <em>This is not needed if you have followed the Docker route succesfully.</em>

It is assumed that you are familier with the commandline and working in the terminal aswell as experience with git and github. Both git and docker should be installed on you workstation or laptop you want to do the development of the website.

### Build from scratch
To build the htmlserver from scratch you need to download the sourcecode from github. The url for this is posted above in the [overview](#overview) section. 


### Preparement
To create the structure for the project you should create those directories unless the already exist. To do this you can use the following: Go into the directory where you want to start from, I would suggest your home directory.


#### Goto home directory 
This will be the place where the sourcecode and the htmlfiles will be placed.  
`cd ~ `

#### Clone the github repository
To download the sourcecode files and create the directory structure.  
`git clone https://github.com/Revention/htmlserver.git`


#### Html directory
The html directory is not in the cloned source therefore we need to create it. The html files needed to run your website should be placed here. I would expect at least an index.html file and probably an css file and/or a javascript file. 

`mkdir  htmlserver/html`

#### Build command

To build the image from the commandline you should have downloaded the dockerfile from github and run the build command.

`docker build -f src/Dockerfile -t dev-html .`

> -f location of the dockerfile  
> -t tag of the docker image  


#### Run command

`docker run -d --name htmlserver -p 8080:80 -v "$(pwd)/html":/usr/share/nginx/html:ro dev-html`

> -d container runs in detached mode  
> --name naam van de container  
> -p poortnummers gemapt van poort 80 (intern container) naar 8080 op localhost  
> -v volume voor het dynamisch updaten van de webserver bij aanpasing

#### Check on running container

You can check if the container is running by issueing one of the following commands:

`docker ps`  
`docker container ls`  

This should give you the container id and run status. If nothing is showing but a header, please check with `docker container ls --all` if there is a container stopped.
