# Ansible Role: Pip (for Python)

[![Build Status](https://travis-ci.org/geerlingguy/ansible-role-pip.svg?branch=master)](https://travis-ci.org/geerlingguy/ansible-role-pip)

An Ansible Role that installs [Pip](https://pip.pypa.io) on Linux.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    pip_install_packages: []

A list of packages to install with pip. Examples below:

    pip_install_packages:
      # Specify names and versions.
      - name: docker-py
        version: "1.2.3"
      - name: awscli
        version: "1.11.91"
      # Or specify bare packages to get the latest release.
      - docker-py
      - awscli

## Dependencies

None.

## Example Playbook

    - hosts: all
      roles:
        - geerlingguy.pip

## License

MIT / BSD

## Author Information

This role was created in 2017 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
