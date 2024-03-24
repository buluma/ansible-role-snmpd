# Ansible role [snmpd](https://galaxy.ansible.com/ui/standalone/roles/buluma/snmpd/documentation)

Install and configure snmpd on your system.

|GitHub|Version|Issues|Pull Requests|Downloads|
|------|-------|------|-------------|---------|
|[![github](https://github.com/buluma/ansible-role-snmpd/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-snmpd/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-snmpd.svg)](https://github.com/buluma/ansible-role-snmpd/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-snmpd.svg)](https://github.com/buluma/ansible-role-snmpd/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-snmpd.svg)](https://github.com/buluma/ansible-role-snmpd/pulls/)|[![Ansible Role](https://img.shields.io/ansible/role/d/buluma/snmpd)](https://galaxy.ansible.com/ui/standalone/roles/buluma/snmpd/documentation)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-snmpd/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - role: buluma.snmpd
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-snmpd/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: prepare
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - role: buluma.bootstrap
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-snmpd/blob/master/defaults/main.yml):

```yaml
---
# defaults file for snmpd

snmpd_security_names:
  - name: notConfigUser
    source: default
    community: public

snmpd_groups:
  - name: notConfigGroup
    security_model: v1
    security_name: notConfigUser
  - name: NotConfigGroup
    security_model: v2c
    security_name: NotConfigUser

snmpd_views:
  - name: systemview
    type: included
    subtree: ".1.3.6.1.2.1.1"
  - name: systemview
    type: included
    subtree: ".1.3.6.1.2.1.25.1.1"

snmpd_accesses:
  - group: notConfigGroup
    context: ""
    security_model: any
    security_level: noauth
    prefix: exact
    read: systemview
    write: none
    notif: none

snmpd_syslocation: Unknown
snmpd_syscontact: Root <root@localhost>

snmpd_dontlogtcpwrappersconnects: "yes"

# snmpd_processes:
#   - name: mountd
#   - name: ntalkd
#     maximum: 4
#   - name: sendmail
#     minimum: 1
#     maximum: 10
#
# snmpd_scripts:
#   - name: shelltest
#     program: /bin/sh
#     arguments: /tmp/shtest

snmpd_disks:
  - path: /
    minimum: 10000

snmpd_load:
  one_minute_average: 12
  five_minute_average: 14
  fifteen_minute_average: 14
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-snmpd/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | Version |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Ansible Molecule](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-bootstrap.svg)](https://github.com/shadowwalker/ansible-role-bootstrap)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-snmpd/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[Alpine](https://hub.docker.com/r/buluma/alpine)|all|
|[Amazon](https://hub.docker.com/r/buluma/amazonlinux)|Candidate|
|[EL](https://hub.docker.com/r/buluma/enterpriselinux)|all|
|[Debian](https://hub.docker.com/r/buluma/debian)|all|
|[Fedora](https://hub.docker.com/r/buluma/fedora)|all|
|[opensuse](https://hub.docker.com/r/buluma/opensuse)|all|
|[Ubuntu](https://hub.docker.com/r/buluma/ubuntu)|all|

The minimum version of Ansible required is 2.12, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-snmpd/issues)

## [Changelog](#changelog)

[Role History](https://github.com/buluma/ansible-role-snmpd/blob/master/CHANGELOG.md)

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-snmpd/blob/master/LICENSE)

## [Author Information](#author-information)

[Shadow Walker](https://buluma.github.io/)

