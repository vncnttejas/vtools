# vtools

**vtools** stands for vincent tools is a Docker based tool for installing applications quickly and not worry about the implementation or installation steps of these software.

**vtools** creates an isolated sandbox environment for running your software.
In this context ***Software*** can be a database or some software service (like minio) which is a dependency for your application to run.

# Prerequisite
  - Python version 2*
  - latest version of Docker installed on your machine.
  - Does not require the knowledge of Python or Docker for using it.

# Installation
  - Install pip if you don't have already have it.
  - Clone the repo to you root folder
    ```
    cd ~
    git clone https://github.com/vncnttejas/vtools
    ```
  - Install `scriptine` with pip with the command
    `python2 -m pip install scriptine`
  - Add the bin path to your env variables
    `vim .profile #this could also be .bashrc or .zshrc`
    and add the line `alias dapp=$HOME/vtools/bin/dapp` to the end of the file.
    

# Commands
`dapp` is the only command the tool provides, at the moment, short for "desktop app".

`dapps start mongo`
will install(if the docker container for mongo is not already available) and start the mongodb service on your machine.
Currently there are configurations for 5 widely used softwares. However you will be able to add your own configuration.
Creating a config file is simple task, however requires a very basic understanding of Docker Compose file creation. If however you are not aware of Docker Compose configurartions, I will the documentation for it, in the next update to the documentation.

`dapp stop <service-name>` will stop the service if it is already started, else will be ignored.

## Pros
- Creates a sandbox environment to execute your software hence your OS filesystem and registry is not polluted with unwaned files and entries.
- You will be able to update the software configurations easily unlike bare-metal installation due to the declarative syntax of the configurations. For eg: You can update the password of the mongo by just setting the password variable to some value in the mongo.yaml file under manifests folder.
- Installation and Setting up service is a piece of cake
    -  `dapp start mongo` will install and set-up the mongodb service similarly `dapp start mysql` will install and start mysql service.

## Cons
- Since the software binaries are inside the Docker container, if you want execute the binary of the software you may have to use `docker exec` command.
