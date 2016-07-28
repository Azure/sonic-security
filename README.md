
Welcome to the SONiC NAS Host Adapter.
======================================
This SONiC repo contains the manifest file for the repo tool used to pull down sources for the SONiC NAS Project.

The SONiC NAS project is the SAI host adapter originally written by Dell contributed to the SONiC project.

It is assumed that the user is familiar with Linux and has some basic development knowledge.   


Reading the documentation
-------------------------
Comprehensive documentation is available at the following link: [SONiC NAS Documentation](http://confluence.force10networks.com/pages/viewpage.action?spaceKey=OPS&title=OS10%20Open%20Source%20Documentation)


Getting SONiC NAS
-----------------
There are two ways to get the SONiC NAS:
- Download and install the binaries. See the Installation Instructions for more details.
- Build from scratch. See the below for a step by step instruction to build the project.
 

The build environment
--------------------------------
Build Environment prerequisites:
Updated environment: sudo apt-get update
- GIT: sudo apt-get install git
- Repo: sudo apt-get install repo
- apt-utils: sudo apt-get install apt-utils
- For docker environement setup, follow the [Docker environment setup guide](https://docs.docker.com/engine/installation/linux/ubuntulinux/).
```
sudo apt install docker.io
sudo apt-get install docker-engine
sudo service docker start
```
- To avoid running docker commands as root (with sudo), follow these steps:
```
sudo grouped docker
sudo gpasswd -a ${USER} docker
sudo service docker restart
```
- You may have to log out/in to activate the changes to groups   
- Ensure you have proper permissions to clone source file (SSH Keys must be installed)

Build Environment Recommendations:
- Intel multi-core system 
- We recommend Ubuntu 14.04 or later
- 20G of free disk space 
- Bash (most shell commands displayed in the documentation or this page refer to bash commands - we like csh as well)

Clone the Source code
---------------------
To get the source files for the SONiC NAS host adapter run the following commands in an empty directory (root directory). For example ~/dev/sonic/:
```
repo init -u ssh://git@github.com/Azure/sonic-nas-manifest.git
repo sync
```

The command, “repo sync”, will download all of the source files that you need to build the SONIC NAS host adapter. 
In addition to the source files, you will also need some binary libraries for the SAI. Currently, the SAI is not open 
sourced entirely as it is based on Broadcom's SDK and there is no open source SAI implementation from Broadcom at this time.

Building the code
-----------------
Setup your path to include the sonic-build-tools/scripts folder (if you plan to run this command often, you could optionally add it to the .bashrc):
```
cd sonic-build-tools/scripts
export PATH=$PATH:$PWD
```

SONiC NAS Docker Environment
----------------------------
To setup your Docker SONiC NAS image, use the script in sonic-build-tools/scripts folder called sonic_setup. This script will build a docker container called docker-sonic which will be used by the build scripts:
```
cd sonic-build-tools/scripts/
sonic_setup
```

Test your environment
---------------------
To test the environment, you can run sonic_build in the directory sonic-logging (the sonic-logging repository): 
```
cd sonic-logging
sonic_build -- clean binary
```

Building one repository
-----------------------
Please refer to the corresponding README.md file, associated with the repo for the specific build commands (and package dependencies).

Building all repositories
---------------------------
In order to build all repos please follow these steps:
- Download the SAI development binary packages to the root folder. (The link to be provided)
- Then build all with the following command:
```
sonic_build_all
```

The above steps will build all of the repos and create packages in the same root directory.

Installation
------------
Once all of the repos have been built then you can install the created ONIE Debian x86_64 image. Then install all of the build packages along with the other Debian files you downloaded earlier from in the root directory.

See the SONiC NAS documentation for more information on the installation.
