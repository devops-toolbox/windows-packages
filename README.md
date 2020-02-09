Role Name
=========

windows-packages: Windows-packages

[![Build Status](https://travis-ci.org/cmihai-ansible/windows-packages.svg?branch=master)](https://travis-ci.org/cmihai-ansible/windows-packages)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.windows-packages](https://galaxy.ansible.com/devops-toolbox.windows-packages)

```bash
ansible-galaxy install devops-toolbox.windows-packages
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
windows-packages_packages_state: present
windows-packages_remove_packages: true
windows-packages_enable_service: true
windows-packages_enable_selinux: true
windows-packages_copy_templates: true
windows-packages_firewall_configure: true
windows-packages_firewall_rules:
  - service: ssh
  - port: 3389
windows-packages_users:
  - user: devops
    group: docker
windows-packages_selinux_booleans:
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
- name: Install windows-packages on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: windows-packages is configured
      import_role:
        name: devops-toolbox.windows-packages
      vars:
        windows-packages_packages_state: present
        windows-packages_remove_packages: true
        windows-packages_enable_service: true
        windows-packages_enable_selinux: true
        windows-packages_copy_templates: true
        windows-packages_firewall_configure: true
        windows-packages_firewall_rules:
          - service: ssh
          - port: 3389
        windows-packages_users:
          - user: devops
            group: docker
        windows-packages_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: windows-packages
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
