Role Name
========

This role installs drone if it isn't already installed. This doesn't perform any extra configuration.

[![Build Status](http://drone.onitato.com/github.com/rack-roles/drone/status.svg?branch=master)](http://drone.onitato.com/github.com/rack-roles/drone)

Requirements
------------

This role requires Ubuntu 14.04 and docker.

Role Variables
--------------

### Upgrades

Drone does not currently offer an apt repository, to upgrade to a new verison supply `--extra-vars upgrade_drone=true` with your `ansible-playbook` run.

### drone\_users

`drone_users` is a list of hashes, each hash containing the following:

* `name` Persons name
* `email` Persons email
* `password` bcrypt password hash (optional, you will have to use forgot password to set a password)
* `admin` True/False (boolean). Default `False`.
* `state` present/absent. Default `present`
* `update_password` True/False (boolean). Default `False`. Setting as True will ensure the specified password.

#### bcrypt password hash

1. Install `bcrypt` python module
1. `python -c "import bcrypt; print bcrypt.hashpw('<password>', bcrypt.gensalt());"`

### Email

* `drone_smtp_server` SMTP server address
* `drone_smtp_port` SMTP server port
* `drone_smtp_address` EMail address to send from
* `drone_smtp_username` SMTP authenticaiton username
* `drone_smtp_password` SMTP authentication password

### GitHub

* `drone_github_key` GitHub application key
* `drone_github_secret` GitHub application secret.
* `drone_github_domain` GitHub domain. Default `github.com`
* `drone_github_apiurl` GitHub API url. Default `https://api.github.com`

### Daemon

* `drone_hostname` Hostname that drone will be accessed on. Default hostname defined in inventory or "ansible\_ssh\_host"
* `drone_port` Port for drone to listen on
* `drone_scheme` http or https (https requires `drone_sslcert` and `drone_sslkey` and probably `drone_port` configured for `443`)
* `drone_sslcert_location` Path to SSL certificate on the server.
* `drone_sslkey_location` Path to SSL key on the server.
* `drone_sslcert_file` Path to SSL certificate from your playbook.
* `drone_sslkey_file` Path to SSL key from your playbook.

### Datasource

* `drone_driver` Driver to use for data and configuration storage. Defaults to sqlite3.
* `drone_datasource` The datasource controls the sqllite file name or mysql database connection. Defaults to drone.sqlite.
* `drone_mysql_user` The mysql user to use. Defaults to drone.
* `drone_mysql_pass` Defaults to 'changeme123'
* `drone_mysql_host` Defaults to 'localhost'
* `drone_mysql_port` Defaults to '3306'
* `drone_mysql_dbname` Defaults to 'drone_io'

**Note** The MySQL options only apply if the driver is set to `mysql`

### Other

* `drone_open_invitations` True/False (boolean). Whether open sign up is enabled. Default `False`.


### Note

Not all configuration options found in the database are used by drone at this time, or properly configurable by this role.

Dependencies
------------

`Rackspace_Automation.docker`

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
