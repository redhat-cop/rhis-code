idm_config
=========

The role configures RH IdM Server for basic start.

Requirements
------------

- RH IdM VMs should have been provisioned and deployed.
- RH IdM is running properly.
- Configuration variables should be provided with a variable file.

Role Variables
--------------

```yaml
# default anf general variables
idm_config_allow_sync_ptr: true
idm_config_dynamic_update: true
ipaadmin_principal: "{{ ipaadmin_principal | default(omit) }}"
ipaadmin_password: "{{ ipaadmin_password }}"

# DNS variables
zone_name: "{{ idm_default_dns_zone }}"
idm_config_reverse_dns_networks: ""

# user variables
idm_users:
  - name: "test-user"
    first: "test first name"
    last: "test surname"
    email: "test@test-domain.com"
    state: present

# group
idm_user_groups:
  - name: "test-group"
    desc: "test group description"

# sudo
idm_sudo_rules:
  - name: "test-admin"
    description: "Control sudo access on all servers for admins"
    state: present
    cmdcategory: all
    hostcategory: all
    group:
      - admins

# sudo commands
idm_sudo_commands:
  - name: "/opt/test"
    description: "Command to configure test command"
    state: present

# password policy
idm_password_policy:
  - name: "global_policy"
    state: "present"
    history: "3"
    maxlife: "90"
    minlife: "1"
    minclasses: "3"
    minlength: "12"
    maxfail: "5"
    failinterval: "60"
    lockouttime: "1200"
    maxrepeat: "3"
    maxsequence: "3"
    dictcheck: "true"
    usercheck: "true"
    gracelimit: "2"
    priority: ""

# HBAC
idm_hbac_rules:
  - name: test_allow_all
    description: "Realm Test Admin accesses all hosts"
    state: present
    hostcategory: all
    servicecategory: all
    group:
      - test
      - test-other
```

Dependencies
------------

- N/A

Example Playbook
----------------

```yaml
- hosts: ipahidden
  roles:
    - idm_config
```

License
-------

GPL-3.0-only

Author Information
------------------

Showroom Project Team
