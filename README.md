
Welcome to the SONiC NAS Host-Adapter
======================================
This SONiC repo contains the manifest file for the repo tool used to pull down sources for the SONiC NAS Project. The SONiC NAS project is the SAI Host-Adapter originally written by Dell and contributed to the SONiC project. It is assumed that the user is familiar with Linux and has some basic development knowledge.   

Reading the documentation
-------------------------
Comprehensive documentation is available at [SONiC NAS Documentation](https://github.com/Azure/sonic-nas-manifest/wiki).

Getting SONiC NAS
-----------------
There are two ways to get the SONiC NAS:
- Download and install the binaries - see the [installation](#Installation) instructions for details.
- Build from scratch - see the step-by-step instructions below to build the project.
 
The build environment
--------------------------------
Prerequisites:

Updated environment: sudo apt-get update
- GIT: sudo apt-get install git
- Repo: Install 'repo' using the instructions provided at http://source.android.com/source/downloading.html
```
    Make sure you have a bin/ directory in your home directory and that it is included in your path:
    $ mkdir ~/bin
    $ PATH=~/bin:$PATH
    Download the Repo tool and ensure that it is executable:
    $ curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
    $ chmod a+x ~/bin/repo
```
- apt-utils: sudo apt-get install apt-utils
- For docker environment setup, see the [Docker environment setup guide](https://docs.docker.com/engine/installation/linux/ubuntulinux/).
```
    sudo apt-get install docker.io
    sudo apt-get install docker-engine
    sudo service docker start
```
- To avoid running docker commands as root (with sudo):
```
    sudo groupadd docker ### The 'docker' group might already exist
    sudo gpasswd -a ${USER} docker ### Add your user id to the 'docker' group
    sudo service docker restart
```
- You may have to log out/in to activate the changes to groups   
- Ensure you have proper permissions to clone source file (SSH keys must be installed)

Build environment recommendations:
- Intel multi-core system 
- Ubuntu 16.04 or later (desktop edition with Python installed)
- 20G of free disk space 
- Bash (most shell commands in the documentation or this page refer to bash commands - we like csh as well)

> NOTE: You will need to setup your ssh keys with Github [Settings->keys](https://github.com/settings/keys) as we are using git over ssh. 

Clone the source code
---------------------
To get the source files for the SONiC NAS Host-Adapter, run the commands in an empty directory (root directory). For example ~/dev/sonic/:
```
repo init -u ssh://git@github.com/Azure/sonic-nas-manifest.git
repo sync
```

The "repo sync" command downloads all of the source files that you need to build the SONIC NAS Host-Adapter. 
In addition to the source files, you will also need some binary libraries for the SAI. The SAI is currently not open 
sourced entirely as it is based on Broadcom's SDK and there is no open source SAI implementation from Broadcom at this time.

All the build scripts are found in the [SONiC Build Tools repo](https://github.com/Azure/sonic-build-tools) and will be downloaded as part of the above "repo sync".

Building the code
-----------------
Setup your path to include the sonic-build-tools/scripts folder (if you plan to run this command often, you could optionally add it to the .bashrc):
```
cd sonic-build-tools/scripts
export PATH=$PATH:$PWD
```

SONiC NAS Docker environment
----------------------------
To setup your Docker SONiC NAS image, use the script in the sonic-build-tools/scripts folder called sonic_setup. This script will build a docker container called docker-sonic which will be used by the build scripts:
```
cd sonic-build-tools/scripts/
sonic_setup
```

Test your environment
---------------------
You can run sonic_build in the directory sonic-logging (sonic-logging repository): 
```
cd sonic-logging
sonic_build -- clean binary
```

Building one repository
-----------------------
Refer to the corresponding README.md file associated with the repo for the specific build commands (and package dependencies).

Building all repositories
---------------------------
Issue the "sonic_build_all" command from the root directory to build all repos and create packages in the same root directory.
```
sonic_build_all
```

Installation
------------
Once all of the repos have been built you can then install the created ONIE Debian x86_64 image. You can then install all of the build packages, along with the other Debian files you downloaded earlier in the root directory.

See the [SONiC NAS documentation](https://github.com/Azure/sonic-nas-manifest/wiki/Install-SONiC-Host-Adapter-on-Dell-S6000-Platform) for more installation information.
