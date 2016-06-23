
Welcome to the SONiC NAS Host Adapter.
======================================
This SONiC repo contains the manifest file for the repo tool used to pull down sources for the SONiC NAS Project.

The SONiC NAS project is the SAI host adapter originally written by Dell contributed to the SONiC project.   


Reading the documentation
--------------------------------
Comprehensive documentation is available at the following link: [SONiC NAS Documentation](http://confluence.force10networks.com/pages/viewpage.action?spaceKey=OPS&title=OS10%20Open%20Source%20Documentation)


Getting SONiC NAS
-----------------
There are two ways to get the SONiC NAS. 

The First way is to download and install the binaries built from the sources on github.
See the [Installation Instructions](https://confluence.force10networks.com/display/OPS/Installing+SONiC+NAS+Host+Adapter+on+Dell+Platforms) for more details.

The second way to get SONiC NAS is to build it from scratch.  See the below section for instructions for building from scratch

The build environment
--------------------------------
Build Environment Recommendations:
- Intel multi-core system 
- We recommend Ubuntu 14.04 or later
- 20G of free disk space 
- Bash (most shell commands displayed in the documentation or this page refer to bash commands - we like csh as well)


Dockers
-------
The SONiC NAS build environment relies on a Docker environment in which to build the sources.  

Please refer to the [Docker website](http://www.docker.com) for more inforamtion on setting up and maintaining Docker environments.


SONiC NAS Docker Environment
----------------------------
To setup your Docker SONiC NAS image, use the script in SONiC-build-tools in the scripts folder called sonic_setup.  This script will build a docker container called docker-sonic which will be used by the build scripts.


Getting the code
================

It is assumed that the user is familiar with Linux and has some basic development knowledge.

To get the sources for the SONiC NAS host adapter run the following command.

**repo init -u [URL with the manifest]**

After this completes successfully, then you can follow it up with the following command.

**repo sync**

For example:
mkdir /srv/src/sonic ; cd /srv/src/sonic
repo init -u ssh://git@stash.force10networks.com/sonic/sonic-nas-manifest
repo sync

Repo  sync will download all of the sources that you need to build the SONIC NAS host adapter.  In addition to the sources, you will also need some binary libraries for the SAI.  Currently, the SAI is not open sourced entirely as it is based on Broadcom's SDK and there is no open source SAI implementation from Broadcom at this time.


Building the code
-----------------
Firstly, setup your path to include the sonic-build-tools/scripts folder.

For the sake of this section, we will assume that the code was installed in /srv/src/sonic

eg - from /srv/src/sonic 
export PATH=$PATH:$PWD/sonic-build-tools/scripts

Test your environment
---------------------
Run the following command from the /srv/src/sonic/sonic-logging directory (the sonic-logging repository):
sonic_build -- clean binary

If this generates a libsonic-logging debian package in the /srv/src/sonic directory.  If it doesn't exist, then something is wrong and you may want to re-read and perform the above steps again.


Building one repository
-----------------------
Read the README.md file in the correct repo for the build commands (and package dependencies).  


Building all repositories
---------------------------
Firstly, you will need to download the SAI development packages.  Assuming /srv/src/sonic again, place all of the SAI library packages and SAI development packages in this folder.

After this step, you should have the following directory listing:
 # list of deb files needed  #

After all of the required debian files have installed then you can do a:
sonic_build --all

That will build all of the repos and leave created packages in the /srv/src/sonic directory.

Once all of the repos have been built then you can install the created ONIE Debian x86_64 image and
then install all of the build packages along with the other debian files you downloaded earlier from
the /srv/src/sonic directory.

See the SONiC NAS documentation for more inforamtion on the [installation](https://confluence.force10networks.com/display/OPS/Installing+SONiC+NAS+Host+Adapter+on+Dell+Platforms).
