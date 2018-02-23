vhost
=====

Install LAMP solution for a particular host.

Features:
- http server:
    - supports: nginx
    - letsencrypt setup
    - server file installation through: git, unarchive (bundle)
- php:
    - setup for virtual hosts;
    - modules install from system package manager;
- database:
    - supports: mysql, mariadb

Supported platforms:
- Debian

Role Variables
--------------

```yaml
vhost:
    # server domain
    # used for: website root, db name, db user
    domain: ""
    # admin contact mail; used for certificates
    admin_email:
    # generate server certificates using certbot
    # and configure http server to use it.
    cert: true

    # setup site
    http:
        server: nginx
        # listen to this port (default: 443 when ssl, otherwise 80)
        # if set, only listen to this port.
        port: null
        # root directory
        root: '{{ domain }}'
        # symlink site config into sites-enabled
        enabled: true
        # enable php in configuration. If enabled, `index.php` will be a
        # valid index file, prior to html ones.
        php: false|true,
        # configuration file template
        template: 'templates/nginx.j2',
        # in default config, include this file in virtual host configuration
        config_extra: '',

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

    #
    # install files on the http server
    #

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

