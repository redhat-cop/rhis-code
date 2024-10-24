# where to start?
`playbooks/landscape_site.yml` is the main Ansible playbook to trigger everything from scratch for a Big Bang. Current `rhis-code` consumes `rhis-inventory` repository for the credentials and configurable variables. Duplicate `rhis-inventory` repository as your own inventory to use if you plan to deploy environment on your own and update definitions based on your own.

1. Please read and understand the [High Level Architecture](https://redhat-cop.github.io/rhis-code/network_design/) for the project.

2. Register a new domain or use your existing domain, define it in the https://github.com/redhat-cop/rhis-inventory/blob/devel/group_vars/all/azure_infra.yml file. Setup Azure Nameservers for your public DNS records if you are not using Azure to host your public domain name.

3. Change the subnet definitions in https://github.com/redhat-cop/rhis-inventory/blob/devel/group_vars/all/azure_network.yml if you consider to use a different subnets.

4. Define git username, and email address in [GitHub User](https://github.com/redhat-cop/rhis-inventory/blob/devel/group_vars/all/git_repo_commit.yml). Read [documentation](https://redhat-cop.github.io/rhis-code/github_user/) for more details. This user needs to have `commit`to the relevant branch.

5. Define IdM LDAP bind name in the file https://github.com/redhat-cop/rhis-inventory/blob/devel/group_vars/all/idm_config.yml based your preferred domain name.

6. Create Red Hat activation key manually on RH Cloud Console and define this activation key in https://github.com/redhat-cop/rhis-inventory/blob/devel/group_vars/all/imagebuilder.yml to enable image based VMs to be able to register to the RH Console.

7. Define certificate configuration in https://github.com/redhat-cop/rhis-inventory/blob/devel/group_vars/all/pki_idm_generate_certs.yml

8. Ensure that you have all Red Hat subscriptions in place to use. These are mainly `Red Hat Satellite Infrastructure Subscription`, `Red Hat Ansible Automation Platform`, and any subscription that covers access to `Red Hat Enterprise Linux Server` repositories.

9. Create a Satellite manifest to add subscriptions to be used by Satellite. Simple Content Access(SCA) has to be enabled.

10. Ensure that Ansible Automation Platform(AAP) subscription added to the Satellite manifest. There is a name limitation during AAP subscription process, for this reason a subscription has to be visible as `Red Hat Ansible Automation Platform`.

11. Create a custom application on Azure and grant it on a Subscription Level with a `owner` role.

12. Create a user on Red Hat RHSM portal and use this credentials in https://github.com/redhat-cop/rhis-inventory/blob/devel/group_vars/all/vault_rh.yml

13. Create two subscriptions on Azure to differentiate Management and business workloads. Add subscription information to the https://github.com/redhat-cop/rhis-inventory/blob/devel/group_vars/all/vault_azure.yml

14. Update AAP project definitions based on your own inventory repository in https://github.com/redhat-cop/rhis-inventory/blob/devel/group_vars/aap/aap_config_controller_project.yml

15. Define IdM configuration, users, etc in RHIdM config files https://github.com/redhat-cop/rhis-inventory/tree/devel/group_vars/ipahidden/

16. Define RootCA passphrase in https://github.com/redhat-cop/rhis-inventory/blob/devel/group_vars/rootca/vault_rootca_key_passphrase.yml

17. Create Azure RH Image Integration based on the [Azure RH Image Integration](https://redhat-cop.github.io/rhis-code/azure_rhib_integration/) document.

18. Create private and public SSH key pair(Azure compatible) for local user to be able deploy the environment from scratch. This information should be encrypted and stored as `vm_user`, `vm_user_public_key` and `vm_user_private_key` This can be configure automatically after you define `vm_user` in the inventory and running link:playbooks/landscape_init.yml[`landscape_init.yml`] playbook to initialize your local environment in the beginning.

19. All credentials are stored within encrypted string format, so you need to encrypt your own credentials in the inventory repository.

* Default ansible encryption password
* Red Hat IdM credentials like Directory Manager password, administrative user password
* Red Hat Satellite username and password for administrative access
* Ansible Automation Platform credentials like Controller admin username, Controller admin password, Private Automation Hub admin username, Private Automation Hub admin password, AAP Database password, username and password for registry.redhat.io
* Azure custom application credentials that allows ansible to access. Azure Client ID, Secret ID and value of the custom application.
* Azure subscription credentials such as Tenant ID and Subscription ID.
* GitHub user personal access token, gpg secret and public key
* Common passphrase for each host's SSL private key
* Red Hat RHSM username, password and offline token with organization number
* Proxy username and password that will be used on a Jumphost(Bastion) which will help you access to the internal resources by webUI.
* Default ansible username and password on RHIdM which will be used to access to the VMs with SSH.
* Azure Workload subscription ID when used in https://github.com/redhat-cop/rhis-inventory/blob/devel/group_vars/work/vault_azure.yml
