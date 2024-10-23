azure_snapshot
=========

This role creates and deletes snapshots for all disk of a VM.

Role Variables
--------------

```yaml
# azure authentication variables
azure_subscription_id:
azure_tenant_id:
techuser_ansible_client_id:
techuser_ansible_secret_value:

# Custom variables
azure_snapshot_state:
```

Dependencies
------------


Example Playbook
----------------

```yaml
---
- name: Manage Azure Snapshot
  hosts: "{{ host | default('localhost') }}"
  gather_facts: false

  roles:
    - role: azure_snapshot
      when:
      - azure_snapshot | bool()
      tags: azure_snapshot
      delegate_to: localhost
```

License
-------

GPL-3.0-only

Author Information
------------------

Showroom Project Team