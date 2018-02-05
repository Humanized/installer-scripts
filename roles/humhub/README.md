Role Name
=========

Install Humhub.

Requirements
------------
LAMP server


Role Variables
--------------

```yaml
# humhub params
humhub:
    # server domain to use
    domain: ""
    # `lamp.http.server`
    http_server: nginx
    # `lamp.sql.server`
    sql_server: mariadb

    # optional: get sources an HumHub bundle
    bundle:
        # required for bundle: humhub version
        version: ''
        # optional: use this source instead of official one
        src: ''
        # optional: `lamp.http.archive.force`
        force: ''
        # remote

    # download/sync from the given repository
    git:
        # required: use this repository or official repo (if true)
        repo: ''
        # `lamp.http.git.pull`
        pull: false

    # database settings
    db:
        # use this database server
        server: mariadb
        # database password to use
        password:

```


Dependencies
------------

`Humanized.lamp`

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
