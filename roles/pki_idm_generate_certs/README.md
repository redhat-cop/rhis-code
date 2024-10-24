azure_dns
=========

This role generates signed certificate for the host using IDM.

Requirements
------------

- A Red Hat Satellite server should be provisioned and AAP contents downloaded.
- Installed Satellite credentials should have been placed under inventory.

Role Variables
--------------

```yaml
# idm authentication variables
ipaadmin_principal: "{{ ipaadmin_principal }}"
ipaadmin_password: "{{ ipaadmin_password }}"

# default variables
pki_idm_generate_certs_ssl_certs_dir: "/etc/ipa/private/"
pki_idm_generate_certs_ssl_crt_path: "{{ pki_idm_generate_certs_ssl_certs_dir }}{{ inventory_hostname }}.crt"
pki_idm_generate_certs_ssl_key_path: "{{ pki_idm_generate_certs_ssl_certs_dir }}{{ inventory_hostname }}.key"
pki_idm_generate_certs_ssl_csr_path: "{{ pki_idm_generate_certs_ssl_certs_dir }}{{ inventory_hostname }}.csr"
pki_idm_generate_certs_ssl_rsa_key_pass: ""

pki_idm_generate_certs_crt_service_type: "HTTP"
pki_idm_generate_certs_crt_force_regen: true
pki_idm_generate_certs_ssl_private_key_cipher: "auto"
pki_idm_generate_certs_ssl_private_key_size: 4096
pki_idm_generate_certs_ssl_private_key_format: "pkcs8"
pki_idm_generate_certs_csr_digest: ""
pki_idm_generate_certs_csr_common_name: ""
pki_idm_generate_certs_csr_organization_name: ""
pki_idm_generate_certs_csr_organization_unit_name: ""
pki_idm_generate_certs_csr_locality_name: ""
pki_idm_generate_certs_csr_state_or_province_name: ""
pki_idm_generate_certs_csr_country_name: ""
pki_idm_generate_certs_csr_email_address: ""
pki_idm_generate_certs_csr_subject_alt_name: ""

# configuration variables
pki_idm_generate_certs_ipa_server_ca_path:
pki_idm_generate_certs_ipa_client_trust_path:
idm_default_dns_zone:
```

Dependencies
------------

- redhat.rhel_idm

Example Playbook
----------------

```yaml
- hosts: bastion
  roles:
    - pki_dim_generate_certs
      become: true
```

License
-------

GPL-3.0-only

Author Information
------------------

Showroom Project Team
