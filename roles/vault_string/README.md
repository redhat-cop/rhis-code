vault_string
=========

This roles encrypts a file in a given path using ansible-vault

Requirements
------------

- Configuration variables should be provided with a variable file.

Role Variables
--------------

```yaml
# configuration variables
vault_string_vault_password: "{{ vault_password }}"

# execution variables
vault_string_filepath:
```

Dependencies
------------

- N/A

Example Playbook
----------------

```yaml
- hosts: rootCA
  roles:
  - role: vault_string
    vars:
      vault_string_filepath: "{{ __rootca_cert_path  }}"
```

License
-------

GPL-3.0-only

Author Information
------------------

Showroom Project Team
