init_environment
=========

This roles initializes configuration on local host to be able to run ansible code that is required for the project.

* creates, encrypts and commit SSH RSA keypair if it does not exist in the inventory repository
* configures SSH config file to be able to access to the internal resources through Bastion host

Requirements
------------
The role is disabled by default unless you need to configure it.

Role Variables
--------------

```yaml
---
# variable to run role
init_environment_set: false

```

Dependencies
------------


Example Playbook
----------------

```yaml
- hosts: localhost
  gather_facts: true
  roles:
    - init_environment
```

License
-------

GPL-3.0-only

Author Information
------------------

Showroom Project Team
