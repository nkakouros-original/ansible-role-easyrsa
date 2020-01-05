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

Role Variables
--------------

See [defaults/main.yml](defaults/main.yml) for a full list of variables together
with documentation on how to use them to configure this role.

For more info on the different key formats that easyrsa can generate, take
a look at [key-formats.md](key-formats.md).

Example Playbook
----------------

See [molecule/default/playbook.yml](molecule/default/playbook.yml) for a working
example of how to use this role

License
-------

GPLv3

Author Information
------------------

Nikolaos Kakouros
