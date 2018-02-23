Onlyoffice
=========

Install and setup onlyoffice instance.

Requirements
------------

vhost

Role Variables
--------------

```
onlyoffice:
    domain: ""

    db:
        # database password
        password: ""

    # vhost.http
    http:
        # set vhost.http settings here
        port: 1312

    # vhost overwrite conf
    vhost:
        # whatever
```


Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
