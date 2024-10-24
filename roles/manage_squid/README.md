manage_squid
=========

This roles installs squid package and configures it to allow internal network access.

Requirements
------------

This role needs ansible.posix collection to be installed, user and password to be defined in the inventory.

Role Variables
--------------

```yaml
---
# defaults file for manage_squid
manage_squid_allowed_network: "10.0.0.0/8"
manage_squid_http_port: 3128
manage_squid_admin_username: squid_user
manage_squid_admin_password: squid_password
```

Dependencies
------------


Example Playbook
----------------

```yaml
- hosts: bastion
  roles:
    - manage_Squid
```

License
-------

GPL-3.0-only

Author Information
------------------

Showroom Project Team
