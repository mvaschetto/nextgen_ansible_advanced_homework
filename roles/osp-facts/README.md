ops-facts
=========

This rule will collect information on OSP and create and inventory on memory where to run all other playbook and install the tier-app

Requirements
------------

No specific requirments

Dependencies
------------

No dependencies

Example Playbook
----------------
```yaml
- hosts: localhost
  gather_facts: false 

  roles:
    - ops-facts
```
License
-------

BSD