CI Server
========

Automated setup for CI server to use with java projects.

## Software that can be set up:

* [Jenkins](https://jenkins.io/)
* [Nexus](https://www.sonatype.com/nexus-repository-oss)
* [Nginx](https://www.nginx.com/resources/wiki/)
* [SonarQube](https://www.sonarqube.org/)

## Setting up

Software is set up via [Ansible](https://www.ansible.com/).

Copy or modify example playbook to set up your server.
Provide an inventory file for the playbook.
Provision environment using Ansible.

### Customization

#### Domains
Domains are used by gateway to proxy requests to services.
Variables to set up domains:
* `jenkins_domain` for jenkins;
* `nexus_domain` for nexus;
* `sonar_domain` for sonar;

#### Service ports
It is possible to customize network ports for services by setting:
* `jenins_port` for jenkins;
* `nexus_port` for nexus;
* `sonar_port` for sonar;

#### Service versions
Service versions can be changes by setting variables:
* `jenkins_version`;
* `nexus_version`;
* `sonar_version`;

Those settings can be customized when including role.
If, for example, you want to run jenkins on 8888 port on `build.example.com` domain
create playbook like that:
```yml
roles
  - { role: gateway, jenkins_domain: "build.example.com" }
  - { role: jenkins, jenkins_port: 8888 }
  - nexus
```

### Evaluate locally

The Vagrantfile is included to populate your server locally.
It is advised to evaluate installation using vagrant before provisioning servers.

The `example.yml` playbook populates local environment.
Vagrant launches machine in private network using `192.168.1.10` address.
By default gateway is set up to resolve `jenkins.ci` and `nexus.ci` domains
to respective services.

You may use dnsmasq to set up local development domain to test installation.

## Software

### SonarQube
Sonar is installed together with MySQL database.
