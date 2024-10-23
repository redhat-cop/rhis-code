aap_config
=========

This role configures Controller and Private Automation Hub.

Requirements
------------

- Ansible Automation Platform deployed and running.
- Installed Ansible Automation Platform credentials should have been placed under inventory.
- Configuration variables are defined under inventory.

Role Variables
--------------

```yaml
# variables
aap_config: true
aap_config_pah_repo_sync: true
aap_config_organization: ""

aap_config_inventory_repo_name: ""
aap_config_default_project: ""
aap_config_default_inventory: ""

aap_config_default_credentials:
  - "Machine Credential"
  - "Vault Credential"
aap_config_default_notification_template: "Slack Notifications"
aap_config_default_execution_environment: "Automation Hub Default Remote execution environment"
aap_config_default_job_run: "run"

aap_config_default_scm_branch: ""

controller_configuration_projects_async_retries: "90"

controller_hostname: ""
controller_username: ""
controller_password: "{"

ah_hostname: ""
ah_username: ""
ah_password: ""
```

Dependencies
------------

- ansible.controller
- infra.controller_configuration
- infra.ee_utilities
- infra.ah_configuration

Example Playbook
----------------

```yaml
- hosts: bastion
  roles:
    - role: pki_idm_generate_certs
      become: true
    - role: aap_install
    - role: aap_config
```

License
-------

GPL-3.0-only

Author Information
------------------

Showroom Project Team
