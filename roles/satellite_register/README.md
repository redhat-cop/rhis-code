satellite_register
=========

This roles registers the given host to the Red Hat Satellite.

Requirements
------------

- A Red Hat Satellite server should have been provisioned.
- Basic configuration of Red Hat Satellite server should have been done.

Role Variables
--------------

```yaml
# configuration variables
satellite_register_username: "{{ satellite_username }}"
satellite_register_password: "{{ satellite_password }}"
satellite_register_server_url: "https://{{ groups.satellite | first }}"
```

Dependencies
------------

- N/A

Example Playbook
----------------

```yaml
- hosts: bastion
  roles:
  - role: satellite_register
    become: true
```

License
-------

GPL-3.0-only

Author Information
------------------

Showroom Project Team
