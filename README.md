[![Build
Status](https://travis-ci.com/nkakouros-original/ansible-role-easyrsa.svg?branch=master)](https://travis-ci.com/nkakouros-original/ansible-role-easyrsa)
[![Galaxy](https://img.shields.io/badge/galaxy-nkakouros.easyrsa-blue.svg)](https://galaxy.ansible.com/nkakouros/easyrsa/)

Ansible Role: EasyRSA
=========

Installs EasyRSA 3 and generates certificates and keys.

Requirements
------------

- Ansible >= 2.8 (might work with other versions too)

- The role is being tested against Ubuntu 18.04 but it should work with any other
Linux distro as well.

- `git` should be already installed.

- This role needs to be run with `become: true`, i.e. it assumes it runs as the
  root user.

Role Variables
--------------

See [defaults/main.yml](defaults/main.yml) for a full list of variables together
with documentation on how to use them to configure this role.

For more info on the different key formats that easyrsa can generate, take
a look at [key-formats.md](key-formats.md).

When the role runs, `easyrsa_role_run` (a variable set internally by the role)
is set to true. If `easyrsa_enabled` is set to `false`, the role does not run
and `easyrsa_role_run` will be set to `false`.

Example Playbook
----------------

See [molecule/default/playbook.yml](molecule/default/playbook.yml) and
[molecule/default/side_effect.yml](molecule/default/side_effect.yml) for
working examples of how to use this role

License
-------

GPLv3

Author Information
------------------

Nikolaos Kakouros
