Ansible Hbase
=============

Installs Hbase

Requirements
------------

A version of Java compatible with HBase must be previously installed

Role Variables
--------------

TBD

Dependencies
------------

None

Example Playbook
----------------
````
---
  - hosts: hbase
    become: yes
    become_user: root
    roles:
      - {role: "leobueno.ansible-hbase", hbase_install_type: "pseudo-distributed", hbase_manages_zk: true}
````

License
-------

MIT

Author Information
------------------

Leonardo Bueno

leonardo.bueno@gmail.com
