azure_vm_deploy
=========

This role deploys VM on Azure and creates public IP and network interface(NIC) if defined.

Requirements
------------

- An Azure custom app must be created and granted contributor access on subscription level to perform the ansible tasks.

Role Variables
--------------

```yaml
# default variables
azure_vm_deploy_public_ip_allocation_method: "static"
azure_vm_deploy_vm_size: "Standard_B4ms"
azure_vm_image_name: "image-rhel-94"
azure_vm_deploy_user: "{{ vm_user }}"
azure_vm_deploy_user_public_key: "{{ vm_user_public_key }}"
azure_vm_deploy_tags: "{{ vm_tags }}"

# azure authentication variables
azure_subscription_id:
azure_tenant_id:
techuser_ansible_client_id:
techuser_ansible_secret_value:

# Custom variables
azure_public_ip: true
vm_tags:
  sequencestart: "3"
  sequencestop: "3"
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
```

License
-------

GPL-3.0-only

Author Information
------------------

Showroom Project Team