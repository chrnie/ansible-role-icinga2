# ansible-role-icinga2_install
install icinga2 on rhel or debian

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    icinga2_manage_repo_icinga: true

`True` for icinga2 community repos, `False` for distro packages


    icinga2_manage_repo_epel: true

`True` to ensure epel-release rpm is installed.


## Dependencies


## Example Playbook
You can find an example playbook for testing purposes on https://github.com/chrnie/icinga2-vagrant-ansible

    - hosts: all
      roles:
        - chrnie.icinga2_install


## License

Apache License 2.0

## Author Information

Created in 2017 by Christoph Niemann, https://github.com/chrnie
Forked from https://github.com/mkayontour/icinga2-ansible/roles/common
