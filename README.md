Kojak - "Koji in an box"
========================

Kojak is a collection of scripts that can be used to automate the installation and configuration of the Koji build system. It is part of a productization effort to encourage the adoption of Koji for use in development, testing and staging environments.  The scripts included in this repository can be used to create a fully operational Koji instance on the local system or optionally as virtual machine utilizing the Libvirt visualization API and a kickstart file.  The virtual machine is based on a stock vanilla CentOS installation, to provide an automated "out of the box" solution, which may be used for development, testing and educational purposes.

Tool Chain
----------

Future implementations of Kojak will ship with a standardised tool chain designed to allow developers to build, test, deploy, verfiy and replicate product builds and their associated repositories in a consistent way.  The long term goal is to provide a development/staging platform to allow users to familerise themselves with the build system and allow them access to Koji outside of prodcution environments.   

Installation Prerequisites
---------------------------

If you opt for the virtual installation option the scripts will build a virtual machine which will be accessible from your local host.  Alternatively you can install directly on the local host if, for example, you have a dedicated server.  Kojak has been successfully installed and tested on CentOS 6.5 and Fedora 18+. 

For more information about virtualization see below:

CentOS http://wiki.centos.org/HowTos#head-fb1ff7e71fb5f2f511cda8c68cb6ba5f6e8decae 

Fedora http://fedoraproject.org/wiki/Virtualization?rd=Tools/Virtualization

It is recommended that the system be updated before beginning the installation.  A fast internet connection and is also required in order to facilitate the downloading of any package dependancies.

Minimum System Requirements
--------------------------- 

The virtual machine is configured with the following default specifications:

1. 4GB RAM
2. 32GB Disk Space

The you local host should be configured with the following minimum specifications:

1. Centos 6.5 or Fedora 18+ with virtualization package group
2. 8GB RAM
3. 120 GB Disk Space 

Installation Instructions
------------------------

1.  Checkout the contents of the Kojak git repository to a suitable directory on your local host e.g /home/user/workspace).
2.  As root execute kojak script.  You will be prompted about the type of installation you want to conduct.  If you choose to install Koji as a virtual machine you will be further prompted to supply some configuration options or simply accept the default options. 
3.  Once the installation is complete you should confirm that you can access the kojihub.  From the command line,
    as the koji user, execute the following:  

```
    [koji@koji ~]$ koji hello
    hi, kojiadmin!

    You are using the hub at http://koji.localdomain/kojihub
```

If the command executed successfully then your ready to begin creating a tag base for your builds and start building.  For a demo tag base you can simply execute Kojak again and select option number 4 (Create Tags) from the main menu.  You can also edit the create-tags file to create a custom tag set for your build.

See https://fedoraproject.org/wiki/Koji for more details about using Koji.

Configuration Notes
-------------------

The Kojak virtual machine is configured with a set of default options.  Executing the kojak script will allow you to modify and save these variables as required.  Installation directories, iso location and virtual machine resources allocations (Mem, CPU and Storage etc) can all be reconfigured as required.  The appliance is configured with with a static address taken from the pool of ip addresses from the "default" network that is configured with libvirt.

You can access the virtual machine via ssh at 192.168.122.2 using the following credentials:

1. username: root
2. password: root

Currently Kojak uses SSL certificates as the preferred method of authentication.  To utilize the client certificate for browser based logins you will need to import the certificate.  The certificate is can be accessed from /home/koji/.koji.  Certificates are created for a default set of users which includes koji, kojiadmin, kojira and 3 kojibuilders.

Known Issues
------------

See http://github.com/sbadakhc/kojak/issues?state=open
