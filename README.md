ansible-ucrm
=========

Role to install Ubiquiti UCRM software using the official installer.

Requirements
------------

  * ansible >= 2.6
  * python3

Role Variables
--------------

| Variable Name | Default | Description |
|---------------|---------|-------------|
| http_port | 8080 | UCRM http port |
| https_port | 8443 | UCRM https port |
| suspension_port | 8081 | UCRM service suspension port |
| netflow_port | 2055 | UCRM Netflow port |
| subnet | 192.168.80.1/24 | Docker public subnet |
| subnet_internal | 192.168.90.1/24 | Docker pirvate subnet |
| skip_system_setup | false | Do not check system and install requirements (docker, docker-compose, create user) |
| no_auto_update | true | Do not auto update the running container |
| ucrm_uninstall | false | Uninstall UCRM. It removes the .env and .yml files, and makes a backup of the current data directory|

Dependencies
------------

N/A

Example Playbook
----------------
Playbook:

    - hosts: all
      become: True
      become_method: sudo
      gather_facts: yes

      vars_files:
        - vars/ucrm.yml
      roles:
       - ucrm

Vars file:

    ---
    skip_system_setup: true
    no_auto_update: false
    ucrm_user: ansible


License
-------

GPLv3

Author Information
------------------

Juan Luis Baptiste - (juan (__at__) juanbaptiste __dot__ tech)
