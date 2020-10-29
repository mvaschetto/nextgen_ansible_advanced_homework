app-tier
=========

This rule will install haproxy from yum repository and configure it with the defined backend.

Requirements
------------

No specific requirments

Role Variables
--------------

Vars of this rule are:
| Var Name                      | Default                        | Description                                                     |
|:------------------------------|:-------------------------------|:----------------------------------------------------------------|
| payload                       | haproxy                        | Define the package and service name                             |


Dependencies
------------

No dependencies

Example Playbook
----------------

    - hosts: frontend
      roles:
         - lb-tier

License
-------

BSD