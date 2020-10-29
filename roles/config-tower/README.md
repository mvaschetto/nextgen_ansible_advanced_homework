config-tower
=========

This rule will configure Ansible tower with an isolated node to manage OSP environment

Requirements
------------

No specific requirments

Variables
---------
| Var Name                      | Default | Description                    |
|:------------------------------|:--------|:-------------------------------|
| proj_name                     | Null    | Define the Project name        |
| proj_desc                     | Null    | Define the Project description |

Dependencies
------------

No dependencies

Example Playbook
----------------
```yaml
- hosts: localhost
  gather_facts: false 
  become: yes 

  vars:
    - proj_name: "Homework"
    - proj_desc: "Homework assignment"
  roles:
    - config-tower
```
License
-------

BSD