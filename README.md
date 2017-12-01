# ansible-role-icinga2

[![Build Status](https://travis-ci.org/chrnie/ansible-role-icinga2.svg?branch=master)](https://travis-ci.org/chrnie/ansible-role-icinga2)

Install icinga2 on rhel or debian. Configure agent or master mode and control icinga2 features. 

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

### icinga2 settings

    icinga2_role: agent

Choose a role for icinga2. `agent` or `master` is possible.

    icinga2_master_fqdn: false

Without a icinga2 server's fqdn this module will fail

    icinga2_features: [ "checker", "api", "mainlog" ]

All features in this array will be enabled
### Manage package repos

    icinga2_manage_repo_icinga: true

`True` for icinga2 community repos, `False` for distro packages


    icinga2_manage_repo_epel: true

`True` to ensure epel-release rpm is installed.

### includes geerlingguy.mysql

    icinga2_manage_mysql: false

If you choose `true` this module will install and configure mysql

### ido-mysql vars

    mysql_root_password: super-secure-password
    icinga2_feature_ido_user: icinga
    icinga2_feature_ido_password: icinga
    icinga2_feature_ido_dbname: icinga
    icinga2_feature_ido_host: "127.0.0.1"
    icinga2_feature_ido_port: 3306

IDO connection options


## Dependencies


## Example Playbook
You can find an example playbook for testing purposes on https://github.com/chrnie/icinga2-vagrant-ansible

    - hosts: all
      roles:
        - chrnie.icinga2


## License

Apache License 2.0

## Author Information

Created in 2017 by Christoph Niemann, https://github.com/chrnie

Forked from https://github.com/mkayontour/icinga2-ansible/roles/common
