# Ansible Role: Pip (for Python)

[![Build Status](https://travis-ci.org/geerlingguy/ansible-role-pip.svg?branch=master)](https://travis-ci.org/geerlingguy/ansible-role-pip)

An Ansible Role that installs [Pip](https://pip.pypa.io) on Linux.

## Requirements

On RedHat/CentOS, you may need to have EPEL installed before running this role. You can use the `geerlingguy.repo-epel` role if you need a simple way to ensure it's installed.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    pip_package: python-pip

The name of the package to install to get `pip` on the system. You can set to `python3-pip`, for example, when using Python 3 on Ubuntu.

    pip_install_packages: []

The state of the `pip_package`: `present`, `absent` or `latest`. For additional [details](https://docs.ansible.com/ansible/latest/modules/package_module.html).

    pip_state: present

A list of packages to install with pip. Examples below:

    pip_install_packages:
      # Specify names and versions.
      - name: docker
        version: "1.2.3"
      - name: awscli
        version: "1.11.91"

      # Or specify bare packages to get the latest release.
      - docker
      - awscli

      # Or uninstall a package.
      - name: docker
        state: absent

      # Or update a package ot the latest version.
      - name: docker
        state: latest

      # Or force a reinstall.
      - name: docker
        state: forcereinstall

      # Or install a package in a particular virtualenv.
      - name: docker
        virtualenv: /my_app/venv

      # Or upgrade the package to the latest version, in a particular virtualenv.
      - name: docker
        virtualenv: /my_app/venv
        extra_args: '--upgrade'

      # Or use an specific pip version.
      - name: docker
        executable: pip3.4

## Dependencies

None.

## Example Playbook

    - hosts: all

      vars:
        pip_install_packages:
          - name: docker
          - name: awscli

      roles:
        - geerlingguy.pip

## License

MIT / BSD

## Author Information

This role was created in 2017 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
