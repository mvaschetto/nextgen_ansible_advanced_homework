osp-setup
=========

This rule will create  Networks, image, keypare and security group on OSP

Requirements
------------

The host run this playbook need to have installed the openstacksdk package. 

Role Variables
--------------

Vars of this rule are:
* external

| Var Name                  | Default      | Description                             |
|:--------------------------|:------------ |:--------------------------------------- |
| cloud_name                | openstack    | Define cloud to connect to.             | 
| network_name              | ext_network  | Define name of external network         |
| provider_network_type     | flat         | Define network provider type            |
| provider_physical_network | datacentre   | Define the provider int name            |
| subnet_name               | ext_subnet   | Define subnet name                      |
| cidr_network              | 192.0.2.0/24 | Define network ip and subnet mask       |
| state                     | present      | Define state of this object in OSP      |
| external                  | true         | Define network type                     |
| gateway_ip                | 192.0.2.254  | Define default gateway for the subnet   |
| admin_state               | yes          | Define admine state in OSP              |
| ip_version                | 4            | Define version of IP for the subnet     |
| enable_dhcp               | no           | Define the DHCP service to start or not |
| allocation_pool_start     | 192.0.2.150  | Start IP for DHCP assigment             |
| allocation_pool_end       | 192.0.2.200  | End IP for DHCP assigment               |

  * internal

  | Var Name                      | Default       | Description                             |
  |:------------------------------|:------------- |:--------------------------------------- |
  | cloud_name                    | openstack     | Define cloud to connect to.             |
  | network_name                  | int_network   | Define name of external network         |
  | subnet_name                   | int_subnet    | Define subnet name                      |
  | cidr_network                  | 172.16.0.0/24 | Define network ip and subnet mask       |
  | state                         | present       | Define state of this object in OSP      |
  | external                      | false         | Define network type                     |
  | admin_state                   | yes           | Define admine state in OSP              |
  | ip_version                    | 4             | Define version of IP for the subnet     |
  | enable_dhcp                   | yes           | Define the DHCP service to start or not |

  * router

  | Var Name   | Default     | Description                               |
  |:-----------|:------------|:------------------------------------------|
  | cloud_name | openstack   | Define cloud to connect to.               |
  | state      | present     | Define state of this object in OSP        |
  | name       | router      | Define router name                        |
  | network    | ext_network | Define the externak network of the router | 
  | interfaces | int_subnet  | Define internal network of the router     |
 

Dependencies
------------

No dependencies.

Example Playbook
----------------
```yaml
- hosts: workstation
  become: yes
  roles:
    - osp-setup

```
License
-------

BSD
