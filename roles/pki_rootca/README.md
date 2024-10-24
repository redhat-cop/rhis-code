pki_rootca
=========

This roles creates private key and self-signed rootCA certificate.

Requirements
------------

- A server should have been provisioned to create and store the rootCA private key and self-signed certificate.
- Configuration variables should be provided with a variable file.

Role Variables
--------------

```yaml
# default variables
pki_root_ca_root_path: /etc/ssl/ca/
pki_root_ca_key: root-ca-certificate.key
pki_root_ca_cert: root-ca-certificate.crt

# configuration variables
pki_rootca_passphrase_secret: "{{ ca_root_passphrase_secret }}"
pki_rootca_ca_common_name: "{{ ca_common_name }}"
```

Dependencies
------------

- N/A

Example Playbook
----------------

```yaml
- hosts: rootCA
  roles:
    - pki_rootca
```

License
-------

GPL-3.0-only

Author Information
------------------

Showroom Project Team
