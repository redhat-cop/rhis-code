post_config
=========

This roles runs post configuration tasks on new provisioned VMs;
- Installs defined packages
- Copies private key when required.

Requirements
------------


Role Variables
--------------

```yaml
# defaults file for post_config
post_config_priv_key: false
# to install custom packages define this var in the inventory
# post_config_packages:
#   - git
#   - ansible-core
```

Dependencies
------------


Example Playbook
----------------

```yaml
- hosts: bastion
  roles:
    - post_config
```

License
-------

GPL-3.0-only

Author Information
------------------

Showroom Project Team
