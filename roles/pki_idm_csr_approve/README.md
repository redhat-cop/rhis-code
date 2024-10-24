pki_idm_csr_approve
=========

This role signs Red Hat Identity Management (IdM) CSR with rootCA certificate.

Requirements
------------

A signed rootCA certificate should be existed on rootCA VM.

Role Variables
--------------

```yaml
# default variables
pki_idm_csr_approve_csr_path_idm: /root/ipa.csr
pki_idm_csr_approve_crt_path_idm: /root/chain.crt

pki_idm_csr_approve_csr_path_rootca: /tmp/ipa.csr
pki_idm_csr_approve_crt_path_rootca: /tmp/ipa.crt
pki_idm_csr_approve_chain_path_rootca: /tmp/chain.crt

pki_idm_csr_approve_root_path: /etc/ssl/ca
pki_idm_csr_approve_key: rootca_certificate.key
pki_idm_csr_approve_cert: rootca_certificate.crt
pki_idm_csr_approve_passphrase_secret: "{{ ca_root_passphrase_secret }}"
```

Dependencies
------------

- pki_rootca

Example Playbook
----------------

```yaml
- hosts: rootCA
  roles:
    - pki_rootca
    - pki_idm_cert
```

License
-------

GPL-3.0-only

Author Information
------------------

Showroom Project Team
