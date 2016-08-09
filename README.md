
Welcome to the SONiC NAS Host Adapter
======================================
This SONiC repository contains the manifest file for the repo tool used to pull down sources for the SONiC NAS Project. The SONiC NAS project is the SAI host adapter originally written by Dell and contributed to the SONiC project. It is assumed that the user is familiar with Linux and has some basic development knowledge.   

Documentation
-------------------------
Comprehensive information is available at [SONiC NAS Documentation](https://github.com/amybuck/sonic-nas-manifest)


Getting SONiC NAS
-----------------
There are two ways to get SONiC NAS:

1. Download and install the binaries (See installation instructions for more info).
2. Build from scratch (see below for step by step instructions).
 

Build Environment
--------------------------------
Build Environment prerequisites:

Updated environment: sudo apt-get update
- GIT: sudo apt-get install git
- Repo: Install 'repo' using the instructions provided at: http://source.android.com/source/downloading.html
```
      Make sure you have a bin/ directory in your home directory and that it is included in your path:
      $ mkdir ~/bin
      $ PATH=~/bin:$PATH
      Download the Repo tool and ensure that it is executable:
      $ curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
      $ chmod a+x ~/bin/repo
```
- apt-utils: sudo apt-get install apt-utils
- For docker environement setup, follow the [Docker environment setup guide](https://docs.docker.com/engine/installation/linux/ubuntulinux/).
```
sudo apt-get install docker.io
sudo apt-get install docker-engine
sudo service docker start
```
- To avoid running docker commands as root (with sudo), follow these steps:
```
sudo groupadd docker ### The 'docker' group might already exist
sudo gpasswd -a ${USER} docker ### Add your user id to the 'docker' group
sudo service docker restart
```
- You may have to log out/in to activate the changes to groups   
- Ensure you have proper permissions to clone source file (SSH Keys must be installed)

Build Environment Recommendations:

- Intel multi-core system 
- We recommend Ubuntu 16.04 or later (Desktop edition with Python installed)
- 20G of free disk space 
- Bash (most shell commands displayed in the documentation or this page refer to bash commands - we like csh as well)

Clone Source Code
---------------------
To get the source files for the SONiC NAS host adapter run the following commands in an empty directory (root directory). For example ~/dev/sonic/:
```
repo init -u ssh://git@github.com/Azure/sonic-nas-manifest.git
repo sync
```

The repo sync command will download all of the source files that you need to build the SONIC NAS host adapter. In addition to the source files, you will also need some binary libraries for the SAI. Currently, the SAI is not open sourced entirely as it is based on Broadcom's SDK and there is no open source SAI implementation from Broadcom at this time.

All build scripts are found in [SONiC Build Tools repo](https://github.com/Azure/sonic-build-tools) and will be downloaded as part of the above "repo sync".

Building Code
-----------------
Setup your path to include the sonic-build-tools/scripts folder (if you plan to run this command often, you can optionally add it to the .bashrc):
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

Test Environment
---------------------
To test the environment, you can run sonic_build in the directory sonic-logging (the sonic-logging repository): 
```
cd sonic-logging
sonic_build -- clean binary
```

Building Single Repository
-----------------------
Please refer to the corresponding README.md file, associated with the repo for the specific build commands (and package dependencies).

Building All Repositories
---------------------------
To build all repos:

- Download the SAI development binary packages to the root folder. (The link to be provided)
- Then build all with the following command:
```
sonic_build_all
```
The above steps will build all of the repos and create packages in the same root directory.

Installation
------------
Once all of the repos have been built then you can install the created ONIE Debian x86_64 image. Then install all of the build packages along with the other Debian files you downloaded earlier from in the root directory. See the SONiC NAS documentation for more information on the installation.
