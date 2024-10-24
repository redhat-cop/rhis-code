azure_resource_group
=========

This roles creates Resource Group in Microsoft Azure.

Requirements
------------

An Azure custom app must be created and granted contributer access on subscription level to perform the ansible tasks.

Role Variables
--------------

```yaml
# default variables
azure_resource_group_state: present
azure_resource_group_teardown: false

# azure authentication variables
azure_subscription_id:
azure_tenant_id:
techuser_ansible_client_id:
techuser_ansible_secret_value:

# azure resource group configuration variables
azure_rg:
azure_region:
```

Example Playbook
----------------

```yaml
- hosts: bastion
  roles:
    - azure_resource_group
```

License
-------

GPL-3.0-only

Author Information
------------------

Showroom Project Team
