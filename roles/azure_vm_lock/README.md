azure_vm_lock
=========

This roles power-offs and locks the VM.

Requirements
------------

- An Azure custom app must be created and granted Owner access on subscription level to perform Microsoft.Authorization/* or Microsoft.Authorization/locks/* actions.

Role Variables
--------------

```yaml
# default variables
azure_vm_lock_state: present

# azure authentication variables
azure_subscription_id:
azure_tenant_id:
techuser_ansible_client_id:
techuser_ansible_secret_value:

```

Dependencies
------------

- azure_resource_group
- imagebuilder (when custom image is needed.)
- azure_network
- azure_dns (when public IP and public DNS record needed.)
- azure_vm_deploy

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
    - azure_vm_lock
```

License
-------

GPL-3.0-only

Author Information
------------------

Showroom Project Team