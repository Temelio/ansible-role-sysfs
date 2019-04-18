# sysfs

[![License](https://img.shields.io/badge/license-MIT%20License-brightgreen.svg)](https://opensource.org/licenses/MIT)
[![Build Status](https://img.shields.io/travis/Temelio/ansible-role-sysfs/master.svg?label=travis_master)](https://travis-ci.com/Temelio/ansible-role-sysfs)
[![Build Status](https://img.shields.io/travis/Temelio/ansible-role-sysfs/develop.svg?label=travis_develop)](https://travis-ci.com/Temelio/ansible-role-sysfs)
[![Updates](https://pyup.io/repos/github/Temelio/ansible-role-sysfs/shield.svg)](https://pyup.io/repos/github/Temelio/ansible-role-sysfs/)
[![Python 3](https://pyup.io/repos/github/Temelio/ansible-role-sysfs/python-3-shield.svg)](https://pyup.io/repos/github/Temelio/ansible-role-sysfs/)
[![Ansible Role](https://img.shields.io/ansible/role/39668.svg)](https://galaxy.ansible.com/Temelio/sysfs/)
[![GitHub tag](https://img.shields.io/github/tag/temelio/ansible-role-sysfs.svg)](https://github.com/Temelio/ansible-role-sysfs/tags)

Install sysfs package.

## Requirements

This role requires Ansible 2.4 or higher,
and platform requirements are listed in the metadata file.

## Testing

This role use [Molecule](https://github.com/metacloud/molecule/) to run tests.

Local and Travis tests run tests on Docker by default.
See molecule documentation to use other backend.

Currently, tests are done on:
- Debian Stretch
- Ubuntu Trusty
- Ubuntu Xenial
- Ubuntu Bionic

and use:
- Ansible 2.4.x
- Ansible 2.5.x
- Ansible 2.6.x
- Ansible 2.7.x

### Running tests

#### Using Docker driver

```
$ tox
```

## Role Variables

### Default role variables

``` yaml
# Package management
sysfs_packages: "{{ _sysfs_packages | default([]) }}"

# Service management
sysfs_service_file_path: "{{ _sysfs_service_file_path | default('') }}"
sysfs_service_name: "{{ _sysfs_service_name | default('') }}"
sysfs_service_enabled: True

# Configuration management
sysfs_config: "{{ _sysfs_config }}"
sysfs_dependent_services: []
sysfs_rules: []
```

### Debian OS family variables

``` yaml
# System prerequisites
_sysfs_packages:
  - name: 'sysfsutils'

# Service management
_sysfs_service_name: 'sysfsutils'
_sysfs_service_file_path: '/etc/init.d/sysfsutils'

# Configuration management
_sysfs_config:
  files: {}
  folder:
    path: '/etc/sysfs.d'
```

## Dependencies

None

## Example Playbook

``` yaml
- hosts: servers
  roles:
    - { role: temelio.sysfs }
```

## License

MIT

## Author Information

L Machetel (for Temelio Company)
Fork from: Alexandre Chaussier (for Infopen company)
