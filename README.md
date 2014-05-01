Role Name
========

This role installs drone if it isn't already installed. This doesn't perform any extra configuration.

[![Build Status](http://drone.onitato.com/github.com/rack-roles/drone/status.svg?branch=master)](http://drone.onitato.com/github.com/rack-roles/drone)

Requirements
------------

This role requires Ubuntu 14.04 and docker.

Role Variables
--------------

* `drone_scheme`: http
* `drone_hostname`
* `drone_port`: 80
* `drone_sslcert`
* `drone_sslkey`
* `drone_path`

You can explicitly force drone to update by setting the variable `install_drone=True`. Otherwise, it checks to see if drone is installed before attempting to install it again.

Dependencies
------------

`Rackspace_Automation.docker`

Example Playbook
-------------------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: Rackspace_Automation.drone, install_drone: True }

License
-------

BSD

Author Information
------------------

[Rackspace - the open cloud company](http://rackspace.com)

Ask about our DevOps Automation Service - [www.rackspace.com/devops](http://rackspace.com/devops)
