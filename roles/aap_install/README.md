azure_dns
=========

This role installs AAP in an automated way.

Requirements
------------

- A Red Hat Satellite server should be provisioned and AAP contents downloaded.
- Installed Satellite credentials should have been placed under inventory.
- Host certificates should have been created on the hosts by IDM.

Role Variables
--------------

```yaml
# default variables
aap_install_repo_name: "Red Hat Ansible Automation Platform 2.4 for RHEL 9 x86_64 Files"
aap_install_product: "Red Hat Ansible Automation Platform"
aap_install_search_param: "name ~ platform-setup"
aap_install_destination_dir: "/var/aap-install"
aap_install_certs_dir: "{{ aap_install_destination_dir }}/certs"
aap_install_aap_bundle_file: "ansible-automation-platform-setup-2.4-7.tar.gz"
```

Dependencies
------------

- redhat.satellite

Example Playbook
----------------

```yaml
- hosts: bastion
  roles:
    - role: pki_idm_generate_certs
      become: true
    - role: aap_install
```

License
-------

GPL-3.0-only

Author Information
------------------

Showroom Project Team
