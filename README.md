Ansible Role: mcrouter 
======================================

[![Build Status](https://travis-ci.org/entercloudsuite/ansible-mcrouter.svg?branch=master)](https://travis-ci.org/entercloudsuite/ansible-mcrouter)
[![Galaxy](https://img.shields.io/badge/galaxy-entercloudsuite.mcrouter-blue.svg?style=flat-square)](https://galaxy.ansible.com/entercloudsuite/mcrouter)  

Installs mcrouter on Ubuntu 16.04 (Xenial)

## Requirements

This role requires Ansible 2.4 or higher.

## Role Variables

The role defines most of its variables in `defaults/main.yml`:

## Example Playbook

```yaml
---
- name: run the main role
  hosts: all
  roles:
    - role: ansible-mcrouter
      mcrouter_address: localhost:11213
  become: yes
```



## Testing

Tests are performed using [Molecule](http://molecule.readthedocs.org/en/latest/).

Install Molecule or use `docker-compose run --rm molecule` to run a local Docker container, based on the [enterclousuite/molecule](https://hub.docker.com/r/fminzoni/molecule/) project, from where you can use `molecule`.

For this role is required a openstask account

and the expoter your environment variables like this

``` bash
export OS_AUTH_URL="https://myopenstaskprobvider.com/v2.0"
export OS_REGION_NAME="my-reagion"
export OS_TENANT_ID=tenantIDString (a lot of number)
export OS_TENANT_NAME="projectName"
export OS_USERNAME="projectName"
export OS_PASSWORD="v3ryS3cr3t"
export SWIFT_USERNAME=$OS_USERNAME
export SWIFT_TENANTNAME=$OS_TENANT_NAME
export SWIFT_PASSWORD=$OS_PASSWORD
export SWIFT_AUTHURL=$OS_AUTH_URL
export SWIFT_AUTHVERSION=2
export PASSPHRASE=$OS_TENANT_ID
export SWIFT_REGION=$OS_REGION_NAME
```

1. Run `molecule create` 
2. Use `molecule login` to log in to vm.  
3. Edit the role files.  
4. Add other required roles (external) in the molecule/default/requirements.yml file.  
5. Edit the molecule/default/playbook.yml.  
6. Define infra tests under the molecule/default/tests folder using the goos verifier.  
7. When ready, use `molecule converge` to run the Ansible Playbook and `molecule verify` to execute the test suite.  
Note that the converge process starts performing a syntax check of the role.  
Destroy the Docker container with the command `molecule destroy`.   

To run all the steps with just one command, run `molecule test`. 

In order to run the role targeting a VM, use the playbook_deploy.yml file for example with the following command: `ansible-playbook ansible-mcrouter/molecule/default/playbook_deploy.yml -i VM_IP_OR_FQDN, -u ubuntu --private-key private.pem`.  

## License

MIT
