# SONiC dependency tracker

SONiC uses Linux distribution Debian as base Operation System. At the time of writing this document, Debian 9.0 (Stretch) is used for master kernel.

SONiC utilize debian packages to support all functions. There are a few different categories for the packages running on the target. We are tracking the packages based on categories as describled later in the document.

Weekly meeting is scheduled to review the security updates from all the dependencies.  See detail info: [SONiC working group activities](https://github.com/Azure/sonic-security/wiki). Decision will be made about when and how to fix/patch the security issues if the fix is known or resource is assigned to investigate the issues.

A spreadsheet is maintained to keep the dependency history and up-to-dated security issues' status:
[SONiC Dependency Tracker File](https://docs.google.com/spreadsheets/d/1db5uvrd0ph_MBB43iHuNhnLb9klpU6e7NF6S0p3KmZ4/edit?usp=sharing)

## Packages from Debian repo:
SONiC installs packages on the host OS and dockers when building the image, the packages are getting from security repos as binaries. These packages are tracked by Debian security team.

The document here tracks up-to-date issues from debian:
[Debian Security Tracker](https://docs.google.com/spreadsheets/d/1db5uvrd0ph_MBB43iHuNhnLb9klpU6e7NF6S0p3KmZ4/edit#gid=0)

SONiC security team members are subscribled to debian-security-announce@lists.debian.org through:
[debian security announce](https://lists.debian.org/debian-security-announce/)

Weekly review is done against the latest Debian security advisor: 
[https://www.debian.org/security/2018/](https://www.debian.org/security/2018/) and [https://www.debian.org/security/2019/](https://www.debian.org/security/2019/)

## Package built from Debian source code:
In some cases, SONiC needs modify debian maintained source code by adding patches. The patches themselves were reviewed by SONiC community and merged by SONiC maintainers, while the source code security issues were tracked by Debian security team.

The document here tracks up-to-date repos used and related issues:

[SONiC Debian Security Tracker](https://docs.google.com/spreadsheets/d/1db5uvrd0ph_MBB43iHuNhnLb9klpU6e7NF6S0p3KmZ4/edit#gid=0)

[SONiC Upstream Source Code](https://docs.google.com/spreadsheets/d/1db5uvrd0ph_MBB43iHuNhnLb9klpU6e7NF6S0p3KmZ4/edit#gid=793990498)

SONiC security team members are subscribled to debian-security-announce@lists.debian.org through:
[debian security announce](https://lists.debian.org/debian-security-announce/)

Weekly review is done against the latest Debian security advisor:
[https://www.debian.org/security/2018/](https://www.debian.org/security/2018/) and [https://www.debian.org/security/2019/](https://www.debian.org/security/2019/)

## Packages built from vendor source
SONiC supports multiple ASICs and platforms.

To support different ASICs, OCP SAI is used as a standard interface to talk to different HW, See [SAI repo](https://github.com/opencomputeproject/SAI). ASIC vendors will provide source code under SLA and the community will publish binaries for SONiC end users. 

Platform vendors provide platform drivers for things like PSU, LED, FAN and transceiver etc. The code are published on github.

Above source code is tracked here:
[vendor source code](https://docs.google.com/spreadsheets/d/1db5uvrd0ph_MBB43iHuNhnLb9klpU6e7NF6S0p3KmZ4/edit#gid=1590257749)

## Packages built from other source
FRR(Free Range Routing) is well-known routing protocol stack derived from Quagga. Currently it is on 3.0 release branch. [FRR website](https://github.com/FRRouting/frr)

For security issues, we will track above website, and the security team members are subscribed to [announce@lists.frrouting.org](announce@lists.frrouting.org)  and [slack](https://frrouting.slack.com/)

The document here tracks up-to-date issues for FRR:
[FRR security](https://docs.google.com/spreadsheets/d/1db5uvrd0ph_MBB43iHuNhnLb9klpU6e7NF6S0p3KmZ4/edit#gid=614184260)


## SONiC own source code
SONiC own source code is designed and implemented by SONiC community, and follows the SDL mentioned here:
[SONiC SDL](https://github.com/Azure/sonic-security/blob/master/sonic-software-development-lifecycle.md)

The SONiC source code is tracked here:
[SONiC source code](https://docs.google.com/spreadsheets/d/1db5uvrd0ph_MBB43iHuNhnLb9klpU6e7NF6S0p3KmZ4/edit#gid=123193953)
