Welcome to the SONiC NAS Host Adapter.
---------------------


This SONiC repo contains the manifest file for the repo tool used to pull down sources for the SONiC NAS Project.

The SONiC NAS project is the SAI host adapter originally written by Dell contributed to the SONiC project.   

Getting the code
================

To get the sources for the SONiC NAS host adapter run the following command.

**repo init -u [URL with the manifest]**

After this completes successfully, then you can follow it up with the following command.

**repo sync**

Repo  sync will download all of the sources that you need to build the SONIC NAS host adapter.  In addition to the sources, you will also need some binary libraries for the SAI.  Currently the SAI is not open sourced entirely as it is based on Broadcom's SDK and there is no open source SAI implementation from Broadcom at this time.


Setting up the build environment
--------------------------------
The SONiC NAS build environment relies on a Docker environment in which to build the sources.  

To setup your Docker environment use the script in SONiC-build-tools called sonic_setup.  This script will build a docker container called docker-sonic which will be used by the build scripts.





