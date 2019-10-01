# perun-ansible-logrotate

Ansible galaxy role cesnet.logrotate that installs logrotate and prepare basic configuration (without postscript, endscript, ...).

## Requirements


## Role variables
* logrotate_applications - Structure of configuration for logrotate

## Available tags
* install
* configure

## Example playbook
```
- hosts: all
  remote_user: root
  vars:
    logrotate_aplications:
      - name: application_name
        definition:
          - path:
                - path1
                - path2
            options: 
                - option1
                - option2
  roles:
    - cesnet.logrotate
```