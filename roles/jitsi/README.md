Jitsi
=========
Install a running Jitsi server (jitsi-meet, jitsi-videobridge, etc.).

Supported platforms:
- Debian


Requirements
------------


Role Variables
--------------

```
jitsi:
    # [required] install jitsi for this domain
    domain: ''
    # sign certificates with letsencrypt
    cert: true
```

Note: setup for Debian only requires `jitsi.domain`.

Dependencies
------------

Example Playbook
----------------

License
-------

BSD

Author Information
------------------

bkfox

