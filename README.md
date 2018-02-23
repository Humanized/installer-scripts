# Installer Scripts
Ansible script to install services:
* vhost: LAMP solutions (nginx, mariadb/mysql, php...)
* humhub
* jitsi

Thoses are made as reusable roles and customizable. Look at their respective README files for more info about features and usage.


## playbook.yml
Install the various component using the roles available in this repo. Hosts are:
* `humhub`: install/setup Humhub instances. Variable are: `domain`, `admin_email`, `db_password`
* `jitsi`: install/setup Jitsi instances. Variables are: `domain`

Thoses can be instanciated from command-line:

```bash
# install/setup humhub
ansible-playbook humhub.yml --extra-vars "domain=humhub.example.com admin_email=contact@example.com db_password=secret"

# install/setup onlyoffice
ansible-playbook onlyoffice.yml --extra-vars "port=1312" --extra-vars "domain=debian.localdomain" --extra-vars "db_password=onlyoffice"

# install/setup jitsi
ansible-playbook jitsi.yml --extra-vars "domain=jitsi.example.com"
```

Note that this requires the inventory to be set up with thoses hosts such as:

```
[humhub]
machine.tls

[jitsi]
machine.tls
```


## TODO
- vhost: init sql db with one or more dump files
- vhost: certbot cron job
- humhub: defaults' http.config_extra => take configured http server in account
- Yii integration


