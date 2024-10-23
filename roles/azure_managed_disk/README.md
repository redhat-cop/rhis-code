azure_managed_disk
=========

This roles creates and mounts Azure managed disk to VM.

Requirements
------------

- An Azure custom app must be created and granted contributor access on subscription level to perform the ansible tasks.
- An Azure VM should have been provisioned.

Role Variables
--------------

```yaml
# default variables
azure_managed_disk_state: present

# azure authentication variables
azure_subscription_id:
azure_tenant_id:
techuser_ansible_client_id:
techuser_ansible_secret_value:

# azure managed disk configuration variables
azure_rg:
azure_managed_disk_name:
azure_managed_disk_size:
azure_managed_disk_storage_account_type:
```

Dependencies
------------

- azure_resource_group
- imagebuilder (when custom image is needed.)
- azure_network
- azure_dns (when public IP and public DNS record needed.)

Example Playbook
----------------

```yaml
- hosts: bastion
  roles:
    - azure_resource_group
    - imagebuilder
    - azure_network
    - azure_vm_deploy
    - azure_dns
    - azure_managed_disk
```

License
-------

GPL-3.0-only

Author Information
------------------

Showroom Project Team