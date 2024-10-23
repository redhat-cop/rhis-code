azure_dns
=========

This roles creates DNS zones and DNS records in Microsoft Azure.

Requirements
------------

An Azure custom app must be created and granted contributor access on subscription level to perform the ansible tasks.

Role Variables
--------------

```yaml
# default variables
azure_dns_zone_state: present
azure_dns_private_dns_zone_state: present

# azure authentication variables
azure_subscription_id:
azure_tenant_id:
techuser_ansible_client_id:
techuser_ansible_secret_value:

# azure resource group configuration variables
azure_rg:
azure_dns_zone:
azure_dns_registration_enabled:
```

Dependencies
------------

- azure_resource_group

Example Playbook
----------------

```yaml
- hosts: bastion
  roles:
    - azure_resource_group
    - azure_dns
```

License
-------

GPL-3.0-only

Author Information
------------------

Showroom Project Team
