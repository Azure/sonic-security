# SONiC security architecture

This document is to describle the high level architecture and interfaces used externally and internally to identify the security attack surface:

See also:
[SONiC architecture](https://github.com/Azure/SONiC/wiki/Architecture)

## SONiC attack surface diagram
![](https://github.com/Azure/sonic-security/blob/master/sonic-attacksurface-diagram.png)

## External interfaces
As illustrated above, there are interfaces from outside to access SONiC:

### OOB network interface
This interface is usually used for initial provisioning like reimaging the box and ZTP etc. SONiC users may or may not use this interface for management or telemetry etc.

### Serial console
This interface is used for debug/diagonostic when the networking interface is not available or serial console needs to be used to reimage the box or collect log etc.

### In-band networking interface
This interface is the major interface for interacting with the box by most SONiC users.

- SSH  
This is used for operators/administrators to access the device.  Authentication is used but could vary for different SONiC users.  
Example authentication:  
TACACS+ based, SSH key-pair based and user/password based.

- Routing protocol  
Routing protocols are running between devices to form the routing connectivites. SONiC supports BGP protocol at the moment.

- SNMP  
SNMP protocol is running to extract device information and reporting to monitoring system. The information includes:  
Intefaces speeds, descriptions and stats.  
Queue stats.  
CPU/Memory utilization.  
LLDP information.

- LLDP  
LLDP protocol is used to advertise/retrieve point-to-point interfaces information with peers.

- SYSLOG  
Syslog is used to report events logged on the system to the centralized servers.  
Typically you configure the syslog server with UDP or TCP, and the SONiC device would stream the syslog events to the configured servers.
 
- gRPC based Telemetry  
This is the interface to get the telemetry information from SONiC device. The information includes the data in the database like interface stats, protocl state and interal table state etc. It could retrieve data from non-DB as well: CPU stats and memory stats etc. Athentication is provided for gRPC.   
This feature not enabled at the time of writing this document.

- wget/apt-get etc  
For installing packages/images, we could use wget or apt-get to download packages onto the SONiC devices. 

### HW access interface
- ASIC access interface  
This interface is used to talk to ASIC, it is running on top of ASIC vendor SDK. 

- plaform devices access interfaces  
Sysfs and platform drivers is used for acceessing platform devices like PSU, LED, Fan and transceivers.


## Internal interfaces
SONIC internally relies on the kernel and RedisDB to communicate between different components.

### Netlink messages
Essentially, these are using unix domain sockets. They are used to provide networking intefaces inforamtion (up/down, create/delete etc), routing entry infomration and neighbor entry inforamtion.

### RedisDB
RedisDB is the central place for communicating between SONiC related daemons. Unix domain sockets are used for producers and consumers to talk to the RedisDB.

### SAI interface
This is used to talk to ASIC SDK, interface is defined as per:
[SAI Github](https://github.com/opencomputeproject/SAI)

### Other kernel interfaces
Sysfs is used to talk to platorm drivers.
