    /***************************************************************************************/

    88888888ba  88888888888        db        88888888ba,   88b           d88 88888888888  
    88      "8b 88                d88b       88      `"8b  888b         d888 88           
    88      ,8P 88               d8'`8b      88        `8b 88`8b       d8'88 88           
    88aaaaaa8P' 88aaaaa         d8'  `8b     88         88 88 `8b     d8' 88 88aaaaa      
    88""""88'   88"""""        d8YaaaaY8b    88         88 88  `8b   d8'  88 88"""""      
    88    `8b   88            d8""""""""8b   88         8P 88   `8b d8'   88 88           
    88     `8b  88           d8'        `8b  88      .a8P  88    `888'    88 88           
    88      `8b 88888888888 d8'          `8b 88888888Y"'   88     `8'     88 88888888888  

GENERAL INFORMATION
============
This is a minimal version of Geocat Services (development only), meant to be run from the command line, without installing anything. The shipped services are:

* SFTP server
* Apt-Mirror [future development]
* Docker Registry [future development]
* Jenkins/SSL [disabled]

AUTHORS
=======
This work was originally created and maintained by joana.simoes@geocat.net

INSTALL
==========
REQUIREMENTS & INSTALLATION
------------
For supporting version '2' of the compose syntax, you will need docker-compose >= 1.6 and docker >= 1.10.0
Instructions for installing the docker engine on different OS and flavours can be found here:

https://docs.docker.com/engine/installation/

Instructions for installing docker-compose can be found here:

https://docs.docker.com/compose/install/

Note that if you are a non-Linux user, you will need to install docker-machine in addition to docker and compose.
You may check the requirements section first. After that, to build and run the system for the first time you want to go to the root directory and type:

_curl https://raw.githubusercontent.com/doublebyte1/geocat_services_git/master/docker-compose.yml | docker-compose -f - up -d_

You can stop the system, just by typing:

 _docker-compose stop_

After creating the containers, you can start the system at any time with:

 _docker-compose start_

**Note:** Before building the images, you must set some **environmental variables**: 
* gitlab_user: GitLab user on Helios.
* gitlab_pass: GitLab password on Helios.
* RSYSMOND_license_key: NewRelic License key.

Default Configuration
---------------------
The sftp container uses a default username and password, stated on docker compose ("admin", "somepass").

Using GeoCat Services
----------------
When the system is up and running, you can access the SFTP server with this information:

 * IP address: localhost
 * Port: 2222
 * username: admin
 * password: somepass

For instance:

 _sftp -P 2222 admin@localhost_
 
The files placed on the folder /share will be read by the docker images.
 
Recreating Containers
=====================

For recreating a multi-container system, launched with docker compose, you must stop it first. Then you can remove the containers with:

 _docker-compose rm_

And then build them again with:

 _docker-compose up_

Recreating Images
=================

For recreating images, you must remove each image individually with:

 _docker rmi [some-image]_

In order to remove an image, you must ensure *there are no containers running from this image*. If there are any containers instantiated from this image, you must stop & delete them first. 

Then you can rebuild the system with:

 _docker-compose up_

Copyright
========
Currently this product is licensed to GeoCat B.V.
