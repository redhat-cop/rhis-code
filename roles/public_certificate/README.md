public_certificate
=========

This roles creates a CSR and request Let's encrypt to sign it.

Requirements
------------


Role Variables
--------------

```yaml
# defaults file for public_certificate
public_certificate_acme_version: 2
public_certificate_acme_directory: https://acme-v02.api.letsencrypt.org/directory
public_certificate_acme_challenge_type: dns-01
public_certificate_acme_challenge_subdomain: "_acme-challenge.{{ azure_dns_private_dnz_zone_subdomain }}"
public_certificate_letsencrypt_dir: "/etc/letsencrypt"

public_certificate_letsencrypt_account_key_path: "{{ public_certificate_letsencrypt_dir }}/account.key"
public_certificate_letsencrypt_ssl_key_path: "{{ public_certificate_letsencrypt_dir }}/{{ inventory_hostname }}.key"
public_certificate_letsencrypt_csr_path: "{{ public_certificate_letsencrypt_dir }}{{ inventory_hostname }}.csr"
public_certificate_letsencrypt_crt_path: "{{ public_certificate_letsencrypt_dir }}/{{ inventory_hostname }}.crt"
public_certificate_letsencrypt_chain_path: "{{ public_certificate_letsencrypt_dir }}/{{ inventory_hostname }}_chain.crt"
public_certificate_letsencrypt_fullchain_path: "{{ public_certificate_letsencrypt_dir }}/{{ inventory_hostname }}_fullchain.crt"

# azure authentication variables
azure_subscription_id:
azure_tenant_id:
techuser_ansible_client_id:
techuser_ansible_secret_value:
```

Dependencies
------------


Example Playbook
----------------

```yaml
- hosts: bastion
  roles:
    - public_certificate
```

License
-------

GPL-3.0-only

Author Information
------------------

Showroom Project Team
