# HTL3 Rennweg Vienna TYPO3 Kickstart Repository

This repository features a quickstart into the TYPO3 universe for people wanting to host their own server locally.
For this purpose a docker compose file is available, which makes use of https://github.com/martin-helmich/docker-typo3 and a MariaDB image.

In the current version this 

## Step-by-step guide
* Install Docker (e.g.: for Windows: https://www.docker.com/docker-windows, Mac: https://www.docker.com/docker-mac or Ubuntu: https://www.docker.com/docker-ubuntu) and if needed (e.g. on Ubuntu) docker-compose (https://docs.docker.com/compose/install/)
* Get the contents of this repository (e.g.: into your Windows "Own Documents" folder)
    * Recommended: use GIT to clone this repository (e.g.: ` git clone https://github.com/Weissheiten/typo3-htl3r.git typo3-htl3r ` via a command prompt)
    * NotRecommended but possible: Download ZIP from https://github.com/Weissheiten/typo3-htl3r (top right) and extract the contents to a folder of your choice
* Get the containers running
    * Change to the folder in which you did save the files (`dir` or `ls` depending on your system should show this readme and the docker-compose.yml)
    * use the command: `docker-compose up`
    * get a coffee while docker prepares the containers (probably it won't need that long, but a coffee is a coffee)
* Open your browser and surf to http://localhost
    * You should see the install tool now (at this moment of time it will include a warning! see below)
* Fix the PCRE error (soon to be fixed inside the image - to this step will not be necessary in the future)
    * Enter the command shell of the Docker container hosting TYPO3
        * On Windows and Mac this can be easily achieved by right clicking the Docker symbol (the whale) in your task bar and opening "Kitematic"
            * click on the running container (most probably named typo3htl3r_typo3-web_1) and the "EXEC" icon in the top bar - this should take you to the shell
            * now update the PCRE version: copy and paste the commands
                * `cd /tmp`
                * `wget http://ftp.de.debian.org/debian/pool/main/p/pcre3/libpcre3_8.39-3_amd64.deb`
                * `dpkg -i libpcre3_8.39-3_amd64.deb`
                * `rm -f libpcre3_8.39-3_amd64.deb`
            * you can type `exit` to leave the shell
* Inside your main shell (the one where you do the docker-compose commands) restart the containers
    * `docker-compose stop`
    * `docker-compose start` (we only need "up" to build, create start and attach the containers once, unless we want to start over)
* Open your browser and surf to http://localhost
    * Follow the installation instructions
    * Remember that you want to "Manually configure your MySQL TCP/IP connection"
    * Your username and password are located in the docker-compose.yml file (typo3htl / typo3htl) - you usually will NOT want to connect with the root user
    * Your Host is the name of the DB container: typo3-db
    * You can use the empty existing "typo3" database
    * choose site name, username and password for your TYPO3 installation as you see fit

## Optional steps
* To get started get to the backend and login (http://localhost/typo3)
* Click on Extensions in the list menu (the one on the left)
* switch the dropdown in the top bar to "Get Extensions"
* search for "introduction"
* click on download (cloud icon with the arrow) and "resolve dependencies" (installing the bootstrap package along)
* surf to http://localhost/ and check out the introduction package

## Getting to know TYPO3
Ready to explore TYPO3? Jump right into content editing. You can find an easy step-by-step path which even covers all the topics of the official TYPO3 CMS Certified Editor certification at: https://www.skilldisplay.eu/de/skillpfade/cms-certified-editor-tcce/
The whole learning process is broken down into single skills and each features goals and learning resources. You can see all of them in any way - but if you want to keep track of your progress, register and mark everything you learned with the "Self-SkillUp" button!

