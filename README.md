# perun-ansible-logrotate

Ansible galaxy role cesnet.logrotate that installs logrotate and prepare basic configuration (without postscript, endscript, ...).

## Requirements


## Role variables
* logrotate_files
  * List of files which will be copied to remote host
  * Example value:
    ```
    logrotate_files:
    - { src: "logrotate/app1.conf", dest: "app1.conf", owner: "root", group: "root", mode: "0644"}
    ```
    * where:
      * src - required
      * dest - recommended; if not set, 'src' will be used; Relative to '/etc/logrotate.d/'
      * owner - optional - default 'root'
      * group - optional - default 'root'
      * mode - optional - default '0644'
* logrotate_templates
  * List of files which will be created from template on remote host
  * Example value:
    ```
    logrotate_templates:
    - { src: "logrotate/app1.conf", dest: "app1.conf", owner: "root", group: "root", mode: "0644"}
    ```
    * where:
      * src - required; without '.j2'
      * dest - recommended; if not set, 'src' will be used; Relative to '/etc/logrotate.d/'
      * owner - optional - default 'root'
      * group - optional - default 'root'
      * mode - optional - default '0644'
* logrotate_applications
  * Structure of configuration for logrotate
  * Example value:
    ```
    logrotate_applications:
    - name: application_name
      definition:
        - path: []
          options: []
        - path: []
          options: []
    ```
    , where:
      * application_name - Will be used as configuration file name
      * path - List of path for which will be used list of options
      * options - List of options which will be used for the list of path

## Available tags
* install
* configuration

## Example playbook
```
- hosts: all
  remote_user: root
  vars:
    logrotate_files: []
    logrotate_templates: []
    logrotate_applications:
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
