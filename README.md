# RHIS-code

[![Ansible Lint](https://github.com/redhat-cop/rhis-code/actions/workflows/ansible-lint.yml/badge.svg)](https://github.com/redhat-cop/rhis-code/actions/workflows/ansible-lint.yml/badge.svg) [![Slack Channel](https://img.shields.io/badge/slack-channel-tech?logo=slack)](https://redhat.enterprise.slack.com/archives/C07TAP5PJ8K)


This repository is intended to contain ansible automation code. All documents are stored on [docs](https://github.com/redhat-cop/rhis-code/docs).

The goal of this project is to build a Red Hat based environment by an *enterprise* ready approach an opinionated Red Hat infrastructure that implements several Standard Operating Environments for Red Hat Enterprise Linux using Red Hat Management tools (Red Hat Infrastructure Standard Adoption Model).

The Red Hat Infrastructure Standard (*RH-IS*) [RHIS Builder](https://github.com/redhat-cop/rhis-builder) is a framework for using integrated Red Hat technologies to build, manage, automate, optimize, and maintain Red Hat Enterprise Linux at scale in a hybrid multi-cloud.
One of the fundamental principles of the *RH-ISAM* is to strive towards **everything as code**. The goal is repeatability, consistency, and stability and being modular.

## Advantages of implementing the Red Hat Infrastructure Standard

The Red Hat Infrastructure Standard is an opinionated framework for the deployment, configuration, and use of:

* Red Hat Enterprise Linux
* Red Hat Identity Management
* Red Hat Satellite
* Red Hat Ansible Automation Platform
* Red Hat Build of Keycloak

It leverages the Red Hat Hybrid Cloud Console to deploy, patch, maintain, secure, automate and ensure compliance of the Red Hat Enterprise Linux systems across a Hybrid Multi-cloud environment.

GitOps practices are used in the process to define the desired states and conduct tests on management infrastructure and managed systems through an infrastructure-as-code pipeline.

There are also external tools used to to simulate integration points such as

* Self hosted GitHub Runner
* RootCA based on OpenSSL

## Where to Start
Current [RHIS-code](https://github.com/redhat-cop/rhis-code) consumes [RHIS-inventory](https://github.com/redhat-cop/rhis-inventory) repository for the credentials and configurable variables. Duplicate *RHIS-inventory repository* as your own inventory to use if you plan to deploy environment on your own and update definitions based on your own.

First you can initialize your local environment by running `landscape_init.yml`. This playbook will create an SSH Key pair and configuration for the generic SSH that enables access using Bastion. SSH public key will encrypted and pushed to the inventory repository.

```bash
ansible-playbook -i rhis-inventory/inventory.yml rhis-code/playbooks/landscape_init.yml --ask-vault-pass -e init_environment_set=true
```

`landscape_site.yml` is the main Ansible playbook to trigger everything from scratch for a *Big Bang*.

```bash
ansible-playbook -i rhis-inventory/inventory.yml rhis-code/playbooks/landscape_site.yml --ask-vault-pass
```

Refer to [Where to Start docs](docs/where_to_start.md) for more information.
