rsyslog
=========

<img src="https://docs.ansible.com/ansible-tower/3.2.4/html_ja/installandreference/_static/images/logo_invert.png" width="10%" height="10%" alt="Ansible logo" align="right"/>
<a href="https://travis-ci.org/robertdebock/ansible-role-rsyslog"><img src="https://travis-ci.org/robertdebock/ansible-role-rsyslog.svg?branch=master" alt="Build status" align="left"/></a>

Install and configure rsyslog on your system.

<img src="https://img.shields.io/ansible/role/d/22988"/>
<img src="https://img.shields.io/ansible/quality/22988"/>

Example Playbook
----------------

This example is taken from `molecule/resources/playbook.yml`:
```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - robertdebock.rsyslog
```

The machine you are running this on, may need to be prepared.
```yaml
---
- name: Prepare
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - robertdebock.bootstrap
```

Also see a [full explanation and example](https://robertdebock.nl/how-to-use-these-roles.html) on how to use these roles.

Role Variables
--------------

These variables are set in `defaults/main.yml`:
```yaml
---
# defaults file for rsyslog

# To configure a server to reveice logs, set rsyslog_receiver to yes.
# Not setting this value will not configure the server tor receive logs.
# rsyslog_receiver: yes

# To forward logs to another server, set rsyslog_remote to the hostname or
# the ipaddress of the receiving rsyslog server.
# Not setting this variable will not forward logs.
# rsyslog_remote: server1.example.com
```

Requirements
------------

- Access to a repository containing packages, likely on the internet.
- A recent version of Ansible. (Tests run on the current, previous and next release of Ansible.)

The following roles can be installed to ensure all requirements are met, using `ansible-galaxy install -r requirements.yml`:

```yaml
---
- robertdebock.bootstrap

```

This role uses the following modules:
```yaml
---
- file
- package
- service
- template
```

Context
-------

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/rsyslog.png "Dependency")


Compatibility
-------------

This role has been tested on these [container images](https://hub.docker.com/):

|container|allow_failures|
|---------|--------------|
|alpine:latest|no|
|alpine:edge|yes|
|robertdebock/docker-centos-systemd:7|no|
|robertdebock/docker-centos-systemd:latest|no|
|robertdebock/docker-debian-systemd:latest|no|
|robertdebock/docker-debian-systemd:stable|no|
|robertdebock/docker-debian-systemd:unstable|yes|
|robertdebock/docker-fedora-systemd:latest|no|
|robertdebock/docker-fedora-systemd:rawhide|yes|
|opensuse/leap|no|
|robertdebock/docker-ubuntu-systemd:latest|no|
|robertdebock/docker-ubuntu-systemd:devel|yes|
|robertdebock/docker-ubuntu-systemd:rolling|no|

This role has been tested on these Ansible versions:

- ansible~=2.7
- ansible~=2.8
- git+https://github.com/ansible/ansible.git@devel

The indicator '~=' means [compatible with](https://www.python.org/dev/peps/pep-0440/#compatible-release). For example 'ansible~=2.8' would pick the latest ansible-2.8, for example ansible-2.8.5.

Exceptions
----------

Some variarations of the build matrix do not work. These are the variations and reasons why the build won't work:

| variation                 | reason                 |
|---------------------------|------------------------|
| archlinux/base | target not found: rsyslog |



Testing
-------

[Unit tests](https://travis-ci.org/robertdebock/ansible-role-rsyslog) are done on every commit and periodically.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-rsyslog/issues)

To test this role locally please use [Molecule](https://github.com/ansible/molecule):
```
pip install molecule
molecule test
```

To test on Amazon EC2, configure [~/.aws/credentials](https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/credentials.html) and set a region using `export AWS_REGION=eu-central-1` before running `molecule test --scenario-name ec2`.

There are many specific scenarios available, please have a look in the `molecule/` directory.

License
-------

Apache-2.0


Author Information
------------------

[Robert de Bock](https://robertdebock.nl/)
