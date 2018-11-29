# ansible-role-icinga2

[![Build Status](https://travis-ci.org/chrnie/ansible-role-icinga2.svg?branch=master)](https://travis-ci.org/chrnie/ansible-role-icinga2)

Install icinga2 on rhel or debian. Configure agent or master mode and control icinga2 features.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

### icinga2 settings

    icinga2_role: agent

Choose a role for icinga2. `agent` or `master` is possible.

    icinga2_ca_host: false

Without a icinga2 server's fqdn this module will fail

    icinga2_features: [ "checker", "api", "mainlog" ]

All features in this array will be enabled

    icinga2_state: present

Update or not? `icinga2_state` can be installed,latest,removed,absent,present,build-dep

### Manage package repos

    icinga2_manage_repo_icinga: true

`True` for icinga2 community repos, `False` for distro packages

    icinga2_manage_repo_epel: true

`True` to ensure epel-release rpm is installed.


### includes geerlingguy.mysql

    icinga2_manage_mysql: false

If you choose `true` this module will install and configure mysql

### ido vars

    icinga2_ido_user: icinga
    icinga2_ido_password: icinga
    icinga2_ido_dbname: icinga
    icinga2_ido_host: "127.0.0.1"
    icinga2_ido_port: 3306

IDO connection options

### All other features

    ic2_f_debuglog_options:
      severity: "\"debug\""
      path: "LocalStateDir + \"/log/icinga2/debug.log\""

There is a variable for each feature If you want to change a value, you have to configure all attributes of that feature. All other features work in a similar way.


## Dependencies


## Example Playbook
You can find an example playbook for testing purposes on https://github.com/chrnie/icinga2-vagrant-ansible.

    - hosts: all
      roles:
        - chrnie.icinga2

Tags are supported:
  - ansible-playbook --tags foo --skip-tags bar
  - valid tags: config feature feature_switch install update
  - caused by [ansible issue #32015](https://github.com/ansible/ansible/issues/32015) we have to use the untagged tag.
    - if you only want to update icinga2 on icinga2_master
      - `$ ansible-playbook -i hosts/testing 003_icinga2.yml --tags update,untagged --limit icinga2_master --extra-vars "icinga2_state=latest"`
    - if you want to enable/disabled configured features on all nodes
      - `$ ansible-playbook -i hosts/testing 003_icinga2.yml --tags feature_switch,untagged`

## License

Apache License 2.0

## Author Information

Created in 2017 by Christoph Niemann, https://github.com/chrnie

Forked from https://github.com/mkayontour/icinga2-ansible+

