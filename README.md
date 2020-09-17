# ansible-logrotate-plusplus
Ansible role which installs and configures logrotate
It can test if paths exist before writing a logrotate config to the server.
Load the roles default vars with custom paths and per path parameters, and run the playbook across a dynamic
infrastructure and only write logerotate rules to the appropriate system with the correct paths present.

This project was based of https://github.com/arillso/ansible.logrotate 1.5.2
(https://github.com/arillso/ansible.logrotate/commit/038649f7933c21ba9f1f2c8363bfb4d49aaf46f2)

