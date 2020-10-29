ops-instance-delete
=========

This rule will get and destroy all instances in the provided cloud. It will remove also associated FloatingIP.

Requirements
------------

The host run this playbook need to have installed the openstacksdk package. 

Role Variables
--------------

Vars of this rule are:
| Var Name                      | Default                        | Description                                                     |
|:------------------------------|:-------------------------------|:----------------------------------------------------------------|
| cloud                         | openstack                      | Define cloud name, this need to match with the definition in clouds.yml file                             |


Dependencies
------------

No dependencies.

Example Playbook
----------------

    - hosts: localhost
      var:
        - cloud: openstack
      roles:
         - ops-install-delete

License
-------

BSD
