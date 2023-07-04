ansible-role-hazelcast
=========

## This Ansible Role is not production ready! 
## As of today, July 4, 2023, it does not work!

This is an Ansible role for installing Hazelcast Enterprise.
This is **not** an official Hazelcast product, simply a side project by someone who happens to work there. 

* This software is not supported. 
* I have written this for my own convenience.  
* This software is not supported. 
* It works for me, but may break at any time.
* This software is not supported. 
* Comments and bug reports are welcome. (Use: https://github.com/jimoconnell/ansible-role-hazelcast)
* This software is not supported. 
* You have been warned!


Requirements
------------

Hazelcast Enterprise requires a license key to work.  This isn't in the zip file you download from Hazelcast.  
To get around this, put your `hazelcast.xml` file that includes your key in the same directory where you have your playbook. (See the example playbook below.) 
It should have a line like the following (non-working) license string, most likely:
```
 <license-key>YOURLICENSE#3NODES1234567890000000</license-key>
 ```

If you need a license and don't have one, please visit https://hazelcast.com/pricing/

Role Variables
--------------

In the sample playbook below, the Hazelcast Version is set with:
```
  vars:
    hazelcast_version: "5.1.2"
```    

Dependencies
------------

I will most likely create a role for Management Center, but there isn't one yet.
To install this role, cd into your playbook directory and run:
```
ansible-galaxy install jimoconnell.ansible_role_hazelcast
```

Example Playbook
----------------

```
---
- name: Ensure Java 17 and Hazelcast is installed
  hosts: vmware
  become: yes
  vars:
    hazelcast_version: "5.3.1"
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


