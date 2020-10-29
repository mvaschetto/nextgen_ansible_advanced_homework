app-tier
=========

This rule will install tomcat from yum repository, configure it with a sample HTML page and start the service.

Requirements
------------

No specific requirments

Role Variables
--------------

Vars of this rule are:
| Var Name                      | Default                        | Description                                                     |
|:------------------------------|:-------------------------------|:----------------------------------------------------------------|
| payload                       | tomcat                         | Define the package and service name                             |
| jdk                           | java-1.8.0-openjdk             | Define the package name and version of jdk have to be installed |
| tomcat_web_root               | /usr/share/tomcat/webapps/ROOT | Define the ROOT directory where to deploy the sample page       |

Dependencies
------------

No dependencies

Example Playbook
----------------

    - hosts: apps
      roles:
         - app-tier

License
-------

BSD