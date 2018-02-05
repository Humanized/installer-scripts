LAMP
=========

Install LAMP solution for a particular host.

Supported services:
- http server: nginx
- php
- db: mysql, mariadb

Supported platforms:
- Debian

Role Variables
--------------

```yaml
# server domain
# used for: website root, db name, db user
domain: ""

# setup site
http:
    server: nginx
    # symlink site config into sites-enabled
    enabled: true
    # use this template file
    template: ''

# setup php
php:
    # modules names to enable
    modules: ['']

# setup sql server
sql:
    # sql database: mariadb, mysql
    server: mariadb
    # created user password
    password: ''
    # mysql_db/mysql_user config_file
    config_file: ''
    # mysql_db.collation
    collation: ''
    # mysql_db.encoding
    encoding: ''
```


Setup/Install site files:

```
# extract site files from this archive source. If the directory
# exists yet, it wont do it (except if `force` is true)
bundle:
    # `unarchive.src`; must be defined to enable the feature
    src: ''
    # force archive extraction in target dir
    force: false
    # unarchive.remote_src
    remote_src: false|true
    # extract file from this archive subdir
    strip: ''

# extract site files from this git repository
# clone will fails if there is yet files in this
# repos
git:
    # git.repo
    repo: ''
    # git.update
    pull: false|true
    # git.force
    force: false|true
```

Dependencies
------------

TODO/FIXME
----------
- tasks/bundle.yml: cleanup files in `archive_dest` when strip is done
- tasks/git.yml: force argument -- not similar to bundle's; need coherence


Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: nginx, server: { domain: bkfox.net } }

License
-------
BSD

Author Information
------------------
By bkfox for humanized.

