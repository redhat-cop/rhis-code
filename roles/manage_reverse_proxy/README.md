manage_reverse_proxy
=========

This roles installs and configures Nginx on the given host. It also configures Azure DNS and NSGs.

Requirements
------------


Role Variables
--------------

```yaml
# defaults file for manage_reverse_proxy
manage_reverse_proxy_letsencrypt_dir: "/etc/letsencrypt"
manage_reverse_proxy_ssl_key_path: "{{ manage_reverse_proxy_letsencrypt_dir }}/{{ inventory_hostname }}.key"
manage_reverse_proxy_crt_path: "{{ manage_reverse_proxy_letsencrypt_dir }}/{{ inventory_hostname }}.crt"

# azure authentication variables
azure_subscription_id:
azure_tenant_id:
techuser_ansible_client_id:
techuser_ansible_secret_value:
```

Dependencies
------------

- public_certificate

Example Playbook
----------------

```yaml
- hosts: bastion
  roles:
    - manage_reverse_proxy
```

License
-------

GPL-3.0-only

Author Information
------------------

Showroom Project Team
