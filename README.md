ansible-role-hazelcast
=========

## This Ansible Role is not production ready! 
## As of today, July 4, 2023, it does not work!

This is an Ansible role for installing Hazelcast Enterprise.
This is **not** an official Hazelcast product, simply a side project by someone who happens to work there.
This software is not supported, but comments and bug reports are welcome.


Requirements
------------

Hazelcast Enterprise requires a license key to work.  This isn't in the zip file you download from Hazelcast.  


If you need a license and don't have one, please visit https://hazelcast.com/pricing/

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

```
---
- name: Ensure Java 17 and Hazelcast is installed
  hosts: vmware
  become: yes
  vars:
    hazelcast_version: "5.1.2"
  roles:
    - jimoconnell.ansible_role_hazelcast

  tasks:
    - name: Copy the local hazelcast.xml file
      copy:
        src: ./hazelcast.xml
        dest: /opt/hazelcast/config/hazelcast.xml
        owner: root
        group: root
        mode: '0644'
      
    - name: Start Hazelcast service
      systemd: 
        name: hazelcast.service
        state: started
        daemon_reload: yes
```

License
-------

MIT

Author Information
------------------


