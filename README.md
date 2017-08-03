# grafana_ansible

## Description

[![Ansible Galaxy](https://img.shields.io/badge/galaxy-sbouii.grafana_ansible-blue.svg)](https://galaxy.ansible.com/sbouii/grafana_ansible/) 
[![Build Status](https://travis-ci.org/sbouii/grafana_ansible.svg?branch=master)](https://travis-ci.org/sbouii/grafana_ansible)


This is an ansible role for installing Grafana on Debian and RedHat distributions , it doesn't handle the configuration aspect of 
Grafana . I prefer always to separe the installation and the configuration/monitoring aspect of a software for organizing  purposes.It uses the infrastructure testing tool **[KitchenCi](http://kitchen.ci/)** to verify if the infrastructure is well setup and configured as expected.

## Requirements

### Software Requirements

- **Python 2.7** or higher

- **Ansible 2.0** or higher (can be easily installed via pip. E.g: sudo pip install ansible==2.0.0.2)

- **[Vagrant](https://www.vagrantup.com/) 1.7** or higher 

- **Virtualbox**

## Supported Systems

- Debian
- Ubuntu
- Centos

More infos in the role's metadata file.


### Dependencies

None.

## Role variables
Available variables are listed below, see defaults/main.yml for the default values:

- **`debian_grafana_repositoy_filename`** - the filename of the kubernetes debian repository 
- **`redhat_grafana_repositoy_name`** - a unique kubernetes redhat repository ID
- **`redhat_grafana_repositoy_description`** - a description for the kubernetes redhat repository
- **`grafana_port`** - grafana server port
- **`grafana_user`** - 
- **`grafana_group`** - grafana server port
- **`grafana_home`** - grafana server port
- **`grafana_log_directory`** - grafana server port
- **`grafana_data_directory`** - grafana server port
- **`grafana_max_open_files`** - grafana server port
- **`grafana_conf_directory`** - grafana server port
- **`grafana_conf_file`** - grafana server port
- **`grafana_directory_plugin`** - grafana server port
```
- grafana_init_changes:
  - option: "GRAFANA_USER"
    value: "{{ grafana_user }}"
  - option: "GRAFANA_GROUP"
    value: "{{ grafana_group }}"
  - option: "GRAFANA_HOME"
    value:  "{{ grafana_home }}"
  - option: "LOG_DIR"
    value: "{{ grafana_log_directory }}"
  - option: "DATA_DIR"
    value: "{{ grafana_data_directory }}"
  - option: "MAX_OPEN_FILES"
    value: "{{ grafana_max_open_files }}"
  - option: "CONF_DIR"
    value: "{{ grafana_conf_directory }}"
  - option: "CONF_FILE"
    value: "{{ grafana_conf_file }}"
  - option: "RESTART_ON_UPGRADE"
    value: "true"
  - option: "PLUGINS_DIR"
    value: "{{ grafana_directory_plugin }}"
```
## Available tags

- **`install-grafana`** -  Default tag to perform grafana installation

## Usage

In order to set up a grafana server across your plateform, start by checking out the role from Ansible galaxy:
```bash
ansible-galaxy install sbouii.grafana_ansible
```

Finally call the role within you Ansible playbook:
```yaml
---
- hosts: localhost
  sudo: yes
  roles:
    - grafana_ansible
```
## Development and Testing
### Test with Vagrant
For quick tests, you can spin up a Debian VM using Vagrant. You maybe need to adapt the Vagrantfile to suit your environment (IP addresses, etc).

    $ vagrant up

### Run acceptance tests

For runing Acceptance/Integration tests against your role , we use the tool `test-kitchen`.All written acceptance tests are in the **./test/integration/** directory.

The `.kitchen.yml` file describes the testing configuration and the list of suite tests to run. By default, the instances will be converged with Ansible and ran in Vagrant virtual machines.

To list the instances:

    $ kitchen list

    Instance                    Driver   Provisioner      Verifier  Transport  Last Action
    default-debian-8-x64        Vagrant  AnsiblePlaybook  Busser    Ssh        <Not Created>
    ...

To run the default test suite, for instance, on a Ubuntu Trusty platform, run the following command:

    $ kitchen test default-ubuntu-1404-x64

## Author information

This role was created by [Mariem Sbouii](https://www.linkedin.com/in/mariem-sboui-76906711b) ,a DevOps enthusiast.

