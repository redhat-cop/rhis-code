# GitOps with Ansible
This document explains the basic approach in the project to automate
everything as a code and also manage changes with Ansible based on
GitOps.

## What is IaC?

IaC stands for Infrastructure as Code. It’s a practice in software
engineering where infrastructure is managed using code and software
development techniques. Instead of manually setting up and configuring
servers, networks, and other infrastructure components, IaC allows
developers and system administrators to define and manage infrastructure
configuration through code. This code is typically version-controlled,
enabling automation, consistency, and reproducibility in deploying and
managing infrastructure.

!!! quote

    GitOps works by using Git as a single source of truth for declarative infrastructure and applications —  Weaveworks 'Guide To GitOps'

## What is GitOps?

GitOps represents a workflow rooted in Martin Fowler’s seminal
[Continuous
Integration](https://martinfowler.com/articles/continuousIntegration.html)
overview from 2006, evolving from Site Reliability Engineering (SRE),
DevOps culture, and Infrastructure as Code (IaC) principles.
Essentially, it embodies the concept of "all operations are in git,"
meaning all operations are codified and stored in version control
systems like Gitlab or Github. Once codified, any alterations to the
code propagate to the end systems or applications through predefined
pipelines as per requirements.

GitOps emerged as a cloud-native initiative aimed at applying lessons
learned from Infrastructure as Code (IaC) environments to the management
of Kubernetes clusters and multi-cluster setups. The integration of
GitOps with IaC streamlines environment setup through automation,
facilitating quicker deployments and releases such as canary
deployments. This approach also grants greater flexibility for all
stakeholders in managing environments and applications.

Employing the Red Hat Ansible Automation Platform to enact GitOps
pipelines offers distinct advantages. Leveraging the Automation Webhook
capabilities within Ansible Platform Controller enables the
implementation of agentless GitOps workflows that extend beyond
cloud-native systems to encompass existing IT infrastructure like cloud
services and networking equipment. Utilizing Ansible provides access to
its extensive ecosystem and affords the flexibility to select the most
suitable tools for individual workflows.

## What is a GitOps workflow?

GitOps represents an evolution in Infrastructure as Code (IaC),
utilizing Git as the version control system for infrastructure
configurations. Similar to IaC, GitOps adopts a declarative approach to
infrastructure management, defining the desired system state and
tracking its actual state.

In a GitOps workflow, changes are made through pull requests, altering
the state in the Git repository. Upon initiating a new release via a
pull request, the GitOps operator, situated between the GitOps pipeline
and the orchestration system, retrieves the new state declaration from
Git. Once changes are approved and merged, they are automatically
applied to the live infrastructure, allowing developers to continue
using their standard CI/CD practices.

## Ansible GitOps Framework

### Declarative

While Ansible isn’t inherently declarative, it’s both feasible and
advisable to script Ansible in a declarative manner. In an Ansible
GitOps approach, the emphasis is on crafting code that articulates the
desired state over procedural methods to achieve it. Although procedural
code may sometimes be necessary, prioritizing declarative code yields
superior GitOps outcomes.

### Versioned and Immutable

For code to be versioned and immutable, it must be stored in a version
control repository, typically Git, without specifying a particular Git
service. Immutability entails deploying the same version consistently,
regardless of how many times it’s deployed—a concept distinct from
idempotence. In the context of GitOps, immutability means deploying any
specific revision and obtaining identical results each time.

### Automatic Pull

In an Ansible GitOps setup, the Ansible codebase should be configured to
autonomously update the project repository, where the configuration code
resides. At minimum, the project should refresh periodically, ensuring
that new commits become accessible on the Ansible Automation Platform
(AAP) server. An alternative approach involves integrating an
appropriate webhook into the repository, triggering repository project
updates in AAP whenever the repository refreshes.

### Continuously Reconciled

This criterion necessitates periodically applying the versioned
configuration to the managed environment. Typically, this involves
"software agents" like ArgoCD for OpenShift patterns or AAP for Ansible
Patterns, recognizing new commits and subsequently applying the
configuration. In the case of Ansible, it entails executing units of
work such as playbooks and roles whenever the authoritative Git
repository undergoes changes.

Please refer to [Ansible GitOps Pattern
Theory](https://github.com/mhjacks/ansible-pattern-theory).
