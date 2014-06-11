vagrant_ansible_dev
===================

A configurable simple dev box running ubuntu 14.04 + php5.5 + nginx1.4.6 + mysql5.5.

Requirements
============

- vagrant 1.6+ (https://www.vagrantup.com/downloads.html)
- virtualbox (https://www.virtualbox.org/wiki/Downloads)
- ansible 1.6+ (http://docs.ansible.com/intro_installation.html#installing-the-control-machine)

Packages Installed
==================

Installed via ansible roles:

- mysql-server
- python-mysqldb *(required by ansible)*
- nodejs
- npm
- composer
- nginx
- php5-fpm
- php5-cli

The default configuration also installs:

- git
- beanstalkd
- supervisor
- php5-sqlite 
- php5-mcrypt
- php5-mysql
- php5-sqlite
- php5-xdebug
- grunt-cli
- bower

Usage
=====

Copy *local.yml.dist* to *local.yml*.

Change settings to suit. 

- **project_root** - A top level directory under which vhost/s will be mounted from your host filesystem.
- **projects** - Configure a single (or multiple) web projects. If configuration of the vhost is needed then specify a name for the config file and place it in the *ansible/roles/web/templates/vhosts* folder.

The path to a project is defined by the *project_root* + *docroot*.

Insert entries in your host file mapping the project names to the *vm_ip_address*.

Finally
=======

```
vagrant up
```