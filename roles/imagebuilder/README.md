imagebuilder
=========

This roles creates custom images using RH Insights Image builder API if it's not already in Azure resource group.

Requirements
------------
An Azure custom app must be created and granted contributor access on subscription level to perform the ansible tasks.
Red Hat subscriptions and Azure subscriptions should be integrated and Red Hat Image Builder enterprise app in Azure Entra ID should have contributor role at least at resource group level.

Role Variables
--------------

```yaml
---
# variable to run role
imagebuilder: true

imagebuilder_auth_url: "https://sso.redhat.com/auth/realms/redhat-external/protocol/openid-connect/token"
imagebuilder_url: "https://console.redhat.com/api/image-builder/v1/compose"
imagebuilder_status_url: "https://console.redhat.com/api/image-builder/v1/composes/"

imagebuilder_bootstrap_target: "azure"
imagebuilder_image_extension: "vhd"


# you can use the API url to pull a current list of available distributions
imagebuilder_distribution: "rhel-94"
# default image name
imagebuilder_image_name: "image-rhel-94"

# what we will call the image and where we put it
imagebuilder_file_directory: "/tmp"
imagebuilder_image_definition_file: "request-base-image.json"
imagebuilder_image_file_name: "{{ builder_image_name }}.{{ image_extension }}"
imagebuilder_image_file_path: "{{ imagebuilder_file_directory }}/{{ imagebuilder_image_file_name }}"

# Custom packages to include in image. Example as follow;
imagebuilder_packages:
  - firewalld
  - gdisk
  - git-all

# Image definition volume sizes
imagebuilder_filesystem:
  slash_size: 10737418240
  home_size: 1073741824
  var_size: 10737418240
  tmp_size: 1073741824
  var_tmp_size: 1073741824
  var_log_size: 2147483648
  var_log_audit_size: 2147483648

imagebuilder_timezone: "Europe/Berlin"
```

Dependencies
------------

- azure_resource_group

Example Playbook
----------------

```yaml
- hosts: bastion
  roles:
    - azure_resource_group
    - imagebuilder
```

License
-------

GPL-3.0-only

Author Information
------------------

Showroom Project Team