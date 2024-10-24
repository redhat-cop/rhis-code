---
hide:
  - navigation
  - toc
---

# RHIS Code

This repository is intended to contain ansible automation code. All documents are stored on [RHIS Code](https://github.com/redhat-cop/rhis-code) repository.

!!! abstract
    The goal of this project is to build a Red Hat based environment suitable for a project by an *enterprise* ready approach an opinionated Red Hat infrastructure that implements several Standard Operating Environments for Red Hat Enterprise Linux using Red Hat Management tools (Red Hat Infrastructure Standard Adoption Model).

!!! note "Red Hat Infrastructure Standard (*RH-IS*)"

    The Red Hat Infrastructure Standard (*RH-IS*) is a framework for using integrated Red Hat technologies to build, manage, automate, optimize, and maintain Red Hat Enterprise Linux at scale in a hybrid multi-cloud.
    One of the fundamental principles of the *RH-ISAM* is to strive towards “*_everything as code_*”. The goal is repeatability, consistency, and stability.

## Advantages of implementing the Red Hat Infrastructure Standard

The Red Hat Infrastructure Standard is an opinionated framework for the deployment, configuration, and use of:

* Red Hat Enterprise Linux
* Red Hat Identity Management
* Red Hat Satellite
* Red Hat Ansible Automation Platform
* Red Hat Build of Keycloak

It leverages the Red Hat Hybrid Cloud Console to deploy, patch, maintain, secure, automate and ensure compliance of the Red Hat Enterprise Linux systems across a Hybrid Multi-cloud environment.

GitOps practices are used in the process to define the desired states and conduct tests on management infrastructure and managed systems through an _infrastructure-as-code_ pipeline.

!!! info "URLs"
    1. [RH-IS Builder Repository](https://github.com/redhat-cop/rhis-builder)
