satellite_host_deploy
=========

This role deploy/deletes host (VM) on defined host group in location, organization, with using specified image in the compute resource.

Requirements
------------

Satellite host group must be configured and specified. Location and organization information must be defined. Also image and the compute resource of the image must be defined.

Role Variables
--------------

```yaml
# default variables
satellite_host_deploy: true
satellite_host_deploy_hostgroup: "hg_example"
satellite_host_deploy_compute_attributes:
  vm_size: "Standard_B1ms"
  tags: "sequencestart=1,sequencestop=5"
satellite_host_deploy_organization: "{{ satellite_organization }}"
satellite_host_deploy_location: "{{ satellite_location }}"
satellite_host_deploy_compute_resource: "example_compute_resource"
satellite_host_deploy_image: "example_image"
satellite_host_compute_profile: "example_compute_profile"
# Optional variables
satellite_host_deploy_state: [ present|absent ] # default value is present
```

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

```yaml
- hosts: host.example.com | example_group
  roles:
    - satellite_host_deploy
```

License
-------

GPL-3.0-only

Author Information
------------------

Showroom Project Team