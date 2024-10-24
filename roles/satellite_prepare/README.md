satellite_prepare
=========

This roles prepares host to Red Hat Satellite installation.

Requirements
------------

- A VM must be deployed to run the role.

Role Variables
--------------

```yaml
# default variables
satellite_prepare_ipa_default_bind_policy: "grant {{ ipaclient_realm }} krb5-self * A; grant {{ ipaclient_realm }} krb5-self * AAAA; grant {{ ipaclient_realm }} krb5-self * SSHFP;"
satellite_prepare_foreman_proxy_realm_principal: ""
satellite_prepare_foreman_proxy_bind_update_policy: "{{ satellite_prepare_ipa_default_bind_policy }} grant {{ satellite_prepare_foreman_proxy_realm_principal }}\@{{ ipaclient_realm }} wildcard * ANY;"
satellite_prepare_keytab_path: ""
satellite_prepare_skip_prepare_realm: false

# configuration variables
satellite_prepare_ipa_server_ca_path: "{{ ipa_server_ca_path }}"
satellite_prepare_ipa_client_trust_path: "{{ ipa_client_trust_path }}"
satellite_prepare_ipaclient_domain: "{{ ipaclient_domain }}"

```

Dependencies
------------

- RH IdM is required to be deployed before when RH Satellite will be used with Kerberos integration preferred with RH IdM.

Example Playbook
----------------

```yaml
- hosts: satellite
  roles:
  - role: satellite_prepare
    become: true
```

License
-------

GPL-3.0-only

Author Information
------------------

Showroom Project Team
