Role Name
=========

mandb: Mandb

[![Build Status](https://travis-ci.org/cmihai-ansible/mandb.svg?branch=master)](https://travis-ci.org/cmihai-ansible/mandb)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.mandb](https://galaxy.ansible.com/devopstoolbox.mandb)

```bash
ansible-galaxy install devopstoolbox.mandb
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
mandb_packages_state: present
mandb_remove_packages: true
mandb_enable_service: true
mandb_enable_selinux: true
mandb_copy_templates: true
mandb_firewall_configure: true
mandb_firewall_rules:
  - service: ssh
  - port: 3389
mandb_users:
  - user: devops
    group: docker
mandb_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install mandb on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: mandb is configured
      import_role:
        name: devopstoolbox.mandb
      vars:
        mandb_packages_state: present
        mandb_remove_packages: true
        mandb_enable_service: true
        mandb_enable_selinux: true
        mandb_copy_templates: true
        mandb_firewall_configure: true
        mandb_firewall_rules:
          - service: ssh
          - port: 3389
        mandb_users:
          - user: devops
            group: docker
        mandb_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: mandb
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devopstoolbox.)
