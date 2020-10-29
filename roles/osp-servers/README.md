osp-server
=========

This rule will create  instances in the provided cloud. It will associated FloatingIP to each instance also.

Requirements
------------

The host run this playbook need to have installed the openstacksdk package. 

Role Variables
--------------

Vars of this rule are:
| Var Name                      | Default                        | Required | Description                                                          |
|:------------------------------|:-------------------------------|:---------|:---------------------------------------------------------------------|
| name                          | Null                           | True     | Name to give to the instance                                         |
| cloud                         | openstack                      | True     | Cloud to connect for create instance must match the clouds.yaml conf |
| secgroup                      | Null                           | False    | Security group to associate to the instance                          |
| meta                          | Null                           | False    | Meta do add to the instance                                          |
| ansible_key                   | Null                           | False    | ssh keypare name to add in the instance                              |
| image                         | Null                           | True     | Image name from where start the instance                             |
| flavor                        | Null                           | True     | Flavor name to associate to the created instance                     |
| priv_net                      | Null                           | True     | Private network where attach the instance                            |
| pub_net                       | Null                           | True     | External network from where obtain floating IP                       |
| userdata                      | Null                           | False    | Additional user data to add in the instance                          |
 

Dependencies
------------

No dependencies.

Example Playbook
----------------
```yaml
- hosts: localhost
  connection: local
  become: no
  gather_facts: true

  vars:
    instances:
      - name: frontend
        cloud: openstack
        secgroup: frontend
        meta: 'group=frontends,deployment_name=dev'
        ansible_key: ansible_ssh
        image: rhel-guest
        flavor: m1.medium
        priv_net: int_network
        pub_net: ext_network
        userdata:  |
          #!/bin/bash
          curl -o /tmp/openstack.pub http://www.opentlc.com/download/ansible_bootcamp/openstack_keys/openstack.pub
          cat /tmp/openstack.pub >> /home/cloud-user/.ssh/authorized_keys
      - name: app1
        cloud: openstack
        secgroup: apps
        meta: 'group=apps,deployment_name=QA' 
        ansible_key: ansible_ssh
        image: rhel-guest
        flavor: m1.medium
        priv_net: int_network
        pub_net: ext_network
        userdata:  |
          #!/bin/bash
          curl -o /tmp/openstack.pub http://www.opentlc.com/download/ansible_bootcamp/openstack_keys/openstack.pub
          cat /tmp/openstack.pub >> /home/cloud-user/.ssh/authorized_keys
        ......
  roles:
   - osp-servers
```
License
-------

BSD
