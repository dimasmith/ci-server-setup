CI Server
========

Automated setup for CI server to use with java projects

## Software that will be set up:

* Jenkins

## Roles

The set of reusable ansible roles is combined to set up CI server.

The playbook install products as Docker containers.
It creates `ci` user to group all CI related service under the hood.
Volume directories are available under `ci` user home folder.

The playbook uses two common Ansible roles to set up the server.  
The `docker` role sets up repositories and installs the latest version of the Docker engine and helper scripts.
The `user` role creates `ci` user.
It also adds `ci` user to "docker" group so the user can manipulate images and containers.

The `jenkins` role downloads and starts an instance of Jenkins build server.
Volume data of the server mapped into `jenkins` subdirectory of `ci` user home folder.
There is a known issue with owning data in the mounted volume.
The Jenkins container should be run as `jenkins` user to set up rights.
The role works around this issue by creating a user and passing a directory ownership to it.
It also starts the container providing UID of added user.
You can change UID by setting `jenkins.user.uid` variable.
