
Welcome to the SONiC NAS Host Adapter.
======================================

This SONiC repo contains the manifest file for the repo tool used to pull down sources for the SONiC NAS Project.

The SONiC NAS project is the SAI host adapter originally written by Dell contributed to the SONiC project.   


Reading the documentation
--------------------------------
Comprehensive documentation is available at the following link: [SONiC NAS Documentation](http://confluence.force10networks.com/pages/viewpage.action?spaceKey=OPS&title=OS10%20Open%20Source%20Documentation)


Setting up the build environment
================================
Build Environment Recommendations:
- Intel multi-core system 
- We recommend Ubuntu 14.04 or later
- 20G of free disk space 


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
repo init -u ssh://git@stash.force10networks.com/sonic/sonic-nas-manifest
repo sync

Repo  sync will download all of the sources that you need to build the SONIC NAS host adapter.  In addition to the sources, you will also need some binary libraries for the SAI.  Currently, the SAI is not open sourced entirely as it is based on Broadcom's SDK and there is no open source SAI implementation from Broadcom at this time.



