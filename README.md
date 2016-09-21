Ansible Hbase
=============

Installs Hbase

Requirements
------------

A version of Java compatible with HBase must be previously installed

Role Variables
--------------

````
---
# alternatives are local (implemented), distributed (TODO!), pseudo-distributed (implemented)
hbase_install_type: "local"

hbase_use_hdfs: false

#Used only if hbase_use_hdfs is false
hbase_standalone_dir: "file:///home/hbase/hbase_data"

#Used only if hbase_use_hdfs is true
hbase_hdfs_url: "hdfs://localhost:8020/hbase"

#set to false if you already have zookeper running
hbase_manages_zk: true

#Start hbase at system boot
hbase_enabled: true

# "unkerberized"
hbase_unsecure: true

# hbase.zookeeper.quorum in hbase-site.xml
hbase_zk_nodes: "localhost"

# hbase.table.sanity.checks in hbase-site.xml
hbase_table_sanity_checks: true

hbase_zookeeper_port: 2181

hbase_version: 1.2.3

hbase_zookeeper_data_dir: "{{ hbase_local_dir }}/zookeeper/data"

hbase_zookeeper_extra_config:
    hbase.zookeeper.port:  "{{ hbase_zookeeper_port }}"
    hbase.zookeeper.retry.interval: 5000
    hbase.zookeeper.retry.times: 29
    hbase.zookeeper.root: "/hbase"
    hbase.zookeeper.session.timeout: 30000
    
download_tmp_dir: /tmp

hbase_log_level: WARN

# installs http://phoenix.apache.org
install_phoenix: false

phoenix_version: 4.8.0

# Set properties in hbase-site.xml Default values are set in hbase_default_site_properties 
# in defaults/main.yml and are merged with the var hbase_site_properties
# Example:
hbase_site_properties:
  hbase.table.sanity.checks: false
  hbase.zookeeper.quorum: "example1,example2,example3"
  hbase.coprocessor.master.classes: "org.apache.hadoop.hbase.JMXListener"
  hbase.security.authentication: "kerberos"
  hbase.rest.authentication.type: "kerberos"
  hbase.rest.keytab.file: "/etc/security/keytabs/hbase.service.keytab"
  hbase.rest.kerberos.principal: "HBASE/_HOST@HADOOP.LOCALDOMAIN"

````

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
