drone
========

This role installs drone if it isn't already installed. This doesn't perform any extra configuration.

[![Build Status](https://drone-opsdev.rax.io/github.com/rack-roles/drone/status.svg?branch=master)](https://drone-opsdev.rax.io/github.com/rack-roles/drone)

Requirements
------------

This role requires Ubuntu 14.04 and docker.

Role Variables
--------------

### Upgrades

Drone does not currently offer an apt repository, to upgrade to a new verison supply `--extra-vars upgrade_drone=true` with your `ansible-playbook` run.

### Restoring

* `drone_mysql_backup` Set this variable to the file that contains a database dump, and the role will copy it to the remote server and attempt an import.

### Daemon

* `drone_hostname` Hostname that drone will be accessed on. Default hostname defined in inventory or "ansible\_ssh\_host"
* `drone_port` Port for drone to listen on.
* `drone_scheme` http or https (https requires `drone_sslcert` and `drone_sslkey` and probably `drone_port` configured for `443`)
* `drone_sslcert_location` Path to SSL certificate on the server.
* `drone_sslkey_location` Path to SSL key on the server.
* `drone_sslcert` Variable containing your SSL certificate.
* `drone_sslkey` Variable containing your SSL key.

### Datasource

* `drone_driver` Driver to use for data and configuration storage. Defaults to sqlite3.
* `drone_datasource` The datasource controls the sqllite file name or mysql database connection. Defaults to drone.sqlite.
* `drone_mysql_user` The mysql user to use. Defaults to drone.
* `drone_mysql_pass` Defaults to 'changeme123'
* `drone_mysql_host` Defaults to 'localhost'
* `drone_mysql_port` Defaults to '3306'
* `drone_mysql_dbname` Defaults to 'drone_io'

**Note** The MySQL options only apply if the driver is set to `mysql`

### Note

Not all configuration options found in the database are used by drone at this time, or properly configurable by this role.

Dependencies
------------

`Rackspace_Automation.docker`
`Rackspace_Automation.mysql`

Example Playbook
-------------------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```
    - hosts: servers
      roles:
         - { role: Rackspace_Automation.drone, install_drone: True }
```

License
-------

BSD

Author Information
------------------

This role is inspired by [sivel.drone](https://github.com/sivel/ansible-drone)

[Rackspace - the open cloud company](http://rackspace.com)

Ask about our DevOps Automation Service - [www.rackspace.com/devops](http://rackspace.com/devops)
